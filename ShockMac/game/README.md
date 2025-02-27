SOURCE CODE STRUCTURE
=====================

This directory contains the source code for the game itself, as opposed to the helper libraries that are found elsewhere.

The source code is made up of the following files. (This README is in progress; I have not characterized all of the files yet.)

* AI / Critters
  * [ai.c](AI.C)              - Lowlevel monster control, death, loot tables, etc.
  * [newai.c](NEWAI.C)        - Monster AI states, path finding, combat decisions
* Automap
  * [amap.c](AMAP.C)          - Automap bitmap rendering
  * [amaploop.c](AMAPLOOP.C)  - Automap interactive processing for fullscreen
  * [fullamap.c](FULLAMAP.C)  - Fullscreen automap setup and interfacing
  * [automap.c](AUTOMAP.C)    - MFD minimap automap view
* UI
  * [status.c](STATUS.C)      - "Biorhythm" display logic & rendering
  * Multi-Function Display
    * [ammomfd.c](AMMOMFD.C)  - Display panel with list of weapons and ammo for each
    * [bark.c](BARK.C)        - Spontaneous messages from Shodan etc.
    * [biohelp.c](BIOHELP.C)  - If you have Bioscan upgrade, configure which "biorhythms" are displayed by [status.c]
* Audio
  * [audiolog.c](AUDIOLOG.C)  - Audio log player
  * [airupt.c](AIRUPT.C)      - Music mixing AI, music transition AI
* Trap/Trigger system, i.e. designer-created actions that respond to player/world/game events
  * "Trigger" - An object that reacts when it detects player is in a certain place, has done a certain action, etc.
  * "Trap" - Behaviors that designers can make happen in reaction to triggers
  * [trigger.c](TRIGGER.C)    - Trap implementations, some trigger detection, "comparator" system for conditional execution of traps
* Rendering
  * [frmain.c](FRMAIN.C)      - Top-level function to call functions to render 3D scene, draw overlays, add SFX
  * [frcamera.c](FRCAMERA.C)  - Computer what 3D camera position/orientation to render from
  * [frclip.c](FRCLIP.C)      - Call CONE.C to find map tiles in frustum, then conservatively determine which are occluded
  * [cone.c](CONE.C)          - Determine which map grid cells are within a view frustum ("cone")
  * [frcompil.c](FRCOMPIL.C)  - Minor initialization & deal with map changing size (which never happens with the game, maybe could only happen in the integrated editor)
  * [gamesort.c](GAMESORT.C)  - Sort objects in a single map tile for rendering (complicated because of e.g. force bridge partitioning into top & bottom halves)
  * [frobj.c](FROBJ.C)        - Draw all objects in a single map tile using GAMESORT.C and GAMEOBJ.C
  * [gameobj.c](GAMEOBJ.C)    - 3D rendering of all object types

<!--done A*.c, B*.c, trigger status frmain frcamera frclip cone frcompil gamesort frobj gameobj --!>
