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

Make the shared variable available in the current context:

    namespace inexor { namespace rendering {
        extern SharedVar<int64> maxfps;
    } }

Getting the value of the shared variable by just using it (inexor magically hides the complexity):

    int64 maxfps2 = inexor::rendering::maxfps + 1;

Setting the value of the shared variable by just using it (Inexor magically synchronizes the changes):

    inexor::rendering::maxfps = 200;

### NodeJS

Just use the globally available object `inexor.tree`.

    var node = inexor.tree.getNode("pathAsString");

The node can either contain child nodes _(container)_ or has a value _(leaf)_.

    var value = node.get();

Setting a value of a (leaf) node:

    node.set("newValue");

Getting the value of a leaf node using the object notation:

    var value = inexor.tree.path.to.the.node;

If the node is a container you get the node instead of the value:

    var node = inexor.tree.path.to.the;
    var value = node.getChild("node"); // inexor.tree.path.to.the.node

Setting the value of a (leaf) node using the object notation:

    inexor.tree.path.to.the.node = "newValue";

    var node = inexor.tree.path.to.the;
    node.node = "newValue";

Add a child node of datatype string:

    var node = inexor.tree.path.to.the;
    var childNode = node.addChild("testNode", "string", "initialValue");

Add a child node which is a container itself:

    var node = inexor.tree.path.to.the;
    var childNode = node.addChild("testNode", "object");
    var childChildNode = childNode.addChild("testNode", "int64", 42);

### REST API

The REST API is available on the [[Inexor Client]] and on the [[Inexor Server]]. Additionally, parts of the REST API of the [[Inexor Server]] is public available.

| HTTP Method   | URL                                          | Description   | Result         |
| ------------- | -------------------------------------------- | ------------- | -------------- |
| GET           | http://localhost:48030/tree/path/to/the/node | Returns the value of a single node, if the node is a leaf (no childs) | value          |
| GET           | http://localhost:48030/tree/path/to          | Returns the subtree as JSON, if the node has childs | `{ the: { node: 'value' } }` |
| POST          | http://localhost:48030/tree/path/to/the/node | Changes the value of a node | - |
| DELETE        | http://localhost:48030/tree/path/to/the/node | Deletes the node              | - |
