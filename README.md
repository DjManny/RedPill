# Red Pill — 3D Matrix Screensaver for macOS

[![Build](https://github.com/DjManny/RedPill/actions/workflows/objective-c-xcode.yml/badge.svg)](https://github.com/DjManny/RedPill/actions/workflows/objective-c-xcode.yml)

A 3D OpenGL "Matrix"-style falling code screensaver for macOS.

## Fork Information

This is a fork of [Red Pill](https://github.com/lpar/RedPill) by mathew <meta@pobox.com>,
originally Copyright © 2002–2012. This fork adds GitHub Actions CI and ongoing maintenance.

## ⚠️ macOS Compatibility Notice

This screensaver uses **legacy OpenGL** (`GL_INTENSITY` textures, fixed-function pipeline,
`glBegin`/`glEnd`-style rendering). Apple deprecated OpenGL in macOS 10.14 (Mojama).

- **macOS 10.14 and earlier:** Fully supported.
- **macOS 10.15 (Catalina) – 12 (Monterey):** May work but with increasing issues.
- **macOS 13+ (Ventura and later):** OpenGL support is unreliable; the screensaver may not
  build or render correctly.

A migration to **Metal** is planned to restore full compatibility on modern macOS. See
[Issue: Migrate from OpenGL to Metal](../../issues) for progress.

## Build Instructions

### Prerequisites

- macOS with Xcode installed
- Command Line Tools: `xcode-select --install`

### Building from Source

1. Clone the repository:
   ```bash
   git clone https://github.com/DjManny/RedPill.git
   cd RedPill
   ```

2. Open the project in Xcode:
   ```bash
   open RedPill.xcodeproj
   ```

3. Select the **RedPill** scheme and build (`Cmd+B`).

4. The built `.saver` bundle will appear in `build/Release/Red Pill.saver`.

### Or build from the command line:

```bash
xcodebuild -project RedPill.xcodeproj -scheme RedPill -configuration Release build
```

## Installation

1. Locate the built `Red Pill.saver` file (in `build/Release/`).
2. Double-click it to open System Settings → Screen Saver.
3. Alternatively, copy it manually:
   ```bash
   cp "build/Release/Red Pill.saver" ~/Library/Screen\ Savers/
   ```
4. Open **System Settings → Screen Saver** and select **Red Pill**.

## Preferences

The screensaver includes a configuration sheet with the following options:

| Option | Description | Default |
|--------|-------------|---------|
| Strips | Maximum number of falling glyph strips | 50 |
| Velocity | Speed at which strips drift toward the viewer | 40 |
| Depth | How far away strips start | 200 |
| Cycling | Color cycling speed | 5 |
| Falling | Rate at which cycling colors fall | 2 |
| Cursor | Speed of the cursor fall | 10 |
| Fog | Fog density (0 = off) | 15 |
| Top Start | Start strips at the top of the screen | Yes |
| Main Only | Run on main screen only | No |

## Easter Egg

There is a hidden "spoon mode" that appears randomly in the preferences. If you find it,
remember: *There is no spoon.* 🥄

## Localization

The screensaver ships with English and Japanese localizations.

## License

Red Pill is free software; you can redistribute it and/or modify it under the terms of
the **GNU General Public License v3** as published by the Free Software Foundation.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY.

Please note that Apple's terms and conditions on the App Store prohibit distribution of
GPL-licensed software.

## Credits

- Original author: **mathew** <meta@pobox.com> — [lpar/RedPill](https://github.com/lpar/RedPill)
- ARC migration and 64-bit build: **Markus Moeller** (MacMark)
- Fork maintenance & CI: **DjManny**
