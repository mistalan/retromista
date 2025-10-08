# Emulator Setup Guide

This guide covers setting up emulators for classic platforms: C64 (WinVICE), Amiga (WinUAE), and Arcade (MAME).

## WinVICE - Commodore 64 Emulator

### Installation

**Windows:**
1. Download WinVICE from [https://vice-emu.sourceforge.io/](https://vice-emu.sourceforge.io/)
2. Extract the archive to a folder (e.g., `C:\VICE`)
3. Run `x64sc.exe` for accurate C64 emulation

**Linux:**
```bash
sudo apt-get install vice  # Ubuntu/Debian
sudo dnf install vice      # Fedora
```

**macOS:**
```bash
brew install vice
```

### Getting Started with C64 Development

1. **Choose a development tool:**
   - **CBM prg Studio** (Windows only) - IDE for BASIC/Assembly
   - **VICE built-in monitor** - For assembly debugging
   - **CC65** - C compiler for C64

2. **Your first program:**
   - Create a simple BASIC program
   - Save as `.prg` file
   - Load in VICE with `File > Attach Disk Image`

### Recommended Resources
- [C64 Programming Tutorials](https://www.c64-wiki.com/wiki/Programming)
- [CBM prg Studio Download](https://www.ajordison.co.uk/)
- [CC65 Compiler](https://cc65.github.io/)

## WinUAE - Amiga Emulator

### Installation

**Windows:**
1. Download WinUAE from [https://www.winuae.net/](https://www.winuae.net/)
2. Install the application
3. Download Kickstart ROMs (you must own original Amiga)

**Linux (UAE):**
```bash
sudo apt-get install fs-uae  # Ubuntu/Debian
```

**macOS:**
Use FS-UAE from [https://fs-uae.net/](https://fs-uae.net/)

### Getting Started with Amiga Development

1. **Choose a development tool:**
   - **AMOS** - BASIC-like language for games
   - **Blitz Basic** - Fast BASIC compiler
   - **Assembler** - For professional games

2. **Setup:**
   - Configure Workbench disk
   - Set up hard drive directory
   - Install development tools in emulator

### Recommended Resources
- [Amiga Assembly Tutorial](http://www.chebe.com/amiga-assembly/)
- [AMOS Programming Guide](http://amosfactory.org/)

## MAME - Arcade Emulator

### Installation

**Windows:**
1. Download MAME from [https://www.mamedev.org/](https://www.mamedev.org/)
2. Extract to a folder (e.g., `C:\MAME`)
3. Place ROM files in `roms` subdirectory

**Linux:**
```bash
sudo apt-get install mame  # Ubuntu/Debian
```

**macOS:**
```bash
brew install mame
```

### Development Notes

MAME is primarily for playing and studying arcade games. For creating arcade-style games:
1. Study existing ROM behavior
2. Use modern tools to recreate gameplay
3. Reference MAME source code for hardware details

### Recommended Resources
- [MAME Documentation](https://docs.mamedev.org/)
- [Arcade Game Programming Guide](https://github.com/mamedev/mame)

## Quick Reference

| Platform | Emulator | Best For | Difficulty |
|----------|----------|----------|------------|
| C64 | WinVICE | Learning basics | Beginner |
| Amiga | WinUAE | Advanced graphics | Intermediate |
| Arcade | MAME | Study & reference | Advanced |

## Next Steps

1. Install your chosen emulator
2. Follow the platform-specific tutorial
3. Try example projects in `/examples` folder
4. Join the development community

## Legal Notice

⚠️ **Important:** Only use ROMs and Kickstart files that you legally own. Downloading copyrighted material without permission is illegal.
