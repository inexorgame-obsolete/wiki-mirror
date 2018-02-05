![error: image not found!](https://raw.githubusercontent.com/inexorgame/visualisations/ee7c9356415c966670637256c8a57e75d2071265/agenda/agenda_logo_2.png)

Agenda is a 3D Visual Scripting System that is being developed for Inexor.

The word 'Agenda' is latin and stands for 'things that should be done'.

## Steps
> _What should be done is not just to implement Agenda but also all the stuff that the editors will come up with!_

### Step 1: Demand analysis
### Step 2: Implementation
### Step 3: Testing


## Demand Analysis
In this article we will discuss which requirements it must fulfill and what features we expect of it. This does not yet include any technical discussions about how it really works because this is part of Agenda's Architecture.

#### Client and Server Scripting Layers
TODO

#### Abstraction and Parametrization

TODO
#### Import and Export

TODO

## Architecture

#### Data Model for Nodes and Relations
As mentioned in the [[introduction article|3D Visual Scripting]], a set of **nodes** and **relations** is called a [graph](https://en.wikipedia.org/wiki/Graph_(discrete_mathematics))

The **direction** of relations with nodes is very important!

For the implementation we are probably going to use the [boost graph library](http://www.boost.org/doc/libs/1_64_0/libs/graph/doc/index.html).


#### Node Type Specifications
- Comment Nodes
- Event Nodes
- Timer Nodes
- Sleep Nodes
- Memory Nodes
- Geometric Area Nodes
- Function Nodes
- Operator Nodes
- If Nodes
- Switch Nodes
- While Loop Nodes

#### Rules for Connecting Nodes
1. A node can't be connected to itself
2. A node can't have more than one outgoing code execution relation

##### Other Specific Rules
Specific rules will be explained in the responsible node specification.

#### Script Code Execution Strategy
TODO
###### Code Execution Starting Points
TODO
###### Timer Multithreading
TODO

#### Use cases
TODO
#### Client and Server Scripting Layer
TODO
## Rendering

- Node Rendering
- Relation Rendering
  - [[Bezier Curve]]
- Visual Debugging

## Nodes

(This could maybe more effectively manifest itself inside a Pad?)

### Base Class for Nodes

In this article we will define which **members** (= class variables) and **methods** (= class functions) a base class for Visual Scripting Nodes should have.

#### Constructor
TODO

#### Destructor
TODO

#### Members

##### Position

```
vec position;
```

Because we're implementing a 3D Visual Scripting System, every node needs to have a **position vector** that describes its position in 3D space. 

##### Comment

```
string comment;
```

The user should be abled to add a comment to every script node.

#### Methods 
TODO

### Base Class for Memory Nodes

In this article we will define which **members** (=class variables) and **methods** a base class for memory nodes should have.

#### Constructor
TODO

#### Destructor
TODO

#### Members
TODO

#### Methods
TODO

### Comment node
#### Specification

A comment node does nothing at all. The value of ```m_comment``` will be rendered above the node. It has no imcoming or outgoing relations. Use comments whenever it is neccesary!

#### Class Members
```
std::string m_comment;
```

#### Constructors
none

#### Destructors
none

#### Methods
```
void SetComment(std::string comment);
void ResetComment(void);
```

### Geometric Area Nodes


- Box Nodes
- Sphere Nodes
- Cylinder Nodes
- Cone Nodes

TODO: Advanced geometric areas? ( Polygon Nodes )

### Memory Nodes

##### Simple Types

- Boolean Memory Nodes
- Integer Memory Nodes
- Float Memory Nodes
- String Memory Nodes

#### Advanced Types

- Timestamp Memory Nodes
- Vector Memory Nodes

#### Containers ?
- Memory Arrays

#### Abstract Data Types ?
TODO

### Sleep Nodes

A sleep node waits `sleep_interval` miliseconds before code execution continues.

#### Class hierarchy
```
class CSleepNode : public CScriptNode;
```

#### Constructors
TODO

#### Destructors
TODO

#### Members
```
unsigned int sleep_interval;
unsigned int sleep_start;
unsigned int sleep_end;
```

#### Methods
TODO

#### Minimum and Maximum Values

```
#define INEXOR_VSCRIPT_MIN_SLEEP_INTERVAL 10
#define INEXOR_VSCRIPT_MAX_SLEEP_INTERVAL 1000 * 60 * 60 * 24  // 1 day
```
