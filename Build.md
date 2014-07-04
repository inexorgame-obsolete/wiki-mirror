## Linux

### Ubuntu 14.04

#### Install required packages

> sudo apt-get install git cmake build-essential libsdl{,-mixer,-image}1.2-dev libgl1-mesa-dev

#### Checkout From Git Repository

> git clone https://github.com/sauerbraten-fork/sauerbraten-fork.git

#### Update Submodules

> git submodule update --init

#### Build

> mkdir build && cd build && cmake .. && make install

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
  