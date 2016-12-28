### Configuring Inexor Flex

Command Line Option      | Short | Default | Description
------------------------ | ----- | --------- | -----------
--flex-port              | -p    | 0         | The port of the flex webserver
--preferences            | -u    | $HOME/... | The path to the flex configuration file

### Command Line Commands

<pre>
./inexor start client
./inexor start client --width=640 --height=480 --fullscreen=0
./inexor start client --config=user.toml
./inexor start client --map=pandora
./inexor start server --instance=30001 --port=30000
./inexor start server --config=server.toml
./inexor mediadir add /usr/local/share/games/inexor-game/data
./inexor tree inexor.tree.path.to.the.node=value
</pre>

[Implementation details](https://www.npmjs.com/package/yargs#commandmodule) for [yargs](https://www.npmjs.com/package/yargs) commands

### Sauerbraten Command Line Options

http://sauerbraten.org/docs/config.html#command_line_options
