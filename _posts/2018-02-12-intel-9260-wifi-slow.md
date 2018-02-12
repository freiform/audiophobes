---

layout : post
title : Intel 9260 M.2 WiFi (8086:2526) slow with Linux
date: 2018-02-12 18:30  

---

I replaced the WiFi-card of my laptop with an [Intel 9260](https://www.intel.com/content/www/us/en/products/wireless/wireless-products/dual-band-wireless-ac-9260.html). Unfortunately, the card was very, very slow on my home network (~2.5 mbit down speed). Fortunately, [there is a fix for that](https://bugzilla.kernel.org/show_bug.cgi?id=198351). The patch works fine with 4.14.16, (Fedora 27). 
