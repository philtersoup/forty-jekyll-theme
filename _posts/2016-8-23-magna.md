---
layout: post
title: Firmware Development for Oogenesis
description: Classic 2 channel British equaliser with VCA outputs - Really Nice Audio, UK
image: assets/images/rna/oogenesis/outdoor.jpg
---

In the summer of 2017 I was approached to do something that sounded _fairly trivial_, writing a bit of code to do basic user interaction:
* Reading a matrix of buttons.
* Driving a number of LED's and Relays

This was a part of a larger, ambitious project, being developed at Really Nice Audio. A modern take on a classic British equaliser circuit with an aim towards lowering the cost of production without compromising the signal path and retaining the characteristic audio quality.

Writing embedded software in C++ was a very challenging yet gratifying experience. Having a background in JavaScript, openGL and visual programming environment Max MSP, this was as low-level programming as I have ever done. Having to worry about memory restraints, real-time responsiveness and the perils of having the electronics dictate the program architecture was definitely a mindset that needed getting used to!

I chose to do this project in C++ and not in C because I love objects, and object oriented programming. There is something almost poetic about writing good object oriented code. But again, for a JavaScript dev approaching embedded C++, there were lots of caveats that had to be addressed.

I wrote the initial code as a big old monolith. 1000+ lines, in 1 file. **OHH THE HORROR!**

![]({{ "/" | relative_url }}/assets/images/rna/oogenesis/theHorror.png)

With the help of my house-mate / friend and professional software developer <a href="https://www.jackdanielharding.com/"> Jack </a>, we were able to move everything across to their own classes, have a directory structure that was maintainable, and even make our codebase re-usable to the point that when I was  prototyping firmware for a new module few days back, it took me 15 minutes to get the basic functionalities up and going!

![]({{ "/" | relative_url }}/assets/images/rna/oogenesis/noooice.png)

So the feature list got extended by a lot and we obviously made the most of having digital control over a very high quality analog circuit. This meant:
* Being able to link 2-channels for use in Stereo Mode
* Copying the states of one channel to the other
* Using the LED-Buttons as level indicators
* Auto-magically saving system state to non-volatile memory, so you power back on to how you'd set it!
{:refdef: style="text-align: center;"}
![]({{ "/" | relative_url }}/assets/images/rna/oogenesis/meters.gif)
{: refdef}
