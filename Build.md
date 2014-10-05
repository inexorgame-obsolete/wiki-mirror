# Windows
This will give you a pretty good exemplary environment if you code on Windows.

## Setup

* Download and install [Visual Studio](http://www.microsoft.com/en-us/download/details.aspx?id=34673)
   * the Express Edition is enough
   * on Windows 8.1 or later download [VS 2013](http://go.microsoft.com/?linkid=9832256&clcid=0x409) instead

* Download and install [CMake](http://www.cmake.org/download/)
   * cmake will generate your project files

* Download and install [SmartGit](http://www.syntevo.com/smartgit/download)
   * one of the best ways to develop is git, and one of its best interfaces is SmartGit
   * its free for personal use

## Fetching the Repository

You will have to download the Project somewhere.

* Open SmartGit

* Clone the Repository
  * click `Repository` and `Clone` (or press `Ctrl+Shift+O`)
  * Select "Remote Git ... repository", Url = https://github.com/sauerbraten-fork/sauerbraten-fork
  * On the next Page select both `Include Submodules` as well as `Fetch all Heads and Tags`
  * Select a folder on the next page. Your local Git repository will be created here. 
  * Select `Finish`

## Create a seperate Branch
In Git, you can develop in different branches. An animated Tutorial can be found here: [Learn Git Branching](http://pcottle.github.io/learnGitBranching/) . This tutorial is for the command-line Git, but you should know the underlaying basics to use SmartGit properly.

* Right click `Local Branches`
  * You will have to select your repository before
* Select `Add Branch`
  * name it `<yourname>/<newfeature>`, eg. `BarackObama/World_Domination`
* Click `Add Branch & Checkout`
  * `Checkout` means you are using this branch:
     * All files in your directory will be switched if you have different ones in this branch

## Create the Visual Studio Project
* Open CMake-Gui
   * Select your sauerfork-main folder as `Source Folder`
   * Create a new directory inside your main directory called "Projectfiles" as `Where to build the binaries` 
   * Click Generate
     * Select the highest VS-Version it finds and (if you have) the x64-Version so e.g. `Visual Studio 11 Win64`
   * Click Configure

## Develop your feature
* Open build/sauerbraten-fork.sln
   * It will automatically open with Visual Studio
* At every logical step, commit your work to git
   * Commit often
      * Your feature has to be merged into other branches as easy as possible
      * Big commits often make problems then
   * Try around with SmartGit a bit to do that
* Push your work to the remote repo on github

# Linux
## Fetching the sources

The first step of building this project is rather obvious, but for sake of completeness here you have it.

* Download the repository, you can either use the command line `git clone --recursive https://github.com/sauerbraten-fork/sauerbraten-fork.git` or your favourite git GUI.

## Downloading the dependencies

The next step is to get all the required dependencies to compile. On windows and mac, all the dependencies are packed in the `src/platform_*` directories. You only need an environment that can build c++ programs such as Visual Studio, XCode or MinGW.

On Linux you will need cmake, make, gcc (or clang) and the dev packages of mesa, SDL, SDL_image and SDL_mixer. On systems with apt-get you can simply run the following command `sudo apt-get install git cmake build-essential libsdl{,-mixer,-image}1.2-dev libgl1-mesa-dev`

## Running CMake

The next step is to run CMake, this tool generates project files for your favourite IDE or tool.
If you have cmake in your path you can run `(mkdir build && cmake ..)`, you probably will need to add a `-G "<generator>"` flag to make it generate a project file for your precious IDE (you do not need this for makefiles on linux).

The most commonly used generators will probably include `Visual Studio`, `MinGW Makefiles`, `Unix Makefiles` and `Xcode`. There are also makefiles for Eclipse, CodeBlocks, Sublime Text and a lot others. The complete list can be found [here!](http://www.cmake.org/cmake/help/v2.8.11/cmake.html#Generators).

### Examples

```shell
(mkdir build; cd build && cmake .. && make install) # Should work on mingw (you may need -G "MinGW Makefiles"), linux and mac
(mkdir xcode; cd xcode && cmake .. -G Xcode) # Generate an xcode project
md vstudio && cd vstudio && cmake .. -G "Visual Studio 12" :: Generate a Visual Studio 12 Project

```

### GUI

Some users might prefer CMake GUI, you will probably have to select a source directory and a build directory. Set the source directory to the root directory of the sauerbraten-fork project and the build directory to a new directory inside the other named build. Then select the desired generator and create a project file.

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

## Build Environment

### One-Click Build environment

The script `install-homunculus.sh` in the `tools` folder can be used to automatically compile Sauerbraten fork or to generate Eclipse, Code Blocks, Xcode projects. For Mingw users it can also generate visual studio projects.

It works on OS X, Debian (and derivatives, e.g. Ubuntu), Arch Linux and MinGW.

Just download and run it.

Mac users will have to install XCode first.

### Manual Installation of the Build Environment

First you need to install the dependencies. Those boil down to:

* Git
* A compiler (e.g. GCC)
* A linker (e.g. GCC)
* Cmake
* OpenGL
* SDL
* SDL_Image
* SDL_Mixer

Depending on your environment you also need some of those:

* make (linux, mingw)
* Eclipse (if you want to use eclipse)
** egit Plugin (install it using the Eclipse Marketplace)
* Xcode (under Mac OS X)
* CMake GUI (optional)
* Github for Mac/Windows (optional)