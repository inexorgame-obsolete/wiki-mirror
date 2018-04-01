# C++ API for creating the Inexor Tree

Actually in Inexor Core, the treelike structure is mainly implicitly given. The only difference between a normal variable and a variable shared in the tree is, that upon change, the change gets distributed to flex.  
The path of the variable in flex arrives from the namespace and the name of the class instance you place a variable in. Exemplary the path `rendering/screen/width` comes from `::rendering::screen.width`, where `rendering` is a namespace in which a variable of a struct-type called `screen` is placed, which contains a variable `width`.

The Tree contains no functions, only data.

## Generate the invisible code

We use an in-house code generator for building the synchronization code for all *SharedVars*.
It gets executed whenever the build folder was deleted or when explicitly triggered by building the target `gen_bindings_client` or `gen_bindings_server` (i.e. `make gen_bindings_client` when using make).
This is necessary when you added, removed or modified *SharedVars*.

## SharedVars
Declaring SharedVars is possible for various types of variables:

* The primitive types `char *`, `float`, `int`
* A list, array, queue or map
* A class or struct
* A pointer to any of the above


#### Declaring SharedVars -- Primitive Example

The code
```cpp
namespace rendering {
    SHAREDVAR(int, maxfps, 200, Range(0, 1000)|Persistent());
}
```
creates a SharedVar of type `int` named `maxfps`. It gets initialized with the value `200`.
The last argument of the macro is a list of [SharedVarAttributes](#SharedVar-Attributes).
The resulting path of the variable in the Inexor Tree is `rendering/maxfps`.

-------

**Note:**
The namespace `inexor`, which is used in C++ as the uppermost namespace for all (non-legacy) code, gets ignored when creating the Tree Path.
I.e. the code 

```cpp

namespace inexor {
namespace rendering {
    SHAREDVAR(int, maxfps, 200, Range(0, 1000)|Persistent());
}
}
```
results in the same variable `rendering/maxfps` in Inexor Flex.

#### Declaring SharedVars -- Classes example

Often a good design tries to encapsulate connected variables in a class or struct.

In the nature of C++ it is clear, that it is only possible to synchronize `public` SharedVars. Hence all entries must be public or get ignored.

```cpp
namespace inexor {
namespace rendering {
    class screen_t
    {
      public:
        SHAREDVAR(int, width, 1024, Range(0, 10000));

        screen(SomeWeirdType *t) {}
    };
    SHAREDVAR(screen_t, screen, Persistent());
} } // ns inexor::rendering
```

#### Declaring SharedVars -- Lists example

#### Declaring SharedVars -- Pointer example

#### Using SharedVars

You can treat the variable as if it is a normal primitive.  
For example a SharedVar `maxfps` could be used just like a normal variable
```cpp
int minframetime = 1/maxfps;
```
However when setting the SharedVar, the change will be synchronized to any other component which has the tree
```cpp
maxfps = 300;
```

## SharedVar-Attributes

With *SharedVar-Attributes* one can attach logic to the variables with minimal effort.
Each *SharedVar-Attribute* is actually a class definition, hence they get syntax-highlighted correctly in most IDEs.
Using the Operator `|` one can attach more than just a single *SharedVar-Attribute* to a *SharedVar*.

Although it is easily possible to create SharedVar-Attributes oneself, there are currently two SharedVar-Attributes usable by default

* Range(minimal, maximal)
* Persistent()


**Do not use logic as arguments for SharedVar-Attributes**!
    * e.g. `Range(1024, std::min(1200, 1440))` will definitely not work!
    * Preprocessor logic is not forbidden though: defines will be correctly replaced before parsing the SharedVar.
