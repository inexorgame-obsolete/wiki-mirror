# Introduction
Nobody is perfect. (In case you are ignore the following paper and get back to work!)
Testing and debugging your code is the foundation of innovative and awesome features. Unfortunately, this is not always an easy task. Sauerbraten itself does not provide any built-in debugging or benchmarking tools.

## Guidelines for good code
Please keep in mind that good code
* has suitable comments for important code passages
* uses the Doxygen format for comments in order to support automatic documentation
* does not depend on OS-specific libraries
* is extendable and dynamic
* should be object-orientated
* should respect types (C/C++ has strong types!)
* should think twice about user input or function parameters
* keeps sub-modules in separated header files
* is clean and does not contain passages which aren't used or commented out (final code...)

## Use external debuggers
If not anything works, try to use external debugging tools.
Thanks to [VALVe's Vogl](https://github.com/ValveSoftware/vogl), there is finally a good OpenGL graphic debugger out there. There is also [apitrace](https://apitrace.github.io/).
Other software such as [PIX](http://en.wikipedia.org/wiki/PIX_%28Microsoft%29) or [Crytek RenderDoc](http://cryengine.com/renderdoc) are only for Microsoft DirectX.

# Debugging tricks

## Sauerbraten debug leftovers
command name | parameter | function | appearance
---------------- | --- | ------------------------- | ------------------------- | 
/debugao | 0 or 1 | debug ambient occlusion (?)| ? | | 
/debugdepthfx | 0 or 1 | debug depth function | rectangular area in top left screen | | 
/debugglare | 0 or 1 | debug glare shader (/glare must be 1) | rectangular area in top left of the screen | | 
/debugjson | 0 or 1 | debug JSON parser? | ? | | 
/debugparticles | 0 or 1 | debug the old Sauerbraten particle system | text table in left middle of the screen | | 
/debugparticles | 0 or 1 | debug the old Sauerbraten particle system | text table in left middle screen | | 
/debugsm | 0 or 1 | debug shadow map | rectangular area in top left of the screen | | 
/debugsm | 0 or 1 | debug shadow map | rectangular area in top left of the screen | | 
/aidebug | 0 - 6 | debug artificial intelligence (bots) | shows waypoints, additional text and text over bots | |
/dbgalias | 0 - 5 | debug alias lookups? | ? | | 
/dbgblob | 0 or 1 | ? | ? | | 
/dbgdds | 0 or 1 | ? | ? | | 
/dbgdec | 0 or 1 | ? | ? | | 
/dbgexts | 0 or 1 | ? | ? | | 
/dbgffdl | 0 or 1 | ? | ? | | 
/dbgffsm | 0 or 1 | ? | ? | | 
/dbggrass | 0 or 1 | ? | ? | | 
/dbggz | 0 or 1 | ? | ? | | 
/dbgmodes | 0 or 1 | ? | ? | | 
/dbgmovie | 0 or 1 | ? | ? | | 
/dbgpcull | 0 or 1 | ? | ? | | 
/dbgpseed | 0 or 1 | ? | ? | | 
/dbgubu | 0 or 1 | ? | ? | | 
/dbgvars | 0 or 1 | ? | ? | | 
/dbgzip | 0 or 1 | ? | ? | | 

## Miliseconds and SDL_GetTicks()
So far you can use [SDL_GetTicks()](https://wiki.libsdl.org/SDL_GetTicks) to get the number of miliseconds since the SDL initialisation (program start.)
`unsigned long ulStartTime = SDL_GetTicks(); // Store current time
SDL_Delay(100); // Wait 100 miliseconds
unsigned long ulEndTime = SDL_GetTicks(); // Store end time
conoutf(CON_DEBUG, "Well that took around %llu miliseconds..", ulEndTime - ulStartTime);`

## Do something every 5 seconds (workaround)
Some things are just way too heavy to print every sub-calculation to the screen. You should limit the output.
One method to do this is to calculate the modulo of SDL_GetTicks(). It's very dirty though because some calls could be skipped!
`
if(SDL_GetTicks() % 5000 <= 20) {
    // How long was it ago that another five seconds passed?
    conoutf(CON_DEBUG, "See you in 5 seconds again!");
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