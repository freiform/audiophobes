---

layout : post
title : Dodge MATLAB's Sound Issues on Unix Systems
date: 2015-11-03 17:01

---

Again, I stumbled on MATLAB's nasty sound(sc) issues on my Xubuntu machine which cause random sound dropouts/stuttering and are somehow related to the latency defined by MATLAB's `audioplayer` class.

 This time, after a more thorough search, I found the idea for a [wrapping function by Joachim Thiemann](http://signalsprocessed.blogspot.de/2011/02/playing-sounds-from-matlab-on-unix.html).
With little tweaks I ended up with these three lines of code which solve issues for me (for now) by using ALSA's `aplay`.  
And yes, these issues are ANNOYING!!

    function [] = usound( vSignal, fs)
    %USOUND Replacement for sound() or soundsc() on Unix machines
    % -------------------------------------------------------------------------
    % Adapted from J. Thiemann's code on his blog
    % http://signalsprocessed.blogspot.de/2011/02/playing-sounds-from-matlab-on-unix.html
    %
    % Usage: [] = usound( vSignal, fs)
    %
    %   Input:   ---------
    %         vSignal: signal vector (Nx1 or Nx2) to be played
    %              fs: sampling frequency
    %
    %
    % Author :  J.-A. Adrian (JA) <jens-alrik.adrian AT jade-hs.de>
    % Date   :  03-Nov-2015 16:04:39
    %

    filename = [tempname '.wav'];
    audiowrite(filename, vSignal, fs);

    dummy = system(sprintf('aplay %s &', filename));

    % Copyright (c) 2015, J.-A. Adrian
    % All rights reserved.
    % Licensed under BSD 3-Clause license
