## Why Node.js? Why CEF? Why an HTML based UI?

This question comes up often in the IRC. Specifically people want to know why we want to move away from Cubescript and why not use some common gaming language like LUA.


The decision what language to choose, was made because of a couple of factors:

1. Maintainance: We want to have to maintain as little code as possible our selves.
2. Existing GUI frameworks
3. How well the language is known.

Our choce of node.js+js+cef excels in all categories:
CEF provides a full web browser to work with;
Node JS a fully featured, but extensible server framework;
JS is extremely well known;
There is a very large base of libraries for both node.js and browser. In fact node.js allows us to write easily write business grade applications from the start.

Cubescript and LUA are seriously problematic in most respects:
We'd have to write a GUI framework and a standard library ourselves;
LUA is indeed well known, but our specific GUI libs and stdlibs would not be;
Same goes for cubescript, but we'd additionally have to maintain even the core language and parsers and compilers ourselves;
That's specifically problematic because IMO we'd never even get near any compilers/interpretes as advanced as LUAJit or V8. Both use JITs which is pretty awesome.

Python or Ruby (or erlang or groovy ...) are certainly as excellent as node.js, but since we will be using JS in the browser, better introduce just one language.

Node.js uses protocol buffers to communicate with inexor, the web browser uses http to comunicate with node.js. Node.js and Inexor will run in different processes and it would even be possible to run node.js, inexor and the Web UI on completely different computers. This introduces huge complexities which is a serious drawback.
APIs will have to be used hide those complexities for third party developers.

The distributed system also has some advantages:

1. Node.js can very easily be replaced by other languages
2. It is much easier to implement in C++  (provided we don't want to implement standard libraries for those languages ourselves)
3. The protocols designed in this process can replace enet in the future
4. Since the GUI is simply web, we get a free web GUI for servers and for clients
