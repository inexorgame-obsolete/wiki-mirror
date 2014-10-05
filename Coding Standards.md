#Develop modular, clean and document your work

###No spaghetti code
###No code duplication
###Refactor your work
###Comment Your Work
The Sauerbraten source is mainly uncommented at the moment, but we are about to change that.

Every new populated code should be clearly understandable, not only for you. 
The goal is to be get a quick overview by just reading the comments. 

Commenting is not a hard task, but an important one. **Your future self and other developers will appreciate the minutes you spend commenting**.

Read more in the dedicated wiki page: [Source Code Documentation](Source Code Documentation)

# Coding Consistency

###Pointers
Please use `char *pointer;` instead of `char* pointer;`

###Brackets
As you may see in the rest of the codebase, its always 

> void function()

> {

Please use that to keep consistency.

# Sauerbraten Uniques

###strings 
There are no "strings" as you may know them from C++, just clean char-arrays. 

`typedef char string[260]` in tools.h 

* **defformatstring(_stringname_) (_"Example %s %d and %u", char *a, int b, uint c_);**
 * defines `string _stringname_` and formats the second expression 
 * e.g. `a = "Values", b = -2, c = 5` will lead to `string stringname` beeing `"Example Values -2 and 5"`

* **formatstring(_stringname_) (_see above_);**
 * does **not** define `string _stringname_`
 * formatting works as above

###classes / Structures
There are only structures, no classes. 

> struct mother : parent 

> {
>
> };

###vector-containers
Vectors are extended arrays, which provide numerous abilities.
Sauerbraten's vectors are not those of the vector-class in c++. 

_(for more than the listed abilities check `tools.h`)_

* **Create** them with `vector<variabletype> vectorname;`

* **Add** a variable with `vectorname.add(variable);`

     The new Entry will be at the last place.

* **Use** an entry with `vectorname[i];`

* **Remove** an entry with `vectorname.remove(i);`

    This will also resort the vector (the next entry will take i's position).
 
    So if `myintegers[0]` is `20`, `myintegers[1]` is `35` and `myintegers[2]` is `310` 

    after `myintegers.remove(0); `
    
    `myintegers[0]` is `35` and `myintegers[1]` is `310`

* **Clear** the vector with `vectorname.shrink(0);` 

    or (if you do not want to delete its contents) `vectorname.setsize(0);`

* **Length** receive the amount of entries in that vector with `int len = vectorname.length();`

* **inrange** `bool hasi = vectorname.inrange(i);` tells you whether `vectorname[i]` is actually a thing. This could not be the case if e.g. i is below zero or higher than the amount of entries.

### Loops
* **loop(_var, int xy_)**
 * works as for(int var = 0; var < xy; var++);
* **loopi(_int xy_)**
 * works as for(int i = 0; i < xy; i++)
* **loopj(_int xy_)**
 * works as for(int j = 0; j < xy; j++)
* **loopk(_int xy_)**
 * you got it
* **loopl(_int xy_)**
 * still
* **loopv(_vector x_)**
 * works as for(int i = 0; i < x.length(); i++)
* **loopirev(_int xy_)**
 * works as for(int i = xy; i > 0; i--)