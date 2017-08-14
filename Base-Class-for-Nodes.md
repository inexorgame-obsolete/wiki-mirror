In this article we will define which members and methods a base class for Visual Scripting Nodes should have.

# Members (= Class Variables)

## Position

```
vec position;
```

Because we're implementing a 3D Visual Scripting System, every node needs to have a **position vector** that describes its position in 3D space. 

## Comment

```
string comment;
```

The user should be abled to add a comment to every script node.

# Methods (= Class Functions)