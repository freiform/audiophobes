---

layout : post
title : Zombie Functions in Matlab
date: 2015-11-04 09:17

---

For [one of my projects](https://github.com/bastibe/transplant) I needed a function that does not end. A proper infinite loop that will keep looping even in the event of error or measles. Because the problem is: `try`/`catch` will [not catch every error](http://www.wikihow.com/Be-A-Catcher-In-Baseball). It will not catch Ctrl-C or SIGINT. It will not catch `mex` errors. And it just generally is a [bad catcher](https://www.youtube.com/watch?v=1ppj9tCtngA).

So how do you keep such a function alive? Well, you can't. If SIGINT calls, it will die, [like we all do](http://i.imgur.com/6u3dd.png). But death is not the end, I say. Courtesy of [`onCleanup`](http://mathworks.com/help/matlab/ref/oncleanup.html), let's make a zombie function:

    function zombie(isUndead)
        if nargin == 0
            % normal startup
        elseif isUndead
            % we have been restarted!
        end

        lifeInsurance = onCleanup(@()zombie(true))
    end

The magic behind this is that `onCleanup` creates an object `lifeInsurance` with a special destructor that will call `onCleanup`'s argument when it is destroyed. Thus, when `zombie` ends, `lifeInsurance` goes out of scope and is destroyed--which restarts `zombie` (this time with `isUndead` set to `true`).

If you want to keep variables in your function alive as well, mark them as [`persistent`](http://mathworks.com/help/matlab/ref/persistent.html), so they stay with you into the afterlife.

