Implementation of a very basic IPC method for Inexor.

Ultimately this should provide a method of sending CRUD commands to the Inexor process,
thereby making it possible to outsource most of the business logic to a high-level language,
while keeping the performance critical and graphic rendering stuff inside the C++ Inexor process.

See [[Inexor Tree API]] for the next steps.

### Current Status

The current status of the IPC implementation is very basic, but it works:
The communication between Client and Server works, there is some basic tests and it is documented to a large degree.

At the moment one RPC instruction is implemented, which lets a client execute arbitrary cubescript code on the server.

The purpose of this pull request is to kick of a public beta for this:
The basic architecture of Inexor has not been changed; using the IPC subsystem is completely opt in at the moment.

As the IPC system is always being compiled into the Inexor binary, protobuf and boost/asio is, beginning with this branch, a hard requirement for compiling Inexor.
Node.js is only required is one want's to test the reference client.

### Tech

The Inexor IPC protocol implements an RPC interface using google Protocol buffers to encode remote call instructions and to encode Function arguments and return values.
This utilizes a reliable, connection oriented transport that preserves message boundaries. At the moment we're either using stream oriented unix sockets or tcp and cut the streams manually.
TCP and Unix Sockets abstractions are provided by ASIO.

## Testing

### *nix

1. Run Inexor (and keep it running): $ inexor_unix
3. Execute in inexor: `initrpc`
4. Run the client: $ inexor_cipc_unix # A shell should open, INEXOR must be running for this!
  1. > Inexor = require 'inexor'
  2. > Inexor.eval "echo hallo123", (x) -> console.log x

You should now have a text "hallo123" in the console of inexor.

### Windows

1. Run Inexor (and keep it running)
2. Execute in inexor: `initrpc`
3. CD into the node directory
4. Update the node packages: $ npm update
5. Run the client: $ NODE_PATH=. node node_modules/.bin/coffee # A shell should open, INEXOR must be running for this!
  1. > Inexor = require 'inexor'
  2. > Inexor.eval "echo hallo123", (x) -> console.log x

You should now have a text "hallo123" in the console of Inexor.

## Further Direction

I am planning to add a few more basic features to the IPC interface:
* Event handling
* Locking (for sending a lot of commands to sauer consecutively)
* A remote object interface for things like the ents/players/...
* Method based cubescript interface (calling Inexor.cube.echo instead of Inexor.eval "echo ...")
* Improved IPC transports (e.g. shared memory queue + signals)


# PLEASE TEST :)
