# Sauerbraten Uniques and Code Style

This document will introduce you to the C-ish C++ of Cube2:Sauerbraten and all derivates.  
Please use it when contributing, to keep the coding style consistent.

### Strings examples

There are no "strings" as you may know them from C++, just clean char-arrays. 

`typedef char string[260]` in tools.h 

---------  

```c++
const char *examplestr   = "here we go: another example."     //pointers: char *name; instead of char* name;

void stringexample(bool isugly)
{                                                                        //a new line for the brackets
    string str;                     
    formatstring(str) ("You look so %s", isugly ? "ugly" : "beautiful");
    conoutf("%s", str);                                                  //console output "You look ugly" or "beautiful"
    
    copystring(str, examplestr);                                         //alternatively strcpy or strcat
    conoutf("%s", str);                                                  //"here we go: another example"
    
    filtertext(str, str, false, 10);                         //filtertext(destinationstr, sourcestr, whitespace, length

    conoutf("str now: %s", str)                                         //"herewego:an"
    
    float floatvalue = 0.1235;
    int intvalue = 200;

    //define and format in one step:
    defformatstring(valuestr) ("Floatval %f, cut floatval %.1f, intval %d or %i", floatval, floatval, intval, intval);

    conoutf("printf: %s", valuestr);   //"printf: Floatval 0.1235, cut floatval 0.1, intval 200 or 200"
}                             
```


* **defformatstring(_stringname_) (_"Example %s %d and %u", char *a, int b, uint c_);**
 * defines `string _stringname_` and formats the second expression 
 * e.g. `a = "Values", b = -2, c = 5` will lead to `string stringname` beeing `"Example Values -2 and 5"`

* **formatstring(_stringname_) (_see above_);**
 * does **not** define `string _stringname_`

###classes / Structures
There are only structures, no classes. 

---------

```c++
struct human 
{
    string name;
    int age;
    human() : age(0)                               //allocator
    {
        name[0] = '\0';                            //a fresh created human has neither an age nor a name
    }
};
struct person : human
{
    person *mum, *dad;
    bool goodcook;
    
    person(bool isgoodcook)
    {
        goodcook = isgoodcook;
    }
    ~person()
    {
        DELETEP(mum)                              //Delete pointer: if mum delete mum;
    }
};

vector<person *> otherguys;
//explanation for vector below
void example()
{
    otherguys.setsize(0);                             //fresh beginning, no other guys
    //add 20 persons:
    loopi(20)                                         //for(int i = 0; i < 20; i++)
    {
           otherguys.add( new person( rnd() % 2) );   //chances are 50-50 to have a good cook

           person *p = otherguys.last();              //ah, we forgot, lets get a name for him
           loopk(10) p->name[k] = rnd() % 26 + 'a';   //we are lazy, his name will be completely random 
    }
    conoutf("%d persons in \"otherguys\"!", otherguys.length()); //console output: 20 persons in "otherguys"!
    
    //tell me whos a good cook and remove everyone whos not!
    loopv(otherguys)
    {
         if(otherguys[i]->goodcook) conoutf("%s is a good cook", otherguys[i]->name);
         else otherguys.remove(i--);           //remove the current person and decrements i to correct the loop
    }
}
```
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