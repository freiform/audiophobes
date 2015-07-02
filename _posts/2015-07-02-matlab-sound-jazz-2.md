---

layout: post
title: Sound of Silence, Epilogue
date: 2015-07-02 13:07

---

[A month ago](http://audiophobes.net/2015/06/08/MATLAB-Sound-Jazz/), we found that MATLAB faces problems in playing sounds under a Linux system of Ubuntu flavour. Again, thanks for the [(wireless) internet](https://www.youtube.com/watch?v=iDbyYGrswtg), we found a solution!

As it turns out, [this is most likely your fix!](http://www.mathworks.com/matlabcentral/answers/225677-alsa-lib-pcm-error#answer_184598) Problems seem to arise if the desired delay of 25ms (default) cannot be provided. Setting the value to around 100ms fixes this issue for now. **Hooray!!**
