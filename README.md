# Krynn Native UI for Mudlet

A native Mudlet interface for Chronicles of Krynn, distributed as [KrynnNativeUI_v0.8.10.mpackage](KrynnNativeUI_v0.8.10.mpackage). The package contains the Lua UI script in Mudlet XML format.

## Installation

1. Download the `.mpackage` file.
2. Open your Chronicles of Krynn profile in Mudlet and install the file through Mudlet's Package Manager.
3. Connect to the game. The interface uses Mudlet's Geyser widgets and the game's MSDP data; information appears as the server supplies it.
4. Type `kui status` to inspect the UI status, or `kui connect` to request protocol subscriptions again.

## Features

- A right sidebar with **Game UI** and **Chat History** views, plus bottom gauges for HP, PSP, movement, and experience.
- **Player** panel with character identity, level, race, class, abilities, saving throws, and available combat, alignment, money, practice, position, and world-time values.
- **Quests**, **Group**, and **Affects** panels using server-provided data. Group resource bars show reported values; affects have per-occurrence duration clocks.
- **Room** panel that captures room contents after the `[ Exits: ... ]` line, keeps repeated NPC descriptions as separate occurrences, and lists objects and NPCs/characters.
- Clickable object actions: Look, Examine, Read, and Get. Character actions: Attack, Fire, Lore, and Look. Target keyword overrides help resolve ambiguous entries. These controls send game commands.
- Centered ASCII mapping and a graphical map view, with legend, dragging/panning, reset controls, and graphical zoom. Map observations are session-local and come from protocol data.
- Chat history filters for all messages, tells, group, local, channel, and immortal chat, plus unread indication, **Load History**, and **Clear Chat** controls. Up to 1,200 lines are retained during the Mudlet session.
- Drag handles for sidebar width and the map/information split, with saved layout dimensions in the Mudlet profile.
- Show, hide, refresh, shutdown, layout reset, and room/map diagnostics through the `kui` command.

## Useful commands

| Command | Action |
| --- | --- |
| `kui show` / `kui hide` | Show or hide the interface. |
| `kui refresh` / `kui connect` | Refresh the display or request MSDP subscriptions. |
| `kui player`, `kui quests`, `kui room`, `kui group`, `kui affects` | Select an information panel. |
| `kui ascii` / `kui graphic` / `kui legend` | Select the map display. |
| `kui mapreset`, `kui mapin`, `kui mapout` | Reset map pan or adjust graphical zoom. |
| `kui game` / `kui chat` | Switch sidebar views. |
| `kui chat tell` | Open chat history filtered to tells; also accepts `all`, `group`, `local`, `channel`, or `immortal`. |
| `kui width 500` / `kui split 50` | Set sidebar width or map split percentage. |
| `kui resetlayout` | Restore default layout dimensions. |
| `kui target object 1 sword` | Override the target keyword for the first object entry. |
| `kui roomclear` | Clear captured room contents. |
| `kui status`, `kui roomdebug`, `kui mapdebug` | Show diagnostic information. |
| `kui off` | Shut down the UI and its temporary handlers. Reload the package/script to initialize it again. |

## Data and limitations

Available information depends on the server's MSDP fields and room-output format. Missing values are left unavailable rather than invented. Room capture watches incoming text without hiding or modifying game output. Chat, map observations, room contents, and affects state are session-local; only UI dimensions are saved to `KrynnNativeUI_layout.txt` in the Mudlet profile. This repository supplies the installable package, not a separate unpacked development tree.

## Related Chronicles of Krynn tools

- [Color Text Editor](https://github.com/legimia/ansii-editor): offline colored description editing.
- [Crafting Studio](https://github.com/legimia/crafting-studio): recipe planning, bonuses, and command generation.
