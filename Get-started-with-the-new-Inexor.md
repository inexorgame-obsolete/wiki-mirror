Once you've completed the build procedure the procedure to start Inexor got complicated a little, due to ongoing refactorings and a new [[Overall Architecture]].
So this page serves as an introduction to the (temporal) startup-procedure.

Usually you would like to structure your game folder like this:

- inexor
  - bin (executable files)
  - flex (the InexorFlex submodule)

_That's the default directory structure if you clone the code repository and `make install` (or build the `install` target)_

By using the `flex` command line, you can get the client started.

**Note: You need to have InexorFlex running already!** Do this by executing `npm start` inside the flex folder inside another terminal window. If something changed or you try to run InexorFlex for the first time do `npm install && npm start` instead!

---
Inside the `flex` folder do:

`node inexor client create 31225 --start` which should bring up an Inexor window.

on Linux this can abbreviated to:

`./inexor client create 31225 --start`

This should:

1. Bring up flex, if not started _(Verification needed? I do not think this is true! See the `Note` above)_
2. Clone media repositories if they haven't been cloned
3. Start an InexorCore instance at port `31225 `, connect and initialize it via flex