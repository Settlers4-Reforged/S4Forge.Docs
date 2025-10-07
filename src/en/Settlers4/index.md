# About
This documentation provides an overview of how Settlers 4 works internally.
It is intended for developers who want to understand the game's architecture, or modify its behavior.

The goal of this documentation is to be a glossar on interesting pointers, basic concepts and class definitions. 

## Getting Started
It is recommended to have a basic understanding of reverse engineering and C++/asm86 before beginning.
Tools like IDA Pro, Ghidra, or x64dbg can be very helpful for exploring the game's binary.

Due to the nature of reverse engineering with those different tools, there is no one complete set of binary documentation (function arguments, structs, etc.) available.
A good start is the `S4_MainR.pdb` distributed by Settlers United (Link soon).
It gives you all known function names and some global variables.

If you wish to update that debug database, please reach out to any of the maintainers of S4Forge (but mainly @WizzardMaker)
We are also happy to help you get started or if you have any questions!

Another great source on how the game works is [S4Forge](https://github.com/Settlers4-Reforged/S4Forge) itself.
Most APIs there have to interact with the game in some way, so you can find a lot of useful information in the codebase.
For a definition of the most important classes, check out the [header files](https://github.com/Settlers4-Reforged/S4Forge/tree/main/External) that are used for code generation in S4Forge.

## Concepts
There are various systems at work in Settlers 4.
These can be broadly categorized into the following areas:

- **Game Logic**: This includes the event handling, player actions, AI behavior, and game state management.
- **Rendering**: This encompasses the graphics engine, sprite management, and visual effects.
- **User Interface**: This involves menus, UI elements, and user input handling.
- **Networking**: This covers multiplayer functionality.

