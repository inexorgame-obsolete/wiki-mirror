## Linux

### Ubuntu 14.04

#### Install required packages

> sudo apt-get install git libsdl{,-mixer,-image}1.2-dev cmake build-essential libgl1-mesa-dev

#### Update Submodules

> git submodule update --init

#### Build

> mkdir build && cd build && cmake .. && make install

