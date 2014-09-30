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
    restore.cfg               //previously known as "defaults.cfg"
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
    particle
    texture
        a_teammate
             wood_golden_bar.cfg      //every texture has its own cfg!
             wood_golden_bar.jpg      //you can provide a package.cfg but you should forward to these individual cfgs
             wood_golden_bar_NORM.jpg
             wood_golden_bar_DEPTH.jpg
             ...
        notexture.png
    skybox


```
notice: everything is **singular**, otherwise its pretty self-explaining
### Developers

* a_teammate
* Fohlen