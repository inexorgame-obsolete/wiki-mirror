## Design decisions

* Generic concept
* Intuitive for programmers, modders and server owners
* Extendible for modding, additional gamemode, 3rd party applications
* Central place where to store data
* Open

## Differences between Cubescript and Inexor Tree

### Cubescript

* Currently data and game state are spread all over the cube2 code base
* Some variables are accessible via cubescript
* The variables are located in a single flat namespace
* The names of the variables must be unique

### Inexor Tree

* The namespaces are organized hierarchical
* All variables are located in a namespace
* The names of the variables must be unique within a namespace only

## Accessing to Inexor Tree

### C++

* ...

### NodeJS

* inexor.tree.
* ...

### REST

* ...

