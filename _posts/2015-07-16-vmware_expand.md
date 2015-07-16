---

layout: post
title: "VMWare: Expand Disk needs space"
date: 2015-07-03 10:12

---

Trying to expand a VMWare disk in close quarters might not work. For not very obvious reasons. In fact, the current disk is not expanded or resized but a new disk is created and the contents of the original disk are copied over. In short:

    space_required = old_space + new_space
