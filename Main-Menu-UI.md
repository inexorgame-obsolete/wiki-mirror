Main project page: https://github.com/inexorgame/inexor-core/wiki/User-Interfaces
The main menu provides the means to navigate the core contents of the game.

  - [Main pages](#main-pages)
  - [Further planning](#further-planning)
  - [Key indicators](#key-indicators)
    - [First impression](#first-impression)
    - [Involving users](#involving-users)
  - [Design](#design)
    - [Examples](#examples)
  - [Pages](#pages)
    - [Splash screen](#splash-screen)
    - [Main Menu/Navigation](#main-menunavigation)
    - [Server browser](#server-browser)
    - [Settings](#settings)
    - [Profile/Account](#profileaccount)
    - [Community](#community)
    - [Own content (Recently created/worked on)](#own-content-recently-createdworked-on)

## Main pages

* Splash screen
* Server browser
* Settings
* Profile/Account
* Community
* Own content (Recently created/worked on)

## Further planning

See issue: https://github.com/inexorgame/inexor-core/issues/586  
Contains a roadmap and current tasks to push this project further.

## Key indicators

### First impression

Since this part of the game is accountable the first impression, it is very important to come to an agreement how the UI should look, feel and behave.

### Involving users

We want users to get into the game as quickly as possible, but still allow for elaborate user involvement.
Users can establish their place with the community. Allowing for easily sharing their contents, arranging games (duels, clan-fights, etc) or getting in touch with other players.

> Inexor will end up being kind of a sandbox, and in fact it is already. Users should be able to create their own themes and distribute them among their friends.  
> From [[The-Main-Theme]]

It is important to recite this here, to discuss the implementation details. What points in the menu does the user have to interact with the community?

It would be great to have a similar experience as Steam has with its workshop - where users can publish their own content, download others. This could work ingame as also as a website to see the content. This would allow us to offer something as [Quadropolis](http://quadropolis.us/) (which was the community hub of Sauerbraten) as our own service to our users.

## Design

> In order to be unique, another FPS in gray and black is not what we are aiming for. But the opposite: it should be colorful and weird.  
> From [[The-Main-Theme]]

We need to find a mix of offering the colorful weird UI we are looking for, but still allow for easily navigating.
A good next step is to compare to other splash screens/main menus of other games that offer a similar experience.

### Examples

TBD

## Pages

This section defines what content is found on the individual pages and what its purpose is. We also define how they are interlinked with each other.

### Splash screen

A short animation to introduce game logo, name, maybe even running version.
Can also contain a background video of the different mechanisms of the game to give a better insight what the player is getting into.

### Main Menu/Navigation

We need to decide, whether or not we provide a main menu to navigate the other pages, or if the navigation is always visible. Different concepts are outlined below.

The background can indicate different states during the game.
**Outside of a server:** slightly blurry video of a camera pan on a map.  
**On a server:** with faded out background, so you can still see what is happening in the background.  
**Singleplayer:** Current map as background or something that indicates that the game is paused.  

### Server browser

Finding, filtering, sorting and joining servers.
Hosting servers.
We need to prioritize which server properties to display:

* Servername
* ServerIP/Domain
* Players
* MaxPlayers
* Current Map
* Mode (In Sauerbraten, there is public, protected, private and auth)
* N Friends playing here

Other features: Mark server as favorite, list favorites

### Settings

Settings for the game can have many levels of complexity, since everything is a variable.

* General
  * Video
    * Rendering
    * Resolution
    * FOV
    * Performance filter
      * Particles
      * Lights
      * Glass
      * Models
  * Audio
    * Master
    * Map-Sounds
    * Player-Sounds
      * Footsteps
      * Jumps
      * Weapon
    * Music
  * Mouse
    * Sensitivity
  * Keybindings
  * Communication (Console)
    * Console
      * Filter (Events)
      * Colors
      * History
    * Link to profile settings
* Editing
  * Edit HUD
    * Crosshair
* Fighting
  * Game-mode specific settings
    * FOV, Crosshair, Zen-mode
  * Game HUD
    * Settings for widgets
      * Display Time
      * Crosshair
      * Damage compass
      * HUD Gun
  * Teamchat
    * Shortcuts (Cover me, restore flag, etc)
  * Scoreboard


#### Video

Sauerbraten went as far as allowing users to define whether or not to use glare, or fullbright models.

I would simplify this a bit in terms of performance levels.
There are still some settings that players have a personal taste for. E.g. Motion blur or fadetime of dead bodies.

### Profile/Account
### Community
### Own content (Recently created/worked on)
