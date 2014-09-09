# Introduction
Nobody is perfect. (In case you are ignore the following paper and get back to work!)
Testing and debugging your code is the foundation of innovative and awesome features. Unfortunately, this is not always an easy task. Sauerbraten itself does not provide any built-in debugging or benchmarking tools.
This will change now. Some ingame debugging tools are neccesary in order to control and measure your code's performance!

# Before we begin
## Guideline for good Code
Please keep in mind that good code
* has suitable comments for important code passages
* does NOT depend on OS-specific libraries
* is extendable and dynamic
* should be object-orientated
* should respect types (C/C++ has strong types!)
* should think twice about user input or function parameters
* keeps sub-modules in separated header files
* is clean and does not contain passages which aren't used or commented out (final code...)

## External debuggers
If not anything works, try to use external debugging tools.
Thanks to [VALVe's Vogl](https://github.com/ValveSoftware/vogl) there is finally a good OpenGL graphic debugger out there. 
Other software such as [PIX](http://en.wikipedia.org/wiki/PIX_%28Microsoft%29) or [Crytek RenderDoc](http://cryengine.com/renderdoc) are only for Microsoft DirectX.

# Debugging so far
## Basic screen printing
You can use conoutf(..); (dont forget to include "engine.h") in your code. The modifiers are the same as
[printf](http://www.cplusplus.com/reference/cstdio/printf/)
Examples:
`
conoutf(CON_DEBUG, "Hello World");
conoutf(CON_DEBUG, "%f %d %s %llu", floatvar, intvar, "stringvar", int64var);
`
Those outputs will be printed to the log file as well.
## Sauerbraten debug leftovers
Its very interesting that nobody knows the old debugging commands which still remain in the code. They are not useful anyway.
* /aidebug [0-6] Shows waypoints and starts AI debugger
* /debugsm [0|1] Shadow map debugger
* /debugglare [0|1] Glare debugger
* /debugdepthfx [0|1] Depth function debugger
* /debugparticles [0|1] Particle debugger (not for Hanacks new Particle system)

## Miliseconds and SDL_GetTicks()
So far you can use [SDL_GetTicks()](https://wiki.libsdl.org/SDL_GetTicks) to get the number of miliseconds since the SDL initialisation (program start.)

`
unsigned long ulStartTime = SDL_GetTicks(); // Store current time
SDL_Delay(100); // Wait 100 miliseconds
unsigned long ulEndTime = SDL_GetTicks(); // Store end time

conoutf(CON_DEBUG, "Well that took around %llu miliseconds..", ulEndTime - ulStartTime);
`