# Introduction

> The goal is to implement *module_sound* in order to further modularize Inexor's code.

Inexor is using Cube2's old sound system which uses OpenAL and SDL_Mixer. It has no class design and is not documented at all which makes maintaining it quite unpleasant. 
This code is mostly separated from other code parts so the refactoring progress shouldn't be too complicated.

## Part I - Understanding the old sound system
_See main article:_ [[Cube2's old sound system code]]