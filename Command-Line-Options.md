### Configuring Inexor Flex

Command Line Option | Short | Default | Description
------------------------ | ----- | --------- | -----------
--flex-port              | -p    | 0         | The port of the flex webserver
--preferences            | -u    | $HOME/... | The path to the user preferences file

### Configuring Inexor Core (Client) Instances

Command Line Argument    | Short | Default   | Description
------------------------ | ----- | --------- | -----------
--start-clients          | -c    | 1         | Starts N instances of Inexor Core (Client)
--client-1-width         | -w    | 640       | Sets the screen resolution width
--client-1-height        | -h    | 480       | Sets the screen resolution height
--client-1-grpc-port     | -p    | (auto)    | The port to use for GRPC

### Configuring Inexor Core (Server) Instances

Command Line Argument    | Short | Default   | Description
------------------------ | ----- | --------- | -----------
--start-servers          | -s    | 0         | Starts N instances of Inexor Core (Server)
--start-server-enet-port | -e    | 31415     | The port to use for the server ENET port

### yargs

https://www.npmjs.com/package/yargs

### Sauerbraten Command Line Options

http://sauerbraten.org/docs/config.html#command_line_options

