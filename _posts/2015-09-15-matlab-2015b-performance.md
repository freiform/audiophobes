---

layout: post
title: Matlab 2015b Performance
date: 2015-09-15 14:45

---

A new version of Matlab was released [a few days ago](http://mathworks.com/products/new_products/latest_features.html). Among the new features are a [New Execution Engine](http://mathworks.com/products/matlab/matlab-execution-engine/) that is supposed to make everything so much faster. According to Mathworks, of 76 user applications, 49 were significantly faster!

Let's put this to a test! The last big change in stuff was the transition from 2014a to 2014b, with the introduction of the new plotting framework. So here's a bunch of benchmarks:

The first six items are the output of Matlab 2014a's own `bench` utility (they conveniently changed `bench` in 2014b, presumably to hide the stark contrast between 2014a and 2014b). The last two items are applications we use for our jobs here.

<img src="assets/2015-09-15-matlab-benchmark.png" width="100%" alt="Matlab Benchmark" />

As you can see, application performance got significantly worse in 2014b, rebounded in 2015a, but in general declined slightly over time. If there is a big boost in performance in 2015b, it is not showing in these benchmarks.

But there's more to this than meets the eye. A nice person named Andrew Janke wrote a beautiful [microbenchmark for Matlab](https://github.com/apjanke/matlab-bench) that evaluates the performance of things like function calls and class creation:

<img src="assets/2015-09-15-matlab-microbenchmark.png" width="100%" alt="Matlab Microbenchmark" />

And this is actually rather interesting! As you can see, most things actually got faster. Function calls got a speed boost of about 4x. And most importantly, anything class related now operates at a speed similar to plain functions! Only the dynamic stuff got a bit slower, such as `feval`, Java interop, and anonymous functions. This is likely outweighed by the speedups in other areas, though.

More on Matlab and OOP performance in Matlab [here](http://stackoverflow.com/questions/1693429/is-matlab-oop-slow-or-am-i-doing-something-wrong/1745686#1745686) and more on the rationale behind Matlab's object system [here](http://de.mathworks.com/company/newsletters/articles/inside-matlab-objects-in-r2008a.html) and more on how Matlab deals with variables and allocations in [this](http://stackoverflow.com/questions/1446281/matlabs-garbage-collector) goldmine of links.
