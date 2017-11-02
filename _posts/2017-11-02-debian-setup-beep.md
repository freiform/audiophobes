---

layout : post
title : Setting up Debian - Hardware Beep
date: 2017-11-02 14:47

---

To disable the annoying hardware beeb, the module `pcspkr` has to be unloaded:

    modprobe -r pcspkr

Blacklist to prevent it being loaded on the next reboot:

    echo "blacklist pcspkr" >> /etc/modprobe.d/pcspkr-blacklist.conf
