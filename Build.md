## Linux

### Ubuntu 14.04

#### Install required packages

> sudo apt-get install git cmake build-essential libsdl{,-mixer,-image}1.2-dev libgl1-mesa-dev

#### Update Submodules

> git submodule update --init

#### Build

> mkdir build && cd build && cmake .. && make install

