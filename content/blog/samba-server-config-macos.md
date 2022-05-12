+++
title = "Samba Server Config for macOS & iOS"
date = "2021-11-14T17:50:24-05:00"
lastmod = "2021-11-51T11:51:00-04:00"
tags = ["sysadmin", "linux"]
audio = []
images = []
videos = []
+++

I needed to figure out how to configure Samba to serve files to macOS clients, and to accept Time Machine backups.

<!--more-->

Information in this post is based on NixOS 21.05, Samba 4.14.4, Avahi 0.8, iOS 15.1, and macOS 11.6 (Big Sur).

# ZFS

The storage underlying my Samba shares is a ZFS pool.  *At pool creation time,* you should set the pool option `normalization` to `formD`.  This changes the Unicode normalization algorithm that ZFS uses to format bytes on disk (e.g. in file names) to form D, which is the same algorithm that macOS uses.  You will experience problems with missing files if your pool is set to form C (or CK), because ZFS and macOS will disagree on which normalization form to use.  I did not know about this when I created my pool, and mine is set to `none`, which has at least not yet caused problems.

# Samba

The Samba file server requires rather a lot of additional configuration in order to support macOS/iOS clients.  Beyond the basic directives that are required for every Samba server, this is what I found was necessary to fully support Apple's platforms.

Globally:

* `min protocol = SMB2` — Setting this to `SMB3` breaks compatibility with the Files app on iOS.  If you try, you'll get a UIAlert that says "Operation not supported." when you connect.
* `use sendfile = yes` — Uses the `sendfile` syscall to speed up data transfers.
* `vfs objects = acl_xattr catia fruit streams_xattr` — Enables four plugins on every share.  If having all of these on every share is not what you want, you can specify the `vfs objects` key per-share.  `acl_xattr` and `streams_xattr` improve support for macOS's extended attributes. `catia` is nominally for a specific 3D design software, but it seems to be beneficial. `fruit` is for all of the Apple-specific optimizations and features.
* `fruit:advertise_fullsync = true` — Turns on advertisements for a feature that improves the performance of Time Machine backups.
* `fruit:metadata = stream` — I'm not sure what this does.
* `fruit:aapl = yes` — I'm not sure what this does either.
* `fruit:model = MacPro7,1` — Changes the icon displayed in Finder for this server, when connecting by IP/hostname.

Per Share:

* `spotlight = yes` — Allow spotlight indexes of this share.
* `aio read size = 1` — Force all read I/O operations to be async.  The concerns about data loss listed in the Samba documentation near this option are no longer relevant.
* `aio write size = 1` — Force all write I/O operations to be async too.
* `fruit:time machine = yes` — Label this share as a valid Time Machine backup target.  Don't put this on shares that should not receive Time Machine backups.  (It is still possible to configure Time Machine to back up to shares that do not have this option set, but macOS will at least not suggest it.)

For more information, check [the documentation for `vfs_fruit`](https://www.samba.org/samba/docs/current/man-html/vfs_fruit.8.html).

# Avahi

macOS seems to be slowly moving away from listing metadata directly in the Samba configuration, and instead advertising it in mDNS.  So, if you want a specific share to show up in the Time Machine preference pane when configuring backups for the first time, or if you want your Samba server to have a nice icon in the Network pane in Finder (e.g. not a beige monitor displaying a Windows error), you have to install and enable Avahi.  macOS clients expect to see mDNS service advertisements for `_smb._tcp`, `_device-info._tcp`, and `_adisk._tcp`.  I provided these with a service definition in `/etc/avahi/services/smb.service` [(based on this post)](https://www.tumfatig.net/2017/let-mac-os-auto-discover-your-smb-shares/):

```xml
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
  <name>Your Display Name Here</name>
  <service>
	<type>_smb._tcp</type>
	<port>445</port>
  </service>
  <service>
	<type>_device-info._tcp</type>
	<port>0</port>
	<txt-record>model=MacPro7,1@ECOLOR=226,226,224</txt-record>
  </service>
  <service>
    <type>_adisk._tcp</type>
	<txt-record>sys=waMa=0,adVF=0x100</txt-record>
	<txt-record>dk0=adVN=TimeMachine,adVF=0x82</txt-record>
  </service>
</service-group>
```

If your Time Machine share is not called `TimeMachine`, you will need to replace the `adVN=TimeMachine` portion with `adVN=YourShareName`.  Presumably, the `VN` part is "Volume Name." `VF` appears to be "Volume Format," with bitflags documented [on the netatalk wiki](http://netatalk.sourceforge.net/wiki/index.php/Bonjour_record_adisk_adVF_values).

This configuration makes the share appear to come from the new rack-mounted Mac Pro (the `@ECOLOR` part selects the rack-mounted variant).  If you want to pretend the share is coming from another Apple device, you can try other Apple model identifiers (`PowerBook`, `Xserve`, `Macmini`, and so forth).  A full list of these is in `/System/Library/CoreServices/CoreTypes.bundle/Contents/Info.plist`, look for the many instances of `com.apple.device-model-code` [(source)](https://askubuntu.com/questions/1109810/ubuntu-18-10-samba-4-8-4-smb-conf-what-are-the-valid-values-for-fruitmodel#1144356).  Do note that not all models have a nice icon in the Finder sidebar; I picked the new cheese grater Mac Pro because it does.  Screenshots on the internet suggest that the `Xserve` model ID used to have a custom icon in the Finder sidebar, but it no longer does.

Originally, the above configuration had `<name replace-wildcards="yes">%h</name>`, but for some reason, that stopped working on my test Mac.  It would cause the Finder to say "connection failed" whenever you browsed to the host from the Network sidebar entry. Changing it to anything other than the machine's hostname made it work again.  I have no idea whether this is an actual problem, or just a weird caching issue.
