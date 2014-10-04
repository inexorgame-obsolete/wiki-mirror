### Goal

Enet is fine for transfering the game data like position changes and other game events. Also, enet is fast and has a low latency. But for some use cases it's not nessessary to have a low latency and enet makes things more complicated. XMPP is a multi purpose protocol which is interoperable and extendable. Many higher level funtionalities can be implemented on top of XMPP. The goal is to process game information more easily, make SauerFork more interoperable and profit from already implemented functionalities of XMPP.

### Use Cases

* Dezentralized propagation of game server information ("Masterserver")
** coordinates of game server
** player presence (we also have to think about privacy)
** easy integration of a server list in external programs: websites, desktop client, mobile client

* Game server capabilities

* Chat
** Ingame
** Lobby on Masterserver(s), Gameserver(s)
** Private Chat: Player to Player without the need to be connected to a specific game server
** Transports: Chat with other chat protocols (facebook, google talk, icq, ...)
** Outgame: Chat with a normal XMPP client (Pidgin, Xabber, ...)

* Game states
** JSON
** Per game
*** Flags per team
*** Bases captured per team
** Per player
*** Frags, Teamkills, Scores, ...

* File Transfer Types
** Broadcast (like /sendmap): player <-> server
** Direct/private: player <-> player

* File Transfer Content
** Maps
** Textures
** Models
** (Game modes, Plugins ...)

### Developers

* ?

### Implemenation Details

#### Infrastructure

* There are multiple XMPP servers
* Each game server is a XMMP client
* Each player is a XMMP client

#### Server list propagation ("Masterserver")

* Each server knows a list of game servers
* A game server pulls the server list periodically from other game servers (we need some sort of validation here)
* A game server pushes a notification about his presence to the known game servers periodically
* Entries in the local server list that are older than
** one hour are not propagated anymore
** one week are deleted
* When a game server get a new entry:
** already in the list: propagation enabled again
** not in the list: 
* Direct share: A player can send a server coordinate to another player
* Blacklists (providing malware, spyware)

#### Server capabilitities ("extinfo")

* A game server provides information about his capabilities
** Maybe a just a JSON document
* Once a client knows about a game server it can ask it for it's capabilities
* The list of capabilities is extensible

Typical capabilities:

* available game modes
* enabled game modes
* maximum number of players
* plugin extensions

### Additional / Future posibilities of XMPP

XMPP is an extensible format, so at a later point we may make use of other features.
List of XMPP extensions: http://xmpp.org/xmpp-protocols/xmpp-extensions/

### Not 