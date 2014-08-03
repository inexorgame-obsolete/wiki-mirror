## Coding Standards
###Pointers
Please use `char *pointer;` instead of `char* pointer;`
###Brackets
As you may see in the rest of the codebase, its always 

> void function() 

> { 

Please use that to keep consistency.

## Sauerbraten Uniques

###strings 
There are no "strings" as you may know them from C++, just clean char-arrays. 

`typedef char string[260]` in tools.h 

###classes / Structures
There are only structures, no classes. 

> struct mother : parent 

> {
>
> };

###vectors 
Not std as well but not really hard to understand.

**Initiate** them with `vector<mytype> variablename;`

**Add** something with `variablename.add(variable);`

**Use** an entry with `variablename[i];`

**Remove** an entry with `variablename.remove(i);`

This will also resort the vector (the next entry will take i's position).
 
So if `myintegers[0]` is `20`, `myintegers[1]` is `35` and `myintegers[2]` is `310` 

after `myintegers.remove(0); `

`myintegers[0]` is `35` and `myintegers[1]` is `310`