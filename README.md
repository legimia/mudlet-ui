# Krynn Native UI for Mudlet

A native Mudlet interface for Chronicles of Krynn, distributed as [KrynnNativeUI_v0.8.10.mpackage](KrynnNativeUI_v0.8.10.mpackage). The package contains the Lua UI script in Mudlet XML format.

## Installation

### First: remove the original server-provided UI

If your Krynn profile already has the original UI downloaded from the MUD server, remove that package before installing Krynn Native UI. Running both interfaces can leave overlapping panels or competing screen borders.

1. Open your **Chronicles of Krynn profile** in Mudlet and disconnect from the game while changing packages.
2. Open **Preferences / Settings** (`Alt+P` on Windows/Linux). Find **Allow server to install script packages** and turn it off for this profile. In newer Mudlet versions it is under **Privacy and security → Server Permissions**; the location and wording may differ in older versions. Save/apply if your version provides that button. This prevents the original UI from being automatically installed again when you reconnect.
3. Open **Package Manager** from the toolbar (`Alt+O` on Windows/Linux).
4. Select the **original Krynn UI package supplied by the server**, then click **Uninstall** and confirm. Identify it using the package name and details shown in your profile; the installed name may differ between server package versions. Remove that UI package only, leaving unrelated packages and personal scripts in place.
5. Save the profile, close it, and reopen it to clear any panels or temporary handlers left by the old package.

Turning off server package installation does not uninstall a package that is already present, so complete both the preference change and the uninstall. Keep **MSDP enabled**: the new UI still needs the server's live character and map data. You do not need to disable GMCP or ATCP to stop automatic package installation.

If the old UI returns after reconnecting, check the server package installation preference again and remove the reinstalled original package. If you cannot identify the original package, ask for its exact name before uninstalling an uncertain entry.

### Install Krynn Native UI

1. Download [KrynnNativeUI_v0.8.10.mpackage](KrynnNativeUI_v0.8.10.mpackage).
2. In your Krynn profile, open **Package Manager → Install** and select the downloaded file.
3. Connect to the game. The interface uses Mudlet's Geyser widgets and the game's MSDP data; information appears as the server supplies it.
4. Type `kui status` to inspect the UI status, or `kui connect` to request protocol subscriptions again. The original server-provided interface should no longer be visible.

Mudlet references: [Package Manager](https://wiki.mudlet.org/w/Manual:Package_Manager) and [Profile Preferences](https://wiki.mudlet.org/w/Manual:Profile_Preferences).

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

Browse the [Chronicles of Krynn tools directory](https://github.com/legimia/chronicles-of-krynn) for all tools and getting-started instructions.

- [Color Text Editor](https://github.com/legimia/ansii-editor): offline colored description editing.
- [Crafting Studio](https://github.com/legimia/crafting-studio): recipe planning, bonuses, and command generation.
