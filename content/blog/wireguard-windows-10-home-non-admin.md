+++
title = "WireGuard on Windows 10 Home for Non-Admin Users"
date = "2021-11-29T14:14:11-05:00"
tags = ["sysadmin", "windows"]
audio = []
images = []
videos = []
+++

Here's the extra stuff you need to know to get WireGuard working on Windows 10 Home without having any other Windows administration experience.

<!--more-->

This information is based on [a mailing list message by Jason Donenfeld][email], the author of WireGuard, and [a StackOverflow answer by tromlet](https://superuser.com/a/1657595).  It only works for WireGuard versions 0.3.1 and newer.  By the time of writing this, 0.3.1 is several minor versions out of date, so basically any WireGuard installation should be fine.  Should :P

1. Download PsExec from Microsoft's sysinternals page: https://docs.microsoft.com/en-us/sysinternals/downloads/psexec
2. Download the registry file attachment from [Jason's email on the Linux Kernel Mailing List][email][^lkml].
3. Open PowerShell *as an administrator*, navigate to the folder where you downloaded and extracted PsExec, and run `.\psexec -i -s regedit`.  This is a simple way to run the Windows Registry Editor as the SYSTEM user (`-s`, Windows' version of Unix's root) on the current user's desktop (`-i`).
4. Choose File → Import and import the registry file from the email that you downloaded in step 2.  This registry file adds the "Network Configuration Operators" group to Windows 10 Home, where it does not normally exist.
5. Go to `HKEY_LOCAL_MACHINE\SOFTWARE` and create a new registry key called `WireGuard` by right-clicking "SOFTWARE" in the sidebar and choosing New&nbsp;→&nbsp;Key.
6. Inside `HKEY_LOCAL_MACHINE\SOFTWARE\WireGuard`, create a new DWORD called `LimitedOperatorUI` by right-clicking the empty space in the main pane and choosing New → DWORD (32-bit) Value.
7. Double-click the new `LimitedOperatorUI` value and set it to `1`.  This indicates to WireGuard that it should allow users who are in the Network Configuration Operators group to run WireGuard in an interface mode where no new tunnels can be added or removed, but existing tunnels can be connected to and disconnected from.
8. Exit Registry Editor, freeing up the administrator command prompt.
9. Run `Add-LocalGroupMember
-Group "Network Configuration Operators" -Member $USERNAME` to add the non-admin user to the Network Configuration Operators group.
10. If the user was logged in when their group membership changed, have them log out and log back in again.  Just like on \*nix, group membership changes don't take effect until after logging out and back in again (plus or minus some tricks).

After following these steps, you can test the changes by first making a WireGuard tunnel as an administrator (even one that doesn't connect anywhere is fine), then logging into the non-admin user's account and running WireGuard.  If it did not work, you will get a slightly misleading error dialog stating that the WireGuard UI can only be run by users who are a member of the Administrators group.  If it did, the WireGuard UI will appear, and you will be able to click Activate on the test tunnel created moments earlier.

[email]: https://lore.kernel.org/wireguard/CAHmME9oMFQtePYt37+4eyOn23mwHwP2UGxQi=SaJk9J3p1zCpw@mail.gmail.com/
[^lkml]: Kinda funny that we're getting Windows configuration advice from the LKML!
