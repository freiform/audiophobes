---

layout : post
title : Setting up Debian - Install and run MATLAB
date: 2017-11-02 16:00

---

Installing `matlab-support` will take care of moving MATLAB's own `libstdc` out of the way which will help with things. It also creates shortucuts. 

To use your GPU properly, you have to tell MATLAB to run in hardware rendering mode. This, of course (?!) cannot be done from inside matlab using its `opengl` command. Instead you have to pass `-nosoftwareopengl`. Obviously. At least it works:   

    >> opengl info
                              Version: '3.0 Mesa 13.0.6'
                               Vendor: 'X.Org'
                             Renderer: 'Gallium 0.4 on AMD POLARIS11 (DRM 3.8.0 / 4.9.0-4-amd64, LLVM 3.9.1)'
                       MaxTextureSize: 16384
                               Visual: 'Visual 0x307, (RGBA 32 bits (8 8 8 8), Z depth 16 bits, Hardware acceleration, Double buffer, Antialias 8 samples)'
                             Software: 'false'
                 HardwareSupportLevel: 'full'
            SupportsGraphicsSmoothing: 1
        SupportsDepthPeelTransparency: 1
           SupportsAlignVertexCenters: 1
                           Extensions: {242×1 cell}
                   MaxFrameBufferSize: 16384

Hints on how to get this working on e.g. Debian testing (as of now..) are welcome.  
