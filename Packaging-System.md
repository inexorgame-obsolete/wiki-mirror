##Content Structure
```
bin
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
    interface
        radar
             radar.png
             blip.png
             ...
        background.png
        logo.png
    map
        turbine.cfg
        turbine.jpg
        turbine.ogz
        ...
    model
        game
        hudgun
        item
        map
        player
        worldgun
    particle
    sound
    texture
        a_teammate
             wood_golden_bar.cfg      //every texture has its own cfg!
             wood_golden_bar.jpg      //you can provide a package.cfg but you should forward to these individual cfgs
             wood_golden_bar_NORM.jpg
             wood_golden_bar_DEPTH.jpg
             ...
        default
             notexture.png  
             ...
    skybox
        nothing
            morning_up.jpg
            morning_dn.jpg            //..
            morning.cfg               // Thats new(!) a cfg for skyboxes

```
notice: everything is **singular**, otherwise its pretty self-explaining

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