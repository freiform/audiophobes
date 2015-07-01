---
layout: post
title: "Meta post: Jekyll, sorting, YAML and colons"
date: 2015-07-01 10:10
---

If you plan to use a colon followed by a space in the title tag of a YAML front matter block, put said title in quotes.

If you fail to do so, the parser will not work on following tags. If you happen to specify a date after the title, it will be omitted and taken from the file name of the post instead. The posts for one day will then be sorted alphabetically  which might mess up your post order.
