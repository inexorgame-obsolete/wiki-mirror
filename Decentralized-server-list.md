## How the masterserver worked in the past?

* The masterserver controls the list of servers
* Each server registers on the masterserver
* Each client asks the masterserver for the list of servers

## What are the problems with the masterserver?

* Single point of failure (centralized server list)
* One person decides if a server is suitable or not
* Proprietary data format

## What we are changing

* No single point of failure (decentralized server list)
* No centralized decision about a server is suitable or not
 * Every server is welcome (regular game modes, added game modes, modded game modes)
 * Transparency (is the server modded)
 * Page-Rank like blacklist (malicious servers)
* Open data format
 * Readable (JSON, machine + human)
 * Available (REST API)
 * No language dependency (use whatever programming language you want to)
 * Information can be used everywhere (other servers, other clients, websites, csl-like software)
 * Extendible + backwards compatible
  * The information about servers in the Inexor Tree can be extended by additional information

## Server Identity

* vendor (only alpha numeric, eg psl, dk, nl)
* serverid ("[vendor][number]", only alpha numeric, eg psl4, dk1, nl4)
* ip
* port

## Server list storage

* Each server stores the list of other servers in it's own [[Inexor Tree]]
* Each client stores the list of (all) servers in it's own [[Inexor Tree]]

## Server list synchronization

### Between servers

* At startup a server
 * chooses some known servers randomly and fetches the server list -> the own server list is updated now
 * next, push information about itself to the known servers -> the remote server lists are updated now
* At shutdown
 * The list of servers is written down locally, we need to know the list of servers during the next startup
* At runtime
 * Regularly, each server push information about itself to the known servers (1x per hour)
 * If a server can't push information to a remote server multiple times, the remote server gets removed from the own server list
* Security
 * For security reasons, the remote server accepts changes only if the sender IP matches the IP in the data package
 * Blacklist
  * Malicious servers are blacklisted locally and changes from a remote server aren't accepted anymore
  * If a remote server wants to push a change, the local server can check the malicious state on other remote servers
  * Therefore the propagation about this server is stopped.
 * Whitelist
  * Servers can also whitelist remote servers which means they trust another known server
  * Incoming changes from a whitelisted remote server are always accepted, even when other remote servers are blacklisting the remove server

### Between server and client

* The client fetches the server list from randomly choosen servers using the Inexor Tree REST API
* As soon as a server is known by the client, it can fetch information from the known server directly
* Security
 * Clients can blacklist and whitelist servers locally
 * Clients can check if a server is blacklisted or whitelisted by multiple remote servers

## Inexor Tree

    a/
      /server
        /serverid
      /servers
        /[serverid|self]
          /ip
          /port
          /vendor
          /serverid
          /title
          /description
          /modded
          /moddingdescription
          /started
          /maxslots
          /categories
          /motd
          /blacklisted
          /whitelisted
