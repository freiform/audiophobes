---

layout : post
title : Serial Bluetooth. Again.
date: 2017-11-15 10:30

---

Everytime I touch anything Bluetooth-related on any Linux distribution [it just won't work](http://audiophobes.net/2015/10/15/bluetooth-serial/). 

I am currently running Debian Stretch, Cinnamon comes with blueman to handle your bluetooth needs, at least unless you actually want to use it. I want to talk to a HC-05 module, but when pairing and connecting it using the blueman applet, my user cannot access `/dev/rfcomm0`. Using `lsof` reveals that a python process named `blueman-rfcomm-watcher` and running with root permissions has a finger on the device, effectively blocking it for any user. To fix that and actually talk to tehe HC-05 as a common user, I had to remove blueman and pair the device using `bluetoothctl`. Check if there is an agent running (`default-agent`) and start one if not (`agent on`). Otherwise, you will not be able to enter your pin.

Finally setup rfcomm:

    sudo rfcomm bind <dev> <bdaddr> [channel]	
    
The data I am receiving is not plausible, but that is another battle. 

The adventure continues.  
