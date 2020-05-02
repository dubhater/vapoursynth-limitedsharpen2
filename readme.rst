Description
===========

LimitedSharpen2 is a multipurpose sharpening function for VapourSynth.

This is a port of the Avisynth function LimitedSharpen2, "by Didée, hacked by Akirasuto n' Soulhunter".


Usage
=====
::

    LimitedSharpen2(clp[, ss_x=1.0, ss_y=1.0, dest_x, dest_y, Smode=4, strength, radius=2, Lmode=1, wide=False, overshoot=1, soft=False, edgemode=0, special=False, aSharpS=0.5, aWThresh=0.75, exborder=0])


Parameters:
    *clp*
        A clip to process.
        
    *ss_x*, *ss_y*
        Supersampling ratio. Processing the clip at a higher resolution than the original reduces aliasing on edges.
        
        Default: 1.0, 1.0 (no supersampling).
        
    *dest_x*, *dest_y*
        Target resolution.
        
        Save a resize step when using supersampling.
        
        Default: same as the original resolution.
        
    *Smode*
        Sharpening mode.
        
        * 1: UnsharpMask
        * 2: Avisynth's Sharpen filter (a plain 3x3 convolution)
        * 3: Range sharpening
        * 4: ASharp + AWarpSharp2
        
        Default: 4.
        
    *strength*
        Sharpening strength.
        
        Default: 160 if *Smode* is 1, otherwise 100.
    
    *radius*
        Radius of UnsharpMask.
        
        Only used if *Smode* is 1.
        
        Default: 2.
        
    *Lmode*
        Limiting mode.
        
        Possible values: 1, any other number.
        
        Default: 1.
        
    *wide*
        If True, limit the sharpening to the minimum and maximum of the 5x5 local neighborhood. Otherwise use a 3x3 neighborhood.
        
        Default: False.
        
    *overshoot*
        Sharpening limit. Sharpened pixels may not exceed the minimum and maximum of the local neighborhood by more than *overshoot*.
        
        High values cause excessive haloing.
        
        This is a pixel difference, but in 8 bit pixels. The value gets scaled internally for higher bit depths.
        
        Default: 1.
        
    *soft*
        Softens the effect of sharpening.
        
        Default: False.
        
    *edgemode*
        Edge handling.
        
        * 0: No special handling. The entire image is sharpened.
        * 1: Sharpen only edges.
        * 2: Sharpen only not-edges.
        
        Default: 0.
        
    *special*
        Tries to raise detail contrast in dark areas.
        
        Default: False.
        
    *aSharpS*
        Sharpening strength for *Smode* 4. Passed to ASharp's *t* parameter.
        
        Default: 0.5.
        
    *aWThresh*
        Sharpening strength for *Smode* 4. Passed to AWarpSharp2's *thresh* parameter (multiplied by 256).
        
        Default: 0.75.
        
    *exborder*
        Exclude the borders of the image. Range: 0 to 16.
        
        Default: 0.


Requirements
============

   * `muvsfunc          <https://github.com/WolframRhodium/muvsfunc>`_
   * `ASharp            <https://github.com/dubhater/vapoursynth-asharp>`_
   * `AWarpSharp2       <https://github.com/dubhater/vapoursynth-awarpsharp2>`_


License
=======

???
