* [Windows](#windows)
* [Linux](#linux)
* [Get The Content](#get-the-content)
* [Troubleshooting](#troubleshooting)

***

# Windows
This will give you a pretty good exemplary environment if you are on Windows.

## Setup

* Download and install 
 * Microsoft Visual Studio **2015 (Update3)**
    * download and install [VS 2015 Community Edition](https://www.visualstudio.com)
    * on first start tell it to use the C++ package
        * do so by clicking "Create new C++ project"
    * only version 15 is supported _(otherwise you are required to rebuild the precompiled dependencies yourself)_

* Download and install [CMake](http://www.cmake.org/download/) >= v3.1.0
   * CMake will generate your project files

* Download and install Git
   * Use one of the following tools if you don't already have Git:
     * [SmartGit](http://www.syntevo.com/smartgit/download) - Heavily developed and intuitive GUI (e.g. Supports submodules in the GUI) (Recommended)
     * [GitHub Desktop](https://desktop.github.com) - Very simple and clean UI. Does not support submodules. You must use the command line to update them.
     * [git-scm.com](http://git-scm.com/download) is the official Git website, and has downloads for the CLI version, and links to several GUIs.



## Fetching the Repository

You will have to clone the Project somewhere.

* If you use SmartGit:
  * click `Repository` and `Clone` (or press `Ctrl+Shift+O`)
  * Select "Remote Git ... repository", URL = https://github.com/inexor-game/code
  * On the next Page select both `Include Submodules` as well as `Fetch all Heads and Tags`
  * Select a folder on the next page. Your local Git repository will be created here. 
  * Select `Finish`

* If you use GitHub Desktop:
  * Go to the overview of our `code` repository and click on `Clone in Desktop`
  * Choose a directory in which the repository is getting cloned
  * Click `Ok`
  * You will need to checkout the submodules as well, you can doing that by clicking on the wheel symbol, selecting `Open in Git Shell` and typing in `git submodule init; git submodule sync; git submodule update`

## Create the Visual Studio or CodeBlocks Project
  _(or the project file for another generator)_

Open the CMake-GUI and follow the steps as [described here](#cmake-gui). Then jump back to this point to not get confused with explanations for Linux ;)

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

## Cross-compiling from Linux to Windows
If you are using Linux to cross-compile Inexor to Windows using `mingw32` and `mingw-w64` then you should use
`cmake -DMINGW=1 -DMINGW_TYPE=X ..` where  X is your architecture (either use `i686` or `x86_64` in substitute of X )

***

# Linux
## Fetching the sources

The first step of building this project is rather obvious, but for sake of completeness here you have it.

* Download the repository, you can either use the command line ```git clone --recursive https://github.com/inexor-game/code.git``` or your favourite git GUI.

* If you want to checkout the latest master only you need to initialise the submodules as well
 ```git clone --depth 1 https://github.com/inexor-game/code.git; cd code; git submodule init; git submodule sync; git submodule update;```

## Downloading the dependencies

The next step is to get all the required dependencies to compile. For convenience, all the dependencies are prebuilt and packed in the `platform` directory. You only need an environment that can build C++ programs such as Visual Studio, CodeBlocks, XCode or MinGW.

Specifically, on Linux you will need CMake >= 3.1, make and GCC >= 4.9 or Clang >= 3.8 as your compiler. The version numbers are minimum: They might work with older versions (but it's not official supported) and newer versions are better!
Also install your distribution's development packages of Mesa, SDL2, SDL2_image, SDL2_mixer, Boost and Google Protobuf >= 3.0b3. Also you might need additional packages because of CEF, see the Debian row.

OS  | What to do
--- | ---
Debian/Debian-derived/Ubuntu | `sudo apt-get install git cmake build-essential libsdl2{,-mixer,-image}-dev libgl1-mesa-dev libprotobuf-dev protobuf-compiler libenet-dev libudev-dev libboost-all-dev clang llvm-dev libclang-dev doxygen`  CEF dependencies: `sudo apt-get install libfontconfig1 libfreetype6 libnss3 libxcomposite1 libxtst6 libgconf-2-4 libcups2 libcairo2 libpango-1.0-0 libpangocairo-1.0-0`
OpenSUSE | Run `zypper in -t pattern devel_C_C++` then run `zypper install mesa-libgl-devel libSDL2_mixer-devel libSDL2_image-devel libprotobuf-c-devel  protobuf-c libudev-devel boost-devel enet libenet7`.
ArchLinux | Run `sudo pacman -S --needed git cmake sdl2 sdl2_gfx sdl2_image sdl2_mixer protobuf mesa mesa-libgl enet boost boost-libs`. <br> Currently you need for libcef also some other dependencies, install them via: `sudo pacman -S --needed pango cairo libxi libxcomposite alsa-lib libxtst gconf libxrandr`

## Running CMake

The next step is to run CMake, this tool generates project files for your favourite IDE or tool.
If you have CMake in your path you can run `(mkdir build && cmake ..)`, you probably will need to add a `-G "<generator>"` flag to make it generate a project file for your precious IDE (you do not need this for makefiles on linux).

The most commonly used generators will probably include `Visual Studio`, `CodeBlocks`, `MinGW Makefiles`, `Unix Makefiles` and `Xcode`. There are also makefiles for Eclipse, Sublime Text and a lot others. The complete list can be found [here](https://www.cmake.org/cmake/help/v3.6/manual/cmake-generators.7.html).

### Examples

```shell
(mkdir build; cd build && cmake .. && make install) # Should work on mingw (you may need -G "MinGW Makefiles"), linux and mac
(mkdir xcode; cd xcode && cmake .. -G Xcode) # Generate an xcode project
md vstudio && cd vstudio && cmake .. -G "Visual Studio 14 2015" :: Generate a Visual Studio 14 Project

```

Notice: make sure to do *cmake ..* and *make* from a directory that is not referenced by a symlink somewhere in the path (otherwise you will have some problems with protobuf).

### Working around the libudev error
There is a known ABI change within libudev which might break libcef.so for you.
Refer to the [askubuntu article](http://askubuntu.com/questions/288821/how-do-i-resolve-a-cannot-open-shared-object-file-libudev-so-0-error) for technical details.
The suggested quickfix is
```
sudo ln -sf /lib/$(arch)-linux-gnu/libudev.so.1 /lib/$(arch)-linux-gnu/libudev.so.0
```

### CMake GUI

Some users might prefer CMake GUI. 

   * Select your Inexor root directory for `Where is the source code`
   * Create a new directory within the root directory named `build`
   * Select the new `build` directory for `Where to build the binaries`
   * Click `Configure`
   * Select your desired generator
     * If you use Visual Studio select VS-Version *Visual Studio 14 2015* and (if you have) the x64-Version so e.g. `Visual Studio 14 2015 Win64`
   * Click `Generate` to generate a project file

## Actually building the sources

This step greatly depends on your IDE or environment but if you have used makefiles you can probably just run `(cd build && make install)`. Add `-j<number of cores>` to make to run it multithreaded. Note that `make install` will not install any files globally, but only within the directory structure of the project.

## CMake Variables

The following variables can be used to change the behaviour of the build system.
You can specify them from the command line like this: `-D<variable name>=<value>`

* **CMAKE_BUILD_TYPE** _default: `Debug`_

  Built in CMake variable that affects flags that are used to compile. For example `-O0` when debugging and `-O3` in release mode.

* **CMAKE_TOOLCHAIN_FILE** _default: ``_

  The path to the toolchain file to use for cross compiling. Change this to `../inexor/platform/linux-toolchain-mingw.cmake` to cross compile for Windows.
  
* **BUILD_ALL=1** _default: `0`_

  Build _everything_.

* **BUILD_CLIENT=0** _default: `1`_

  Skips compiling the client.

* **BUILD_SERVER=1** _default: `0`_

  Compiling the server.

* **BUILD_MASTER=1** _default: `0`_

  Compiling the master server.

* **BUILD_GLUEGEN=1** _default: `0`_

  Compile gluegen.

## Run

Start Inexor with the `inexor_unix` file.


# Get the content

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
