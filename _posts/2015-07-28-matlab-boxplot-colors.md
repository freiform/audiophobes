---

layout: post
title: "Recolor Matlab's boxplots"
date: 2015-07-28 11:00

---

There is no boxplot in Matlab but a bunch of assorted lines and symbols. And you have to find them yourself! Hah! For median, box (25th and 75th percentiles) and outliers, proceed as follows:

    red  = [198 0 0]./255;
    blue = [0 123 198]./255;

    set(findobj(gcf,'tag','Median'), 'Color', blue);
    set(findobj(gcf,'tag','Box'), 'Color', red);

    h = findobj(gcf,'tag','Outliers');
    for iH = 1:length(h)
        h(iH).MarkerEdgeColor = red;
    end

And then there's a few other ones, depending on plotstyle and marker:

    'Upper Whisker'
    'Lower Whisker'
    'Upper Adjacent Value'
    'Lower Adjacent Value'
    'Whisker'
    'MedianOuter'
    'MedianInner'
    'NotchLo'
    'NotchHi'
