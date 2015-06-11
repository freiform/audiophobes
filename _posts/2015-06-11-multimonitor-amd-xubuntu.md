---

layout : post
title : Saving a Multi-Monitor Setup for AMD GPUs in Xubuntu
date: 2015-06-11T09:22+01:00

---

I am running Xubuntu with an AMD GPU and two monitors. There are three drivers available for this setup: `xserver-xorg-video-ati`, `fglrx`, and `fglrx-updates`. The first one does not allow multi-monitor setups at all on my machine. The two `fglrx*` drivers can configure this in the *Catalyst Control Center*, but won't save it between reboots. This is a known bug that has not been adressed [since 2010](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/551475).

Luckily, there is a workaround:

- use the `fglrx` driver and configure your multi-monitor settings in the Catalyst Control Center. These can be applied, but will reset on the next reboot. Don't reboot yet.
- open the *Display* settings in the regular Xubuntu *Settings* program, and hit *Apply* there. This will actually save the configuration. (You can't use the `fglrx-updates` driver, since that driver does not work with the *Display* settings)

Your monitor setup should now work, and persist across reboots.
