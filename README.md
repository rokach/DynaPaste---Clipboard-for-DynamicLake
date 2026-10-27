# DynaPaste DynamicLake Plugin

Clipboard history in a full DynamicLake lake.

The plugin executable is native Swift (universal, macOS 13+). The Swift source is included at `Sources/DynaPastePlugin.swift`.

## What it does

- Keeps what you copy: text, links, images, and files from Finder. Copying something already in the history moves it to the top.
- Opens as a big lake, like DynaClip: from the Left Click or Right Click Lake menus, from its DynaGlance button, or by pressing its live activity.
- Each row shows the item, the app it came from, and when. Images and image files show a thumbnail; other files show their Finder icon.
- **Copy** puts the item back on the clipboard; its icon turns into a checkmark and the lake closes.
- Right-click a row for Copy, Paste, Pin/Unpin, Open Link or Show in Finder, and Remove.
- Drag a row out to drop its text, link, file, or image into another app.
- The red trash (top left) clears everything that isn't pinned, after a confirmation. Pinned items stay at the top and don't count toward the history size.
- DynaGlance has its own compact view: the latest 10 copies with a copy button, right-click, and drag. Expanding it opens the full lake.
- The icons on the top right filter the list: All, Text, Links, Images (copied images and image files), and Files. It's back on All the next time the lake opens.
- The lake shows the newest 20 items (DynamicLake's 160-component lake budget); older ones are kept up to the history size.
- Copies from password managers are skipped.

History is stored in `~/Library/Application Support/DynaPaste/` (inside DynamicLake's container when it's sandboxed): `history.json` and copied images in `Images/`.

Hosts without the `lakeLayout` feature get a header-only lake with the latest copy and a copy button.

## Settings

- **History Size** – how many unpinned items to keep (10–200).
- **Keep Images** – save copied images.
- **Ignore Passwords** – skip copies marked concealed or transient (nspasteboard.org).
- **Show Copies in the Notch** – briefly show each copy as a live activity (on by default).

## Notes

- **Paste** sends Command-V to the front app and needs Accessibility permission:
  System Settings ▸ Privacy & Security ▸ Accessibility ▸ enable **DynamicLake Pro**.
  The first Paste without it asks for the permission.
- Text is kept as plain text.

## Checks

From this package:

```sh
./dynapaste --check
./dynapaste --demo-json
```

`--check` prints the history size, the Accessibility status, and the clipboard's current types. `--demo-json` prints sample lake commands, one per line.

## Build

```sh
swiftc -O -parse-as-library -target arm64-apple-macos13 Sources/DynaPastePlugin.swift -o /tmp/dynapaste-arm64
swiftc -O -parse-as-library -target x86_64-apple-macos13 Sources/DynaPastePlugin.swift -o /tmp/dynapaste-x86_64
lipo -create /tmp/dynapaste-arm64 /tmp/dynapaste-x86_64 -output dynapaste
```

---

# DynaPaste---Clipboard-for-DynamicLake
Clipboard plugin for DynamicLake

THIS PLUGIN IS 98% VIBED CODE PLUGINS SO YOU CAN LEARN FROM IT HOW TO MAKE PLUGINS TO DYNAMICLAKE

