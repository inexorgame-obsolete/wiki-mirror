# Introduction
Nobody is perfect. (In case you are ignore the following paper and get back to work!)
Testing and debugging your code is the foundation of innovative and awesome features. Unfortunately, this is not always an easy task. Sauerbraten itself does not provide any built-in debugging or benchmarking tools.
This will change now. Some ingame debugging tools are neccesary in order to control and measure your code's performance!

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

# Debugging tricks so far
## Basic screen printing
You can use conoutf(..); (dont forget to include "engine.h") in your code. The modifiers are the same as
[printf](http://www.cplusplus.com/reference/cstdio/printf/)
Examples:
`
conoutf(CON_DEBUG, "Hello World");
conoutf(CON_DEBUG, "%f %d %s %llu", floatvar, intvar, "stringvar", int64var);
`
Those outputs will be printed to the log file as well.

## Placing conoutf to trace calls
Use conoutf to trace your calls! you can place them almost anywhere in the code.

## Sauerbraten debug leftovers
Its very interesting that nobody knows the old debugging commands which still remain in the code. They are not useful anyway.
* /aidebug [0-6] Shows waypoints and starts AI debugger
* /debugsm [0|1] Shadow map debugger
* /debugglare [0|1] Glare debugger
* /debugdepthfx [0|1] Depth function debugger
* /debugparticles [0|1] Particle debugger (not for Hanacks new Particle system)

## Miliseconds and SDL_GetTicks()
So far you can use [SDL_GetTicks()](https://wiki.libsdl.org/SDL_GetTicks) to get the number of miliseconds since the SDL initialisation (program start.)
`unsigned long ulStartTime = SDL_GetTicks(); // Store current time
SDL_Delay(100); // Wait 100 miliseconds
unsigned long ulEndTime = SDL_GetTicks(); // Store end time
conoutf(CON_DEBUG, "Well that took around %llu miliseconds..", ulEndTime - ulStartTime);`

## Do something every 5 seconds (dirty)
Some things are just way too heavy to print every sub-calculation to the screen. You should limit the output.
One method to do this is to calculate the modulo of SDL_GetTicks(). Its very dirty though because some calls could be skipped!
`
if(SDL_GetTicks() % 5000 <= 20) {
    // How long was it ago that another five seconds passed?
    conoutf(CON_DEBUG, "See u in 5 seconds again!");
}
`

## Using static variables to control code flow
As you surely know, static variables keep their values and will not be deleted from the Stack after the function is called. They are very similar to global variables but can't be accessed outside of the code block (block scope).

`for(int i=0; i<100; i++) {
     static int test = 0;
     test++;
     if(test > 30 && test < 40) conoutf(CON_DEBUG, %d lays between 30 and 40, i);
     // break, continue...
}` 

# New features
* Automatic time recording system with procedure hierarchy and "ingore" passages
* Realtime output on screen so you dont spam your history with conoutf(..);
* Event system for debug breaks (if values exceed ranges or bounderies)

## Recording system
Modern system can measure the time with up to 1 Microsecond precision (Linux even Nanoseconds). A Second is made out of 1000 miliseconds, each milisecond consists of 1000 microseconds. So 1 Microsecond is 1 millionth of a second. That should be enough precision!

## Process time
Let's say the code parts which renders one frame are a unit of code. It takes some time (some microseconds) to run through this code. We could measure this time as follows:

`benchmark.Begin("rendering");
// Rendering....
gl_RenderOneFrame();
benchmarking.End("rendering");`

Now we can read how long it takes to run this code:
`unsigned long long ullHowLong = benchmarking.LastCall("rendering");`

## Process time hierarchy
gl_RenderOneFrame(); contains many function calls as well. We can now link them to the "rendering" group:

`benchmarking.Begin("renderplayermodels", "rendering");`

# /showdebug [0-3] info
to be contined...