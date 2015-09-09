---

layout: post
title: Media Keys in KDE
date: 2015-09-09 17:08

---

Regrettably, KDE does not have a built-in way to assign media functions to arbitrary keyboard shortcuts (or at least, I couldn't find it).

So, here are a bunch of scripts for Play/Pause, Next, Previous, and Stop: https://github.com/bastibe/KDE-Media-Keys

Associate these scripts with a keyboard binding in System Settings -> Shortcuts -> Custom Shortcuts -> Edit -> New -> Global Shortcut -> Command/URL, then set the trigger to the action to the script and use your preferred key as a trigger. Note that you have to save/apply every step of the way, or parts of it won't get saved. Also note that both the action *and* the group have to be enabled for the shortcut to fire.

Taken from a [fine man on the internet](https://www.kubuntuforums.net/showthread.php?58197-How-To-Get-Global-Media-Shortcuts-in-KDE)
