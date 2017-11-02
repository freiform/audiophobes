---

layout : post
title : Setting up Debian - Mixed locales
date: 2017-11-02 18:00

---

When the preferred system language is english but paper, time, numbers, etc are of a different variety, mixed locales come in handy.

    dpkg-reconfigure locales
    
to create the desired locales and then setting them in `/etc/default/locale`, i.e. 

    LANG=en_US.UTF-8
    LC_MEASUREMENT=de_DE.UTF-8
    LC_MONETARY=de_DE.UTF-8
    LC_NUMERIC=de_DE.UTF-8
    LC_PAPER=de_DE.UTF-8
    LC_TIME=de_DE.UTF-8
    
Interestingly GNOME Terminal will refuse to start if there are problems with the locales and/or they are not set. The same applies if `C.UTF-8` is set.
