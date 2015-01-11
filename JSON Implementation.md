Everything in 2 source files: json.h and json.cpp, while you only need to read json.h to understand the API.
It furthermore tries to be as simplistic as possible, while giving everything one needs.
Everything is stored in a JSON-Structure.  

## Some General JSON-info:

There are 6 different data types in JSON:  
* ~~NULL Value _(Not recommended)_~~
* Bool
   * `true`
   * `false`
* Numbers
   * `-10`
   * `10.872`
   * `8.4e6` or `8.4E6`
* Strings
   * begin and end with `"`
* Arrays `[   ]`
   * ordered list
* Objects `{    }`
   * unordered list of items
   * every item is a `"key: value"`-pair
      * you access them through the key name 


#Usage

Let's say you want to load some config stuff from an `important-settings.json`.

    {
        "name": "unnamed", 
        "screen": {
            "fov":      120,
            "fullscreen": false, 
        },
        "sensitivity": 3.28,
        "favorite maps": [
            "mach2",
            "academy",
            "europium"
        ]
    }

## Loading data from a file

Everything is stored in a JSON-Struct, so let's firstly catch all the JSON we have from the file.

    JSON *settings = loadjson("important-settings.json");

Done.  

## Working with the data

Thou now we have it in our JSON-struct, now how can we access the data?  

* j->value...
   * valuestring (if type == string)
       * otherwise ""
   * valueint    (if type == number)
       * otherwise 0
   * valuefloat  (if type == number)
       * otherwise 0
* subitem access:
   * getitem()
       * for arrays access by its position in the array e.g. `j->getitem(4)`
       * for objects (key:value-pairs) access by the name of the key ´j->getitem("fov")`

* subitem access + directly casted:
   * getfloat()
       * for objects e.g. "float sens = j->getfloat("sensitivity");
       * -1.0 if nonexistent
   * getint()
   * getstring()
       * "" if nonexistent

### Example:

Every Key:Value-pair is in its own JSON-structure,  
So changing the settings could e.g. happen like this:

    JSON *fov = settings->getitem("fov");
    if(fov) changefieldofview(fov->valueint);

or directly _(Attention: if "fov" is nonexistent it will return -1!)_

    changefieldofview(settings->getint("fov"));


## Writing Settings after changing them

* render()
   * returns a char array with the rendered JSON-tree
* save( filename ) 
   * saves directly into the specific file

### Example: 

You modify the values in your structure e.g. sensitivity:

    float newsens = 5.6;
    JSON *sens = settings->getitem("sensitivity");
    if(sens) sens->valuefloat = newsens;

or directly again:

   ..

and now save them to disk via:

    settings->save("evenbettersettings.json");

..


## Creating JSON Tree's from Scratch

* JSON *JSON_CreateBool(bool b);
* JSON *JSON_CreateInt(int num);
* JSON *JSON_CreateFloat(float num);
* JSON *JSON_CreateString(const char *str);
* JSON *JSON_CreateArray();  //new ordered list. access: position
* JSON *JSON_CreateObject(); //new unordered list. access: name

## And add it into another JSON

* additem()

## Example:

..


## Developers

* a_teammate

## Resources

* https://sourceforge.net/projects/cjson/