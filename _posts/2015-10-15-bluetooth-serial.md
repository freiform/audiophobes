---

layout : post
title : Serial Bluetooth Woes
date: 2015-10-15 13:45

---

I've been trying for quite some time to access a Bluetooth device using a virtual serial port. While blueman (Xubuntu 15.04)
worked out of the box, bluedevil (Kubuntu 15.04) never managed to establish a connection. After some fiddling around with bluez, I had access to the device in question via `/dev/rfcomm0`, but unfortunately only as superuser. All attempts to access the device as user were met with messaged about busy devices or permission issues. Looking at the permissions in question, everything seemed fine, including my user's intimate affiliation with the `dialup`-group . After some searching and fiddling, one of the following steps (or any combination including #3) apparently did the trick:

1. edit `/etc/bluetooth/rfcomm.conf` to look something like this:


    rfcomm0 {
        # Automatically bind the device at startup
        bind yes;
        # Bluetooth address of the device
        device AB:CD:EF:01:23:45;
        # RFCOMM channel for the connection
        channel 1;
        # Description of the connection
        comment "my wicked bt-device";
    }

2. create a file named `pincodes` in `/var/lib/bluetooth/<your_hopefully_less_wicked_bt-adapter's-address>/`, containing your wicked bt-device's address and PIN:


    AB:CD:EF:01:23:45 1234

3. create a new udev-rule, e.g. in `/etc/udev/rules.d/40-rfcomm.rules`:


    KERNEL=="rfcomm*", GROUP="dialout", MODE="0666"

All other things being equal, calling


    rfcomm bind 1

and then accessing `/dev/rfcomm0` with a terminal of your choice, should do the trick.

On a related note, you might want to allow the user(s) in question to run rfcomm, e.g. by typing something in the lines of


    sudo chmod u+s /usr/bin/rfcomm

Thanks to all the unsung heroes and the information buried in the bowels of their respective forums, repos and weblogs:


[1] http://pi19404.github.io/pyVision/2015/04/03/22/

[2] https://forums.gentoo.org/viewtopic-t-797762-start-0.html

[3] http://myro-users.2293151.n4.nabble.com/Resolving-Bluetooth-permission-issues-on-Linux-td3597293.html
