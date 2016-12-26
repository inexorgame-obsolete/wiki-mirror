* [Windows](#windows)
* [Linux](#linux)
* [Get The Content](#get-the-content)
* [Troubleshooting](#troubleshooting)

***

# Dependencies

There are seven hard dependencies currently for building Inexor.  
You will need to obtain them in some form (see the specific [Windows](#windows) and [Linux](#linux) sections below)

* git
  * a version control system
* [CMake](http://www.cmake.org/download/)
  * Generates our platform specific build code from cross platform scripts
  * >= v3.1.0
* A Compiler
  * Translates the human-readable source code to executable binary code
* [python](https://www.python.org/downloads/)
  * version doesn't matter, although 2.x is prefered to 3.x
  * we need it for our package manager conan
* [Conan](https://www.conan.io/)
  * Our package manager
    * (through which we obtain all libraries Inexor depends on)
* [node.js + npm](https://nodejs.org/)
  * This is the base for InexorFlex (our scripting environment)
  * npm (the node package manager) is usually included with node
* [Doxygen](http://www.stack.nl/~dimitri/doxygen/download.html)
  * This is needed for our build-time reflection
    * (code generation for our network code and scripting binding)
    * Yes, not only the docs

On Linux you will be able to download all these through your package manager.

# Windows
This will give you a pretty good exemplary environment if you are on Windows.

## Setup

* Download and install 
 * Microsoft Visual Studio **2015**
    * download and install [VS 2015 Community Edition](https://www.visualstudio.com)
      * _on first start tell it to use the C++ preset_
         * _do so by clicking "Create new C++ project"_
    * VS 2013 might also work but is definitely not recommended
    * **The newest update is required** (VS 2015 Update 1 will fail to build)
* Download and install Git
   * Use one of the following tools if you don't already have Git:
     * [SmartGit](http://www.syntevo.com/smartgit/download) - Heavily developed and intuitive GUI [Recommended]
       * You'll need to manually [**add Git to your PATH**](https://github.com/inexor-game/code/wiki/%5BWindows%5D-add-git-to-PATH)
     * [GitHub Desktop](https://desktop.github.com) - Very simple and clean UI.
     * [git-scm.com](http://git-scm.com/download) is the official Git website, and has downloads for the CLI version, and links to several GUIs.
* Download and install [CMake](http://www.cmake.org/download/)
* Download and install [python](https://www.python.org/downloads/)
  * version doesn't matter, although 2.x is prefered to 3.x
* Download and install [Conan](https://www.conan.io/downloads)
* Download and install [node.js + npm](https://nodejs.org/)
  * version does not matter, either LTS or normal
* Download and install [Doxygen](http://www.stack.nl/~dimitri/doxygen/download.html)
  * [**add doxygen to your PATH**](https://github.com/inexor-game/code/wiki/%5BWindows%5D-add-git-to-PATH)
    * Replace `git.exe` with `doxygen.exe` when searching, add it as the point 2 says.


## Fetching the Repository

You will have to clone the Project somewhere.

* If you use SmartGit:
  * click `Repository` and `Clone` (or press `Ctrl+Shift+O`)
  * Select "Remote Git ... repository", URL = https://github.com/inexor-game/code
  * On the next Page select `Fetch all Heads and Tags`
  * Select a folder on the next page. Your local Git repository will be created here. 
  * Select `Finish`

* If you use GitHub Desktop:
  * Go to the overview of our `code` repository and click on `Clone in Desktop`
  * Choose a directory in which the repository is getting cloned
  * Click `Ok`

## Create the Visual Studio or CodeBlocks Project
  _(or the project file for another generator)_

Execute the `tool/create_visual_studio_project.bat`.  
This will:

1. create a new `build` folder
  * which will contain your project file `Inexor.sln` (you can open that one to open VS)
2. receive all dependencies
  * (which **takes some time** the first time you do it) (using [`conan install`](http://docs.conan.io/en/latest/getting_started.html#building-the-timer-example) internally)
3. Create the VS project using CMake
4. do a first build
  * which also takes some time

So relax and sit back.

Advanced users can also manually do the conan-install step and and use the CMake Gui as [described here](#cmake-gui).

## Compile Inexor
* If you use Visual Studio:
  * Open `build/Inexor.sln `
     * It will automatically open with Visual Studio
  * Right click the **`INSTALL`** solution in solution explorer, and click build.
* If you use CodeBlocks:
  * Open `build/Inexor.cbp`
  * Select the target `install`
  * Click on `Build`

## Get the data
See [Directory-Structure](https://github.com/inexor-game/code/wiki/Directory-Structure) to see how your folder structure should look like to start Inexor.

## Run
Start Inexor with the `inexor.bat` file.

***

# Linux
## Fetching the sources

The first step of building this project is rather obvious, but for sake of completeness here you have it.

* Download the repository, you can either use the command line ```git clone --recursive https://github.com/inexor-game/code.git``` or your favourite git GUI.

## Install the build requirements

The next step is to get all the required dependencies to compile. You'll need an environment that can build C++ programs such as Eclipse, CLion, CodeBlocks.

Specifically, on Linux you will need CMake >= 3.1, conan, make and GCC >= 4.9 or Clang >= 3.5 as your compiler. The version numbers are minimum: They might work with older versions (but it's not official supported) and newer versions are better!
Also install your distribution's development packages of Mesa

OS  | What to do
--- | ---
Debian/Debian-derived/Ubuntu | `sudo apt-get install git cmake build-essential nodejs doxygen python-pip`  CEF dependencies: `sudo apt-get freeglut3 freeglut3-dev libglew1.5-dev libglm-dev`
OpenSUSE | Run `zypper in -t pattern devel_C_C++` then run `zypper install mesa-libgl-devel conan node doxygen cmake git`.
ArchLinux | Run `sudo pacman -S --needed git cmake mesa mesa-libgl conan doxygen`. <br> Currently you need for libcef also some other dependencies, install them via: `sudo pacman -S --needed pango cairo libxi libxcomposite alsa-lib libxtst gconf libxrandr`

### Installing conan.io
Conan.io is usually to be installed using the python package manager `pip`
Simply `pip install conan` should do it.
Although conan officially supports `python>=3` the version `python2.7` is suggested.

### Getting the latest Node.js
For the application to run appropiately `Node.js >= 6.9.1` is required (it might work on lower versions, ** it might**). 
Consider [their website](https://nodejs.org/en/) for install instructions.

## Running Conan & CMake

Run Conan to get all the used libraries in place. [conan instructions](http://docs.conan.io/en/latest/getting_started.html#building-the-timer-example) 
See the examples below.

Afterwards run CMake, which generates project files for your favourite IDE or tool.
If you have CMake in your path you can run `(mkdir build && cmake ..)`, you probably will need to add a `-G "<generator>"` flag to make it generate a project file for your precious IDE (you do not need this for makefiles on linux).  
Alternatively use the example lines below.

The most commonly used generators will probably include `Visual Studio`, `CodeBlocks`, `MinGW Makefiles`, `Unix Makefiles` and `Xcode`. There are also makefiles for Eclipse, Sublime Text and a lot others. The complete list can be found [here](https://www.cmake.org/cmake/help/v3.7/manual/cmake-generators.7.html).

### Examples

```shell
(mkdir build && cd build && conan install .. && conan build ..) # Should work for any setting any compiler, any OS
# By default conan install uses build_type `Release`.
(mkdir build && cd build && conan install .. -s build_type=Debug && conan build ..)
# to create a debug build and build it.
(mkdir build && cd build && conan install .. -s compiler=gcc -s compiler.version=5.2 && conan build ..)
# to set a specific compiler and version if you got multiple ones installed.
# Reading some stuff up in the conan docs might be helpful here
```

Notice: make sure to do *cmake ..* and *make* from a directory that is not referenced by a symlink somewhere in the path (otherwise you will have some problems with protobuf).

## Actually building the sources

This step greatly depends on your IDE or environment but if you have used makefiles you can probably just run `(cd build && make install)`. Add `-j<number of cores>` to make to run it multithreaded. Note that `make install` will not install any files globally, but only within the directory structure of the project.

## Run

Start Inexor with the `inexor_unix` file.

# Other

## Get the content

Data like maps and fonts is provided in a separate [data repository](https://github.com/inexor-game/data). Clone that repository along with the optional repository [data-additional](https://github.com/inexor-game/data-additional) in the `media` directory, which should be in the root directory of the Inexor code repository. Alternatively you can use a symbolic link like in the following example.

    .
    ├── code
    │   ├── bin
    │   ├── build
    │   ├── inexor
    │   ├── media -> ../media
    │   ├── node
    │   └── tool
    └── media
        ├── data
        └── data-additional

More on that see: [[Directory Structure]]

## CMake GUI

Some users might prefer CMake GUI. 

   * Select your Inexor root directory for `Where is the source code`
   * Create a new directory within the root directory named `build`
   * Select the new `build` directory for `Where to build the binaries`
   * Click `Configure`
   * Select your desired generator
     * If you use Visual Studio select VS-Version *Visual Studio 14 2015* and (if you have) the x64-Version so e.g. `Visual Studio 14 2015 Win64`
   * Click `Generate` to generate a project file

## Working around the libudev error

(On some linux systems)
There is a known ABI change within libudev which might break libcef.so for you.
Refer to the [askubuntu article](http://askubuntu.com/questions/288821/how-do-i-resolve-a-cannot-open-shared-object-file-libudev-so-0-error) for technical details.
The suggested quickfix is
```
sudo ln -sf /lib/$(arch)-linux-gnu/libudev.so.1 /lib/$(arch)-linux-gnu/libudev.so.0
```

## Troubleshooting

This is a list of common problems and their solutions

* `Keep your directories clean, don't build in the main directory!`
  
   This error means that you are telling CMake to generate project files inside the project's root directory.
   You should keep your root directory clean and create a directory named build inside the root directory.
   Then tell CMake to generate to that directory instead of the root directory.
   To do this from the commandline, just use `(mkdir build; cd build && cmake -G "<your generator>" ..)`.

* Random errors like `XY was set to NOTFOUND`
   
   This can have multiply sources, probably your CMake cache is somehow disturbed by changes around it or you are missing parts of the repository.
   What you should try to solve this:
   Check for existence of the submodules folders: in `platform` should be files.  
   (Only needed if you do not use a GUI for git supporting submodules, like SmartGit): Furthermore these submodules need to be up to date if you previously checked out another version of the repo, so you need to do `git submodule update` to fetch the needed one.  
    And last but not least, if you previously created makefiles/projectfiles/whatever into a `build` directory, delete it and create a new `build` directory instead.

* Core textures not found (e.g. `texture/inexor/notexture.png`)

    Two likely possibilities: Either you didn't get the [media repositories](#get-the-content) or you didn't start Inexor via the scripts (`inexor.bat` on Windows or `inexor_unix` on Linux).
