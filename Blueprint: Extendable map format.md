### Objective

Create a map format which is forward and backward compatible, modular and extendable.

### Author(s)

* Hanack

### Goals

* Maps can be loaded by older and newer clients
* Store more complex data structures
* Saving data from plugins / extensions / mods

### Description

#### Maps can be loaded by older and newer clients

* Older servers and clients profit from maps build by mappers with a newer client
* Features saved in the maps are ignored if an older client don't know them

#### Store more complex data structures

* The new entity (+particle) system can't be saved in such a static way the old map format is (5 integers for each attribute)
* References to other data (internal)
* References to other data (internal)
* Serialization / Deserialization
* Compression

#### Saving additional data from plugins / extensions / mods

* Plugins, extensions and mods may have to store additional data in a map (for example for special game modes)
* External tools, websites and the API can read the data

#### Minimal data

* Metadata
* Octree
* Variables
* Textures
* Entities
* Lightmaps
* PVS
* Blendmaps
