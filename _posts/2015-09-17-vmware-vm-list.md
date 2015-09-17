---

layout: post
title: Making VMWare remember VMs
date: 2015-09-17 09:45

---

On Linux, VMWare Player and Workstation does not remember the location of its virtual machines across reboots. VMWare saves that list in `~/.recently-used.xbel`, and as of a few versions back, this file was moved to `~/local/share/recently-used.xbel`. So far, this should not be a problem, but for reasons that are entirely beyond me, they also [*wipe* `~/.recently-used.xbel`](https://bugs.launchpad.net/ubuntu/+source/gtk+3.0/+bug/1007336) on every log-off, which explains why VMWare does not remember it's VMs.

[Solutions](http://askubuntu.com/questions/75328/how-to-save-vmware-player-library) for this are plentiful and diverse, ranging from copying the file to its old location on log-*on*, to starting VMWare as superuser (which shouldn't make a difference, right?), to reinstalling VMWare repeatedly.

Personally, I found that `ln -s /home/user/.local/share/recently-used.xbel /home/user/.recently-used.xbel` seems to fix the issue and should be mostly benign. On the other hand, it is not clear why this persists over reboots, but it does. Oh well, the joys of Linuxing.
