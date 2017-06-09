Branches | Issues | Main developers
-------- | ------ | ---
master | [#4](/inexor-game/code/issues/4) | [@a-teammate](/a-teammate), [@Fohlen](/Fohlen), [@Croydon](/Croydon)

## Inexor Files and Directories Structure
- Building Inexor:
	- **build** | *has to be created manually, holds all the build files*
	- cmake | *generates build configuration, used by conan*
	- CMakeLists.txt | *cmake configuration file*
	- conanfile.py | *conan configuration*
 	- dependencies.py | *references needed packages to be installed by conan*
	- **node_modules** | *contains modules installed using npm, currently only holds TOML module required for configuration*
	-  Continuous Integration:
		- appveyor.yml | *CI for Windows*
		- Jenkinsfile | *CI pipeline configuration file*
		-  **tool** | *contains scripts for easy compilation and continuous integration*

- Documentation
	- **doc** | *holds generated documentation*
	- doxygen.conf | *generates the configuration*

- Deprecated in the future:
	- history.cfg
	- init.cfg
	- inexor.bat
	- master.cfg
	- **media** (relocated, see *Out-of-tree*)
	- server-init.cfg
	- server.bat
- Game:
	- **bin**	| *game binaries*
	- **dist** | *holds per-distribution elements*
		- **Linux** | *contains freedesktop standard desktop entry file for integration with linux desktop environments* 
	- **flex** | *Node.js client and server management platform and scripting engine*
	- **inexor** | *contains the core engine called by inexor-flex*
	- **screenshot** | *contains screenshot taken by user*
	- inexor.log | *log file*
	- inexor_unix | *bash script to easily start inexor* on UNIX-like platforms 
	
- Information: (self-explanatory)
	- changelog.md
	- contributing.md
	- credits.md
	- license.md
	- readme.md

- Out-of-tree:  ( *~/.local/usr/share/inexor/* )
	- **media** | *holds hierarchically all contents used	by inexor-flex to feed inexor-core*	
		- **core** | *required media content*
		- **data-additional** | *additional media content, will be deprecated in favor of a content delivery system*
		- **user**  | *deprecated*


## Media Repositories
Since we split data files from the code files for using Git with less waiting time, we have 2+ repositories now for a single Inexor game.  
So you'll need to bring back the data repositories (data (required) , data-additional (optional), ..) with the code repo.

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
To create this structure you are required to git clone (more info on Git [here](https://github.com/inexor-game/code/wiki/Build)) the content of the [data](https://github.com/inexor-game/data) repository in a subfolder inside `media`.
 
If you want to have some additional maps, textures and other content you can clone [data-additional](https://github.com/inexor-game/data-additional) in a separate subfolder inside `media`. Only the main `data`-repository is required.

It doesn't matter how you name the folders inside media, they will all get mounted.

_To start Inexor you should remember to always use the specific scripts (`inexor_unix` on Linux, `inexor.bat` on Windows)._
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
