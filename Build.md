## Fetching the sources

The first step of building this project is rather obvious, but for sake of completeness here you have it.

* Download the repository, you can either use the command line `git clone https://github.com/sauerbraten-fork/sauerbraten-fork.git` or your favourite git GUI.
* Make sure you download the submodules, you can do that using the following command `git submodule update --init` or again using your favourite git GUI.

## Downloading the dependencies

The next step is to get all the required dependencies to compile. On windows and mac, all the dependencies are packed in the `src/platform_*` directories. You only need an environment that can build c++ programs such as MinGW, xcode or VS.

On linux you will need cmake, make, gcc (or clang) and the dev packages of mesa, SDL, SDL_image and SDL_mixer. On systems with apt-get you can simply run the following command `sudo apt-get install git cmake build-essential libsdl{,-mixer,-image}1.2-dev libgl1-mesa-dev`

## Running CMake

The next step is to run CMake, this tool generates project files for your favourite IDE or tool.
If you have cmake in your path you can run `(mkdir build && cmake ..)`, you probably will need to add a `-G "<generator>"` flag to make it generate a project file for your precious IDE (you do not need this for makefiles on linux).

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
  