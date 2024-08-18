Drongo's Config Generator
v018
16 July 2019

Overview
Drongo's Config Generator (DCG) is a simple addon designed to allow the quick and easy creation of new factions (using existing assets). It is editor/loadout based and mostly WYSIWYG. It generates complete config.cpp files ready to be built into .pbo files.

NOTE: Do not use the Faction, Group or Weapon modules in the same mission as each other. Also be aware that any factions made with 3rd-party mods will have those mods as a dependency.

INSTALLATION:
Copy ConfigDumpFileIO.dll (or ConfigDumpFileIO_x64.dll for 64 bit version of Arma 3) into your Arma 3 directory.
Install the pbo files as with any Arma mod.

Instructions:
FACTION:
1) Make and save a mission with all units (edited loadouts) and empty vehicles you wish to use.
2) In the Variable Name field of every unit, enter the desired Display Name of the class (eg. Rifleman, Rifleman_AT). Use _ instead of spaces.
3) Place a DCG Generate Faction module and enter the tag, faction name and side.
4) Press "Play Mission" and wait a few seconds.
5) A message will appear giving the name of your output file (it will be in your Arma 3 directory)
6) Paste the contents of this file into your config.cpp and compile with Arma Tools
7) Put the pbo files from step six in a mod folder and start Arma 3 with that mod folder enabled

GROUPS (optional):
1) Make a mission with units formed into the groups you want.
2) In the Callsign field of each group, enter the desired name of the group (eg. Fire Team, HQ section). Use spaces, not underscores.
3) Place a DCG Generate Groups module and enter the tag, faction name and side (must be the exact same as used with the Faction module).
4) Press "Play Mission" and wait a few seconds.
5) A message will appear giving the name of your output file (it will be in your Arma 3 directory)
6) Paste the contents of this file at the end of your config.cpp (after the faction stuff) and compile with Arma Tools
7) Put the pbo files from step six in a mod folder and start Arma 3 with that mod folder enabled

WEAPONS (optional):
NOTE: This is not necessary if you enable "Generate Weapons" in the faction module.
1) Make and save a mission with all units (edited loadouts) you wish to use (ONE WEAPON ONLY FOR EACH UNIT)
2) Note that only the weapon and weapon attachments will count (no magazines etc will be checked)
3) Place a DCG Generate Weapons module and enter the tag and addon name (you can use the same faction name from the Faction Generator)
4) Press "Play Mission" and wait a few seconds.
5) A message will appear giving the name of your output file (it will be in your Arma 3 directory)
6) Paste the contents of this file into your config.cpp and compile with Arma Tools

HOW TO USE MULTIPLE CONFIGS TOGETHER:
1) Create weapons first, then the faction, then groups.
2) Create a folder in your project folder with the name of your addon (eg. Projects\MyCoolMod)
3) Under the folder above, create a subfolder called Weapons (eg. Projects\MyCoolMod\Weapons)
4) Generate your weapons, rename the output file to config.cpp and copy it into Projects\MyCoolMod\Weapons
5) Generate your faction.
6) Generate your groups.
7) Copy and paste the contest of the group file at the very end of your faction file (on a new line).
8) Save the faction file and rename it config.cpp.
9) Copy this file to Projects\MyCoolMod.
10) Compile MyCoolMod, then copy the pbos and play.


Other Information
Factions:

Ranks control which units are used as crew:
LIEUTENANT: Vehicle crew
CAPTAIN: Armour crew
MAJOR: Helo crew
COLONEL: Fixed wing crew
If these are not defined, the system will use the very first defined man as the crew instead.

Groups:
NOTE: The dismounted men of vehicle groups must not be placed inside the vehicle (or they will be ignored).

Ranks control infantry Spec Ops and Support groups. Set the group leader's rank.
COLONEL: Spec Ops
MAJOR: Support
Any other rank: Infantry

Ranks control vehicle Motorized, Mechanized, Armored, Airborne and Air groups. Set the group leader's rank:
COLONEL: Armored
MAJOR: Mechanized
CAPTAIN: Airborne
LIEUTENANT: Air
Any other rank: Motorized

Known Bugs:
Identity etc is not currently generated (the base unit is used)
Group icons are not yet implemented
Units with random uniform/texture scripts in the base unit's config will have their uniform/camo overwritten (can be mitigated with class EventHandlers{};)
Uniforms may not show up for units on a different side (Bohemia bug, not mine)

Credits:
Drongo: Scripting
