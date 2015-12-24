Branches | Issues | Main developers
-------- | ------ | ---
master | [#4](/inexor-game/code/issues/4) | [@a-teammate](/a-teammate), [@Fohlen](/Fohlen), [@Croydon](/Croydon)

## Media Repositories
Since we split data files from the code files for using Git with less waiting time, we have 2+ repositories now for a single Inexor game.  
So you'll need to bring back the data repositories (data (required) , data-additional (optional), data-playground (optional), ..) with the code repo.

This is the structure you want:

```
bin
media
    data
        map
        texture        
        ..
    additional
        map                   // more info on the exact package directories see below
        texture
        ..
inexor.bat
inexor_unix
..
```
To create this structure you'll need to git clone (more info on Git [here](https://github.com/inexor-game/code/wiki/Build)) the contents of the [data](https://github.com/inexor-game/data), [data-additional](https://github.com/inexor-game/data-additional) and [data-playground](https://github.com/inexor-game/data-playground)) repos in seperate subfolders inside `media`.  
**Only the main `data`-repository is required**, but the other ones provide some more maps and stuff, so you'll probably want them, too.  
It doesn't matter how you name the folders inside media, they'll all get mounted.

_To start Inexor you should remember to always use the specific scripts (`inexor_unix` on linux, `inexor.bat` on windows)._
_Therefore you need to build the `install` target before, more on that see [Build](https://github.com/inexor-game/code/wiki/Build)._

## Content Structure
```
config                        // previously known as "data"
    saved.cfg                 // previously known as "config.cfg"
    restore.cfg
    server-restore.cfg
    server-saved.cfg
    ...
media                         // previously known as "packages"
  core                        // this is the packagedir
    brush
    interface
        radar
             radar.png
             blip.png
             ...
        background.png
        logo.png
    map
        dust6.cfg
        dust6.jpg
        dust6.ogz
        dust6.txt
        dust6.wpt
        ...
    model
        game
             base
             flag
             ...
        hudgun
        item
             boost
             health
             ...
        map
             nobiax
                  tropical_plants
                       ...
        player
             ironsnoutx10k
             ...
        worldgun
    music
    particle
    skybox
        nothing
            morning_up.png
            morning_dn.png            // ..
            morning.cfg               // Todo: A new cfg file for skyboxes
    sound
    texture
        a_teammate
             wood_golden_bar.cfg      // Todo: every texture has its own cfg!
             wood_golden_bar.png      // you can provide a package.cfg but you should forward to these individual cfgs
             wood_golden_bar_norm.png
             wood_golden_bar_depth.png
             ...
        inexor
             notexture.png  
             ...

```

Notice: everything is **singular**, otherwise its pretty self-explaining. 
Directories, to which map designers normally often add files, have a ``directory/nickname/stuff`` structure to keep them clean.

We encourage you to use subdirectories for different themes etc. so that you will get a structure like ``directory/nickname/theme1/stuff``, ``directory/nickname/another_theme/stuff``.

## Differences to Sauerbratens structure

* scripts are in config/
* config.cfg is named saved.cfg
* **Paths are relative to their executing file**
  * makes independent (shareable) folders possible

## In the future:
* every texture has its own cfg
* every skybox has its own cfg
