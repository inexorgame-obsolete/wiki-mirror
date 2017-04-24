Once you've completed the build procedure you can get rolling with flex and Inexor.
Usually you would like to structure your game folder like this:

- inexor
  - bin (executable files)
  - `flex` (could be a symlink or you clone flex there)

By using the `flex` command line, you can get the client started.
From the `flex` folder, assuming that a `bin` folder is present in the parent directory, do the following:

`./inexor client create 31415 --start` which should bring up a Inexor window.
