+++
title = "Tagging Music as Explicit in iTunes"
date = "2022-08-14T18:38:09-04:00"
tags = ["itunes", "music.app"]
audio = []
images = []
videos = []
summary = "AtomicParsley's `--advisory` flag does the trick, as long as you also remove and re-add the track."
+++

I buy music from 7digital sometimes, and their method of marking tracks as explicit is to append “ Explicit” to the title of the track.  Because I'm a persnickety nerd about my music collection, I find this annoying.  If you are like me and also find it annoying, here's how to fix it.

Assumptions (if these do not apply, this information won't help you):
1. The files you want to fix are in m4a containers (`song.m4a`).  (The codec doesn't matter, this method works regardless of whether you use AAC or ALAC.)
2. You use iTunes (Windows) or Music.app (macOS).

Directions:
1. Download [AtomicParsley](http://atomicparsley.sourceforge.net) ([SourceForge download link](https://sourceforge.net/projects/atomicparsley/files/atomicparsley/)) for your platform of choice. In my case, I installed it on macOS with `brew install atomicparsley`.
2. Run `atomicparsley path/to/file.m4a --advisory=explicit --overWrite`.  This marks the track as explicit, and instructs AtomicParsley to overwrite the original file, rather than making a new temporary file.
3. Remove the track from iTunes/Music.app.  Make sure to choose to keep the files on disk.
4. Re-add the file to iTunes/Music.app.  This is necessary because it only reads an explicit tag when the track is added to your library.

As an aside, you might notice that `--advisory=clean` is also available.  This does not remove the ‘🄴’ badge from the track in iTunes/Music.app, it adds a ‘🄲’ badge.  The clean badge is typically used to indicate that this copy of the track has been edited or re-recorded to remove the explicit language (e.g. a radio edit).  If you want to remove the explicit mark (or the clean mark), use `--advisory=""`.
