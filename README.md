# LFC Vehicle Colour Editor
 
A lightweight desktop tool for reading and writing RGB colour values stored in `.col` binary files used by a racing simulation game. Supports both **Windows** and **Linux**.
 
---
 
## Features
 
- **Open / Reload / Save / Save As** — full file lifecycle for `.col` binary files
- **8 colour slots** — 4 Body slots and 4 Wheel slots, each independently editable
- **Live preview** — three colour swatches per slot (Base, Clamped, Source) update as you type
- **Clamp Factor slider** — linearly interpolates each channel toward the game-safe range `[10, 160]`
- **Auto Clamp** — automatically computes the minimum slider value that brings all channels into range
- **Reset button** — reverts a slot to the last saved state
- **Undo / Redo** — per-field undo stack in every hex input (`Ctrl+Z` / `Ctrl+Y`)
- **Uppercase enforcement** — hex inputs silently upper-case all typed and pasted characters
- **Out-of-range highlighting** — Clamped row turns orange in the RGB table when any channel is outside bounds
- **Status bar** — last action displayed at all times
- **Keyboard shortcuts** — full keyboard navigation without touching the menu
---
 
## Download & Run
 
No Python installation required. A pre-built executable is provided for both platforms.
 
### Windows
 
1. Download `LFC-VehicleColourEditor-win64.zip`.
2. Extract the archive to any folder (e.g. `Desktop`).
3. Double-click `LFC-VehicleColourEditor.exe` to launch.
> The executable is a single file. You can place it anywhere and delete it just as easily.
 
### Linux
 
1. Download `LFC-VehicleColourEditor-linux-x86_64.tar.gz`.
2. Extract the archive:
   ```bash
   tar -xzf LFC-VehicleColourEditor-linux-x86_64.tar.gz
   ```
3. Run the binary executable:
   ```bash
   ./LFC-VehicleColourEditor
   ```
 
> On most desktop distributions (Ubuntu, Mint, Fedora Workstation, etc.) this works out of the box. If the application does not start, the Tk system library may be missing — install it with one command:
> ```bash
> sudo apt install python3-tk        # Debian / Ubuntu / Mint
> sudo dnf install python3-tkinter   # Fedora / RHEL
> sudo pacman -S tk                  # Arch
> ```
 
---
 
## Keyboard Shortcuts
 
| Shortcut | Action |
|---|---|
| `Ctrl+O` | Open `.col` file |
| `Ctrl+R` | Reload from disk |
| `Ctrl+S` | Save |
| `Ctrl+E` | Save As |
| `Ctrl+Q` | Exit |
| `Ctrl+H` | About |
| `Ctrl+Z` | Undo (hex input) |
| `Ctrl+Y` | Redo (hex input) |
| `Ctrl+A` | Select all (hex input) |
| `Ctrl+V` | Paste (hex input, auto upper-cased) |
 
---
 
## Colour Clamping
 
The game engine rejects RGB channel values outside `[10, 160]`. The editor handles this with a **Clamp Factor** (`t`):
 
- At `t = 0.0` the original colour is written unchanged.  
- At `t = 1.0` every channel is fully remapped to the safe range.  
- **Auto Clamp** finds the smallest `t` (in 0.01 steps) at which all channels pass validation.
---
 
## License
 
Copyright © 2026 obdegirmenci. All rights reserved.
 
This software is proprietary. The compiled binary may be used freely for personal, non-commercial purposes. Reverse engineering, redistribution, modification, or commercial use of any kind is strictly prohibited without explicit written permission from the author.
 
