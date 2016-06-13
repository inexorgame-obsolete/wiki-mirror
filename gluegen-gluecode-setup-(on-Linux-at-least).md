
###gluegen/gluecode setup (on Linux at least)

Following is a manual routine description for compiling gluecode/gluegen _(this belongs to the dev ninjabook!)_.

We presume you have a setup of the following structure

- You installed the necessary llvm/clang libraries
- Your folders are named code containing code/platform and build

If not solved yet (cross if fixed) you'll gotta figure a bit with the CMake file to get everything running.

- Locate your LLVM library folder. For me it was `/usr/lib/llvm-3.8`
- Modify `inexor/gluegen/CMakeList.txt` accordingly, see this [pastie](http://pastie.org/10874137#9-10)

#### Go ahead young padawan, let's build
From inside your `build` folder

 1. cmake ../code -DBUILD_CLIENT=0 -DBUILD_GLUEGEN=1 -DCMAKE_BUILD_TYPE=Release
 2. `make gluecodegenerator`
 3. Copy the binary to platform: `cp inexor/gluegen/gluecodegenerator ../code/platform/tool/linux`

Due to some issues you'll have to delete some things manually at the moment (cross if fixed)

 4. `rm ../code/inexor/rpc/treedata.gen.hpp`
 5. `rm ../code/inexor/rpc/treedata.gen.proto`
 6. `cmake ../code -DBUILD_CLIENT=1 -DBUILD_GLUEGEN=0 -DCMAKE_BUILD_TYPE=Release`
 7. `make run_gluegen`

Once this succeeded we built the actual client

 8. `cmake ../code DBUILD_CLIENT=1 -DBUILD_GLUEGEN=0 -DCMAKE_BUILD_TYPE=Release`
 9. `make`

**Use the executable luke!** `(inexor/client/inexor)`. 

You should have a working gRPC/gluegen setup now. Thanks @aschaeffner

_PS: Don't forget the power of `-jcores`!_
