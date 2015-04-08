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
 * Microsoft Visual Studio
    * download [VS 2013 Express Edition](http://www.microsoft.com/en-us/download/details.aspx?id=44914) - requires Windows 7 SP1 or newer
 * **OR as an alternative:** [Code::Blocks](http://www.codeblocks.org)
   * please [download here](http://www.codeblocks.org/downloads/26) the latest release, with the `mingw-setup` addition

* Download and install [CMake](http://www.cmake.org/download/)
   * cmake will generate your project files

* Download and install git
   * one of the best ways to develop is git, and one of its best interfaces is SmartGit
   * its free for personal use
   * Use one of the following tools if you don't already have git:
     * [SmartGit](http://www.syntevo.com/smartgit/download) - [Supports submodules in the GUI](https://www.syntevo.com/smartgit/documentation/5/show?page=submodules)
     * [GitHub for Windows](https://windows.github.com) - GUI does not support submodules. You must use the CLI to update them.
     * [Cygwin](https://cygwin.com/) - probably overkill just for access to git.
     * [git-scm.com](http://git-scm.com/download) is the official git website, and has downloads for the CLI version, and links to GUIs.

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

* If you use GitHub for Windows:
  * Go to the overview of our `code` repository and click on `Clone in Desktop`
  * Choose a directory in which the repository is getting cloned
  * Click `Ok`

## Create the Visual Studio or CodeBlocks Project
  * (or the project file for another generator)

Open the CMake-GUI and follow the steps as [described here](#cmake-gui). Then jump back to this point to not get confused with explainations for linux ;)

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
 
***

# Linux
## Fetching the sources

The first step of building this project is rather obvious, but for sake of completeness here you have it.

* Download the repository, you can either use the command line `git clone --recursive https://github.com/inexor-game/code.git` or your favourite git GUI.

* If you want to checkout the latest master only you need to initialise the submodules as well
 `git clone --depth 1 https://github.com/inexor-game/code.git; git submodule init; git submodule sync; git submodule update;`
## Downloading the dependencies

The next step is to get all the required dependencies to compile. On Windows and Mac, all the dependencies are packed in the `src/platform_*` directories. You only need an environment that can build C++ programs such as Visual Studio, CodeBlocks, XCode or MinGW.

On Linux you will need cmake, make, gcc (or clang) and the dev packages of mesa, SDL, SDL_image, SDL_mixer, ASIO and Google Protobuf. On systems with apt-get you can simply run the following command `sudo apt-get install git cmake build-essential libsdl2{,-mixer,-image}-dev libgl1-mesa-dev libprotobuf-dev protobuf-compiler libasio-dev`

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

### CMake GUI

Some users might prefer CMake GUI. 

   * Select your Inexor root directory for `Where is the source code`
   * Create a new directory within the root directory named `build`
   * Select the new `build` directory for `Where to build the binaries`
   * Click `Configure`
   * Select your desired generator
     * If you use Visual Basic select the highest VS-Version it finds and (if you have) the x64-Version so e.g. `Visual Studio 12 Win64`
   * Click `Generate` to generate a project file

## Actually building the sources

This step greatly depends on your IDE or environment but if you have used makefiles you can probably just run `(cd build && make install)`. Add `-j<number of cores>` to make to run it multithreaded.

## CMake Variables

The following variables can be used to change the behaviour of the build system.
You can specify them from the command line like this: `-D<variable name>=<value>`

* **RELEASE_BUILD** _default: `0`_
  
  This will create a release package when set to `1`.

  It also changes:
   * The version format to not include the git hash.
   * The default build type (**CMAKE_BUILD_TYPE**) from `Debug` to `Release`.

* **CMAKE_BUILD_TYPE** _default: `Debug`_

  Built in CMake variable that affects flags that are used to compile. For example `-O0` when debugging and `-O3` in release mode.

* **CMAKE_TOOLCHAIN_FILE** _default: ``_

  The path to the toolchain file to use for cross compiling. Change this to `../src/platform_windows/linux-toolchain-mingw.cmake` to cross compile for windows.
  
## Troubleshooting

This is a list of common problems and their solutions

* `Keep your directories clean, don't build in the main directory!`
  
   This error means that you are telling CMake to generate project files inside the project's root directory.
   You should keep your root directory clean and create a directory named build inside the root directory.
   Then tell CMake to generate to that directory instead of the root directory.
   To do this from the commandline, just use `(mkdir build; cd build && cmake -G "<your generator>" ..)`.