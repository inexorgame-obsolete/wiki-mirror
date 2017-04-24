Once you've completed the build procedure you can get rolling with flex and Inexor.
Usually you would like to structure your game folder like this:

- inexor
  - bin (executable files)
  - `flex` (could be a symlink or you clone flex there)

By using the `flex` command line, you can get the client started.
From the `flex` folder, assuming that a `bin` folder is present in the parent directory, do the following:

`./inexor client create 31415 --start` which should bring up a Inexor window.

This should:

1. Bring up flex, if not started
2. Clone media repositories if they haven't been cloned
3. Start an inexor core instance at port `31415`, connect and initialize it via flex