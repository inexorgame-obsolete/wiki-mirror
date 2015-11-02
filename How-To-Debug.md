This page serves as simple basic instruction on how you can eliminate a lot of crashing bugs by simply using some tools!

Firstly you will probably notice that on crash you see a log of lastly executed commands (on Windows you see that in an additional appearing window, on Linux and OS/X it appears in the command line and of course in the log.txt file.)

What we do now is called *stepping* and it basicly means you go step by step through your program to see which line of code the error caused.

# Windows (Visual Studio)

To enable stepping you have to set your configuration to Debug (Release won't work).
Now we need to find a way to start your executable inside Visual Studio. This requires the following steps:

### Start Inexor inside VS
1. Copy all necessary shared libs from `bin/windows/__your_architecture__/´ to your executable intermediate folder `build/inexor/client/Debug`
  * this basicly means you copy all files from the old place, except inexor.exe and inexor.pdb
  * if you do not have files inside `bin/windows/__your_architecture__/` (your_architeture of course beeing either win32 or win64 depending on your system), you need to build the `install` project inside your inexor solution once.
2. Set an execution folder (and arguments)
  1. Right click the `inexor` project inside your solution explorer, select `Properties` (Straight down on the bottom of the list)
  2. Select the `Debugging` section
  3. Add `-t0 -glogdebugging.txt` to `Command Arguments` (This means we always want to start in windowed mode and specify a log-file where all output is saved to)
  4. Forward the `working directory` to the base dir of your inexor project (or where your data repo is)
    * that's the place you'd normally start the inexor.bat from, so one above `media`
  5. Save and close
3. Set the `inexor` project as the startup project
  * This is done by right clicking the `inexor` project in the solution explorer again and selecting `Set as Startup-Project`

Now, we can start Inexor inside Visual Studio by simply pressing the `Debug` button in the toolbar (The play button in the upper middle of your screen :P ).

Now to the next and last part:

### Find the bug

Luckily we do not start from scratch, we`ve got some starting point: our output of the lastly executed functions!
So what we want to do now is:
 
1. Pause the program just before the bug probably occurs
2. Going step-by-step (call by call, function after function) forward, checking values and when what causes the bug.

For doing 1., we need to set a `Breakpoint` that is done by either:
* Right clicking a specific code line (in your place i'd choose the second last function of the callstack and in that function the first line after the brace) and select 'Breakpoint' -> `Insert Breakpoint`
* Or shorthand by just clicking left of the text line in the reserved area.

A red point will appear left of your line, marking that specific spot.

Now you have to start the program (click the Play-Button ;) ) and try to reproduce the bug somehow (if it lastly appeared while shooting rockets, you .. well you get the point)

Yay! We made it till here, now make it to the end: You'll notice that your program stopped and threw you back to the text-editor. The Breakpoint line is now also marked with a yellow arrow. This arrow marks your current line.

Now to the find the actual stepping:

You can control how fastly your code continues by using the Debug-Tool-Bar (it freshly appeared, there will be some arrows saying `Step over`, `Step into`, `Step out`.. if you hover them in your upper middle toolbar.
You can check values of variables by simply hovering them.

Here you go, you can find the error now easily by going step by step through your program till it crashes, noting the line and what values the variables in your line had when it crashed!

