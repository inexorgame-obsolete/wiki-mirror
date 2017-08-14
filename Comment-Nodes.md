# Specification

A comment node does nothing at all. The value of ```m_comment``` will be rendered above the node. It has no imcoming or outgoing relations. Use comments whenever it is neccesary!

## Class Members
```
std::string m_comment;
```

## Constructors
none

## Destructors
none

## Methods
```
void SetComment(std::string comment);
void ResetComment(void);
```