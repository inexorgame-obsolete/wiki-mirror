##Content Structure
```
config                        //previously known as "data"
    ui                        //user-interface
        options.cfg
        scoreboard.cfg
        serverbrowser.cfg
        menus.cfg
    saved.cfg                 //previously known as "config.cfg"
    restore.cfg
    server-restore.cfg
    server-saved.cfg
    ...
media                         //previously known as "packages"
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
            morning_up.jpg
            morning_dn.jpg            //..
            morning.cfg               // Thats new(!) a cfg for skyboxes
    sound
    texture
        a_teammate
             wood_golden_bar.cfg      //every texture has its own cfg!
             wood_golden_bar.jpg      //you can provide a package.cfg but you should forward to these individual cfgs
             wood_golden_bar_NORM.jpg
             wood_golden_bar_DEPTH.jpg
             ...
        inexor
             notexture.png  
             ...

```

Notice: everything is **singular**, otherwise its pretty self-explaining. 
Directories, to which map designers normally often add files, have a ``directory/nickname/stuff`` structure to keep them clean.

We encourage you to use subdirectories for different themes etc. so that you will get a structure like ``directory/nickname/theme1/stuff``, ``directory/nickname/another_theme/stuff``.

##Differences to Sauerbratens structure

* scripts are in config/
* config.cfg is named saved.cfg
* every texture its own cfg
* every skybox its own cfg
* **Paths are relative to their executing file**
  * makes independent (shareable) folders possible


### Developers

* a_teammate
* Fohlen
* Nooby