### Objective

Create a map format which is forwards and backwards compatible

### Author(s)

* Hanack

### Description

* Newer clients can read older maps
* Older clients can read newer maps
 * ignore new features they haven't implemented

The map format have to be extendable:

* Separate things
* Allow references within the document
* Allow references to external documents