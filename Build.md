* [Windows](#windows)
* [Linux](#linux)
* [One-Click Build environment](https://github.com/inexor-game/code/blob/master/tool/README.md)
  * Script for automatic compile or generate project files
  * Works on OS X, Debian (and derivatives, e.g. Ubuntu), Arch Linux and MinGW

***

# Windows
This will give you a pretty good exemplary environment if you are on Windows.

## Setup

* Download and install 
 * Microsoft Visual Studio **13**
    * download [VS 2013 Express Edition](http://www.microsoft.com/en-us/download/details.aspx?id=44914) 
    * only version 13 is _supported_ [1]
    * requires Windows 7 SP1 or newer
 * **OR as an alternative:** Code::Blocks
   * please [download here](http://www.codeblocks.org/downloads/26) the latest release, with the `mingw-setup` addition

* Download and install [CMake](http://www.cmake.org/download/)
   * cmake will generate your project files

* Download and install git
   * Use one of the following tools if you don't already have git:
     * [SmartGit](http://www.syntevo.com/smartgit/download) - Heavily developed and intuative GUI (e.g. Supports submodules in the GUI)
     * [GitHub Desktop](https://desktop.github.com) - GUI does not support submodules. You must use the command line to update them.
     * [Cygwin](https://cygwin.com/) - probably overkill just for access to git.
     * [git-scm.com](http://git-scm.com/download) is the official git website, and has downloads for the CLI version, and links to GUIs.


[1] _otherwise you would need to rebuild the precompiled dependencies yourself_



## Fetching the Repository

You will have to clone the Project somewhere.

* If you use SmartGit:
  * Open SmartGit

  * Clone the Repository
    * click `Repository` and `Clone` (or press `Ctrl+Shift+O`)
    * Select "Remote Git ... repository", Url = https://github.com/inexor-game/code
    * On the next Page select both `Include Submodules` as well as `Fetch all Heads and Tags`
    * Select a folder on the next page. Your local Git repository will be created here. 
    * Select `Finish`

* If you use GitHub Desktop:
  * Go to the overview of our `code` repository and click on `Clone in Desktop`
  * Choose a directory in which the repository is getting cloned
  * Click `Ok`

## Create the Visual Studio or CodeBlocks Project
  _(or the project file for another generator)_

Open the CMake-GUI and follow the steps as [described here](#cmake-gui). Then jump back to this point to not get confused with explanations for linux ;)

## Compile Inexor
* If you use Visual Studio:
  * Open `build/Inexor.sln `
     * It will automatically open with Visual Studio
  * Right click the `INSTALL` solution in solution explorer, and click build.
* If you use CodeBlocks:
  * Open `build/Inexor.cbp`
  * Select the target `install`
  * Click on `Build`

## Get the data
We have seperated repositories for our code and the data. To actually start Inexor you will also need [the data](https://github.com/inexor-game/data). It's highly recommend to keep the repositories clean and to create a directory in which you compile + copy the data, to run Inexor.

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

The next step is to get all the required dependencies to compile. For convenience, all the dependencies are prebuilt and packed in the `inexor/platform` directory. You only need an environment that can build C++ programs such as Visual Studio, CodeBlocks, XCode or MinGW.

However on Linux you will need cmake, make, gcc (or clang) and the dev packages of mesa, SDL2, SDL2_image, SDL2_mixer, ASIO and Google Protobuf. On systems with apt-get you can simply run the following command `sudo apt-get install git cmake build-essential libsdl2{,-mixer,-image}-dev libgl1-mesa-dev libprotobuf-dev protobuf-compiler libasio-dev libenet-dev libudev-dev`

### Clang

If you are compiling with clang, you will also need libboost-regex1.55-dev and libboost-system1.55-dev. Alternatively you could build your entire stack with clang's c++ standard lib.

## Running CMake

The next step is to run CMake, this tool generates project files for your favourite IDE or tool.
If you have cmake in your path you can run `(mkdir build && cmake ..)`, you probably will need to add a `-G "<generator>"` flag to make it generate a project file for your precious IDE (you do not need this for makefiles on linux).

The most commonly used generators will probably include `Visual Studio`, `CodeBlocks`, `MinGW Makefiles`, `Unix Makefiles` and `Xcode`. There are also makefiles for Eclipse, Sublime Text and a lot others. The complete list can be found [here](http://www.cmake.org/cmake/help/v3.2/manual/cmake-generators.7.html).

### Examples

```shell
(mkdir build; cd build && cmake .. && make install) # Should work on mingw (you may need -G "MinGW Makefiles"), linux and mac
(mkdir xcode; cd xcode && cmake .. -G Xcode) # Generate an xcode project
md vstudio && cd vstudio && cmake .. -G "Visual Studio 12" :: Generate a Visual Studio 12 Project

```

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
     * If you use Visual Studio select VS-Version *Visual Studio 12 2013* and (if you have) the x64-Version so e.g. `Visual Studio 12 Win64`
   * Click `Generate` to generate a project file

## Actually building the sources

This step greatly depends on your IDE or environment but if you have used makefiles you can probably just run `(cd build && make install)`. Add `-j<number of cores>` to make to run it multithreaded.

## CMake Variables

The following variables can be used to change the behaviour of the build system.
You can specify them from the command line like this: `-D<variable name>=<value>`

* **CMAKE_BUILD_TYPE** _default: `Debug`_

  Built in CMake variable that affects flags that are used to compile. For example `-O0` when debugging and `-O3` in release mode.

* **CMAKE_TOOLCHAIN_FILE** _default: ``_

  The path to the toolchain file to use for cross compiling. Change this to `../inexor/platform/linux-toolchain-mingw.cmake` to cross compile for windows.
  
## Troubleshooting

This is a list of common problems and their solutions

* `Keep your directories clean, don't build in the main directory!`
  
   This error means that you are telling CMake to generate project files inside the project's root directory.
   You should keep your root directory clean and create a directory named build inside the root directory.
   Then tell CMake to generate to that directory instead of the root directory.
   To do this from the commandline, just use `(mkdir build; cd build && cmake -G "<your generator>" ..)`.

* Random errors like `XY was set to NOTFOUND`
   
   This can have multiply sources, probably your cmake cache is somehow disturbed by changes around it or you are missing parts of the repository.
   What you should try to solve this:
   Check for existence of the submodules folders: in `inexor/platform` should be files.  
   (Only needed if you do not use a GUI for git supporting submodules, like SmartGit): Furthermore these submodules need to be up to date if you previously checked out another version of the repo, so you need to do `git submodule update` to fetch the needed one.  
    And last but not least, if you previously created makefiles/projectfiles/whatever into a `build` directory, delete it and create a new `build` directory instead.