---

layout: post
title: Spotify on Ubuntu 15.04
date: 2015-07-03 10:12

---

One thing I sorely miss on Linux is Spotify. Turns out, there actually is a [Linux build of Spotify](https://www.spotify.com/download/linux/)!

But, this is *Linux*, so nothing works. More specifically, running `spotify` yields

     spotify: error while loading shared libraries: libgcrypt.so.11: cannot open shared object file: No such file or directory

But, this *is* Linux, and everything is [fixable](https://community.spotify.com/t5/Help-Desktop-Linux-Mac-Windows/Spotify-app-and-Ubuntu-15-04/m-p/1121949#M123803). In this case, Spotify is missing `libgcrypt11`, which is not available on 15.04.. It *was* available in utopic, though, so just add `deb http://security.ubuntu.com/ubuntu utopic-security main` to your software sources, `sudo apt-get update`, and `sudo apt-get install libgcrypt11`.

Stuff like this is normal on Linux. That's why people love it so much.

I am still undecided whether it is better to have stuff work some of the time, or if I prefer to be able to fix stuff some of the time. But who am I kidding, I'm writing this from Emacs on Linux; I obviously prefer repairability over it-just-works-except-when-it-doesn't.
