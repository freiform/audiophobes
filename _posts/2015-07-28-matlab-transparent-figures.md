---

layout: post
title: Transparent background for Matlab figures
date: 2015-07-28 10:36

---

Are you designing a poster or something else more colorful than your run-of-the-mill paper? You want to display a matlab figure? You are annoyed by the figure's white background on your colorful document? Fear not!

Get Yair Altman's excellent [export_fig](https://github.com/altmany/export_fig) and read the documentation. Hint:

    set(gca, 'color', 'none');
    export_fig your-fancy-see-through.pdf -transparent
