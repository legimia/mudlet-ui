# Complete package source

Everything shipped in `KrynnNativeUI_v0.8.10.mpackage` is expanded here.

The stable `KrynnNativeUI.mpackage` contains the same script and XML content, with its archive entry named [package/KrynnNativeUI.xml](package/KrynnNativeUI.xml). Keeping the download and entry names stable allows future releases to use the same package identity; the script still reports its internal version.

- [KrynnNativeUI.lua](KrynnNativeUI.lua): the full Lua script, decoded from the XML so it can be read as normal Lua.
- [package/KrynnNativeUI_v0.8.10.xml](package/KrynnNativeUI_v0.8.10.xml): the exact XML file from the archive, including script name, active state, and package metadata. Mudlet can import this XML too.

The archive contains **one XML file with one active script**, named `Krynn Native UI v0.8.10`. There are no other bundled files, images, separate alias/trigger definitions, or third-party libraries. The script creates its widgets, temporary alias, trigger, timers, and event handlers at runtime. Mudlet supplies Geyser and the protocol APIs.

## Feature-by-feature code guide

| Feature | Functions / code in the Lua file |
| --- | --- |
| Initial state and saved dimensions | Initial `K` fields, `readLayout`, `saveLayout` |
| Protocol decoding and common display helpers | `decode`, `V`, `any`, `collection`, `card`, `bar` |
| Player statistics | `renderPlayer`, `webStats`, `webInfoLine` |
| Group and combat display | `renderGroup`, `partyResource`, `combatHealth`, `combatBar` |
| Affects and countdowns | `affectEntries`, `K.syncAffectsClock`, `K.renderAffectsPanel`, `K.startAffectsTimer` |
| Quests | `renderQuests` |
| Room parsing, targets, and actions | `roomKeyword`, `K.roomSetTarget`, `K.roomSend`, `K.renderInteractiveRoom`, `K.captureRoomLine` |
| Graphical map and exits | `explicitExits`, `renderGraphicMap`, `K.renderGraphic` |
| ASCII map and legends | `legendAscii`, `legendGraphic`, `drawAsciiMap`, `K.renderMap` |
| Chat capture, colors, filters, and history | `K.classifyChatLine`, `K.captureChatLine`, `K.appendChat`, `K.renderChat`, `K.loadChatHistory`, `K.clearChat` |
| Gauges and MSDP subscriptions | `K.updateGauges`, `K.subscribe` |
| Map dragging and zoom | `K.panStart`, `K.panMove`, `K.graphMove`, `K.graphWheel` |
| Sidebar resizing and map split | `K.applyWidth`, `K.applySplit`, width/split drag callbacks, `K.resetLayout` |
| Widget construction | `K.makeUI`, `label`, `button`, `gauge` |
| Visibility, cleanup, diagnostics | `K.show`, `K.hide`, `K.shutdown`, `K.status`, `K.roomDebug`, `K.graphDebug` |
| Commands and startup | `K.command` and the final trigger, alias, timer, and event registration code |

## Editing and releases

These files expose the installed code without changing it. The XML copy matches the archive byte for byte; the Lua copy matches the XML script text after XML entity decoding.

The `.mpackage` remains the installable release artifact. Editing the extracted Lua does not update that archive automatically. Import changes into Mudlet and export an updated package, then refresh the extracted source for that release. Do not install both the archive and its XML as separate copies of the UI.
