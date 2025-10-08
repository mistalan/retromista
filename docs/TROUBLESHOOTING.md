# Troubleshooting Guide

Common issues and solutions for RetroMista development.

## Table of Contents
- [Unity Issues](#unity-issues)
- [Emulator Issues](#emulator-issues)
- [Asset Creation Issues](#asset-creation-issues)
- [Audio Issues](#audio-issues)
- [Build Issues](#build-issues)
- [Performance Issues](#performance-issues)

## Unity Issues

### Unity Won't Start

**Problem:** Unity Hub opens but Unity Editor won't start

**Solutions:**
1. Check system requirements (8GB RAM recommended)
2. Update graphics drivers
3. Try different Unity version (LTS recommended)
4. Run as administrator (Windows)
5. Check antivirus isn't blocking

### Sprites Look Blurry

**Problem:** Pixel art looks blurry/fuzzy

**Solutions:**
1. Select sprite in Project window
2. In Inspector:
   - Filter Mode: **Point (no filter)**
   - Compression: **None**
   - Click Apply
3. Main Camera:
   - Add Pixel Perfect Camera component
   - Enable Pixel Snapping

### Player Falls Through Floor

**Problem:** Player character falls through platforms

**Solutions:**
1. Check both have Collider2D components
2. Player needs Rigidbody2D
3. Set Collision Detection to "Continuous"
4. Check layers aren't set to ignore collision
5. Verify collider sizes match sprites

### Physics Acting Weird

**Problem:** Movement feels floaty or too fast

**Solutions:**
1. Rigidbody2D settings:
   - Gravity Scale: Try 2-3 for platformers
   - Linear Drag: 0 for platformers
   - Mass: Usually 1 is fine
2. Use FixedUpdate() for physics code
3. Time.deltaTime for frame-independent movement

### Build Fails

**Problem:** Build errors or crashes

**Solutions:**
1. File → Build Settings → Add current scene
2. Check all referenced assets exist
3. Remove unused assets
4. Try different build platform
5. Check Console for specific errors

### Scripts Won't Compile

**Problem:** Red errors in Console

**Solutions:**
1. Read error message carefully
2. Check for typos in variable/function names
3. Ensure using correct Unity namespaces
4. Restart Unity if changes not detected
5. Delete Library folder and reopen project

## Emulator Issues

### WinVICE Issues

**Problem:** VICE won't start or crashes

**Solutions:**
1. Download latest stable version
2. Extract to folder without spaces in path
3. Run x64sc.exe (accurate C64 emulation)
4. Check Windows compatibility mode
5. Disable Windows Defender Real-time scanning for VICE folder

**Problem:** Can't load programs

**Solutions:**
1. File → Autostart Disk/Tape Image
2. Or manually:
   - LOAD "FILENAME",8,1
   - RUN
3. Check file is .prg, .d64, or .tap format
4. Try dragging file onto VICE window

**Problem:** Keyboard not working correctly

**Solutions:**
1. Options → Keyboard Settings
2. Try different keyboard mapping
3. Use symbolic mapping for modern keyboards
4. Check Joystick settings aren't capturing keys

### WinUAE Issues

**Problem:** No Kickstart ROM

**Solutions:**
1. You need legal Kickstart ROM
2. Must own original Amiga
3. Place in WinUAE/ROMs folder
4. Select in Configuration → ROM
5. Kickstart 1.3 or 3.1 recommended

**Problem:** Slow performance

**Solutions:**
1. Settings → CPU:
   - Set to 68020 or higher
   - Increase CPU speed to "max"
2. Chipset → Fast copper
3. Enable JIT compilation
4. Disable unnecessary accuracy options

**Problem:** Wrong display resolution

**Solutions:**
1. Settings → Display
2. Resolution: Try 640x512
3. Fullscreen: Try windowed mode first
4. Check "RTG" for high-res modes

### MAME Issues

**Problem:** ROM not found

**Solutions:**
1. Check ROM file is in roms/ folder
2. ROM must match MAME version
3. Use exact ROM name from MAME
4. Some games need parent ROMs
5. Verify ROM with `mame -verifyroms gamename`

**Problem:** Controls not working

**Solutions:**
1. Tab → Input (general)
2. Tab → Input (this game)
3. Map controls to keyboard/gamepad
4. Check default.cfg for conflicts

## Asset Creation Issues

### Aseprite Issues

**Problem:** Aseprite won't install/run

**Solutions:**
1. Windows: Try installer version
2. Linux: Use AppImage or compile from source
3. Check system requirements
4. Alternative: Use LibreSprite (free)

**Problem:** Export animation not working

**Solutions:**
1. File → Export Sprite Sheet
2. Choose "Array" layout
3. Set output format (PNG)
4. Check "Trim Cels" is off for Unity

### Piskel Issues

**Problem:** Can't save work

**Solutions:**
1. Browser may be blocking downloads
2. Allow pop-ups for piskelapp.com
3. Export as PNG regularly
4. Save project as .piskel file
5. Use desktop version if browser fails

**Problem:** Import to Unity shows wrong colors

**Solutions:**
1. Export as PNG (not GIF)
2. Disable transparency if not needed
3. Check color mode is RGB
4. Unity import settings: Compression = None

## Audio Issues

### BeepBox Issues

**Problem:** Can't export audio

**Solutions:**
1. Use Export → WAV
2. Check browser allows downloads
3. Try different browser
4. Desktop version available for offline use

**Problem:** Music too long/large file

**Solutions:**
1. Shorter loops = smaller files
2. Use lower sample rate for export
3. 8-bar loops usually enough
4. Compress with Audacity if needed

### Unity Audio Issues

**Problem:** Sound not playing

**Solutions:**
1. Check Audio Source attached to GameObject
2. Assign audio clip in Inspector
3. Check volume > 0
4. Verify "Mute Audio" is off in Game view
5. Check Audio Mixer settings

**Problem:** Music cuts off

**Solutions:**
1. Audio Source settings:
   - Loop: ✓ (for music)
   - Play On Awake: ✓
2. Don't destroy music GameObject between scenes:
   ```csharp
   DontDestroyOnLoad(gameObject);
   ```

**Problem:** Crackling/popping sounds

**Solutions:**
1. Edit → Project Settings → Audio
2. Increase DSP Buffer Size
3. Check audio clip import settings:
   - Load Type: Streaming (music)
   - Load Type: Decompress On Load (SFX)

### Bfxr Issues

**Problem:** Exported sound quality poor

**Solutions:**
1. Use Sample Rate: 44100 Hz
2. Bit Depth: 16-bit
3. Export as WAV (not web format)
4. Don't over-compress in Bfxr

## Build Issues

### Unity Build Issues

**Problem:** Build size too large

**Solutions:**
1. Remove unused assets
2. Compress textures (where appropriate)
3. Use Asset Bundles for large assets
4. WebGL: Enable compression
5. Strip engine code in Player Settings

**Problem:** WebGL build won't run

**Solutions:**
1. Must host on web server (not open locally)
2. Use Unity's Build and Run
3. Or upload to itch.io for testing
4. Check browser console for errors
5. Enable WebGL 2.0 in build settings

**Problem:** Build crashes on startup

**Solutions:**
1. Check all scenes added to build
2. Verify all assets present
3. Check for platform-specific issues
4. Test in editor first
5. Review Player.log file for errors

### C64 Build Issues

**Problem:** Program won't run on C64

**Solutions:**
1. Check .prg file created correctly
2. Verify memory usage < 64KB
3. Test in VICE before real hardware
4. Check for compatibility issues
5. Save in correct format for loader

## Performance Issues

### Unity Performance

**Problem:** Game runs slowly

**Solutions:**
1. Profile with Window → Analysis → Profiler
2. Reduce draw calls:
   - Use sprite atlases
   - Batch sprites
3. Optimize scripts:
   - Cache GetComponent calls
   - Use object pooling
   - Avoid FindObjectOfType in Update
4. Reduce particle effects
5. Use 2D Physics, not 3D

**Problem:** Build slower than editor

**Solutions:**
1. Development Build increases size
2. Don't enable Deep Profiling in builds
3. Strip debug symbols
4. Use IL2CPP for better performance

### C64 Performance

**Problem:** Game too slow in BASIC

**Solutions:**
1. Minimize PRINT statements
2. Use POKE instead of PRINT for graphics
3. Move to Assembly for speed
4. Optimize loops (fewer calculations)
5. Precalculate values where possible

**Problem:** Assembly still slow

**Solutions:**
1. Reduce sprite overdraw
2. Use hardware sprites instead of software
3. Optimize inner loops
4. Use lookup tables
5. Profile with VICE monitor

## General Issues

### Getting Stuck on Tutorial

**Problem:** Tutorial steps don't work

**Solutions:**
1. Ensure Unity/tools version matches
2. Re-read carefully (easy to miss steps)
3. Check for typos in code
4. Compare with example projects
5. Ask in GitHub Discussions

### Can't Find Files/Assets

**Problem:** Downloaded assets not visible

**Solutions:**
1. Unity: Refresh asset database (Ctrl+R)
2. Check correct import format
3. Verify file in correct folder
4. Check .meta files exist
5. Reimport asset

### Out of Memory

**Problem:** Tools crash with memory error

**Solutions:**
1. Close other applications
2. Reduce asset sizes
3. Use 64-bit versions of tools
4. Increase virtual memory (Windows)
5. Upgrade RAM if consistently low

## Still Having Issues?

### Before Asking for Help

1. ✅ Check this troubleshooting guide
2. ✅ Read error messages carefully
3. ✅ Search Google for error text
4. ✅ Check tool-specific documentation
5. ✅ Try minimal reproduction

### Where to Get Help

1. **GitHub Discussions:** [Ask here](https://github.com/mistalan/retromista/discussions)
2. **GitHub Issues:** [Report bugs](https://github.com/mistalan/retromista/issues)
3. **Unity Forums:** For Unity-specific issues
4. **Lemon64:** For C64 issues
5. **Stack Overflow:** For programming questions

### When Asking for Help

Include:
- Clear description of problem
- What you've tried
- Error messages (full text)
- System info (OS, Unity version, etc.)
- Minimal code example
- Screenshots if relevant

### Emergency Solutions

**Nuclear Options (when all else fails):**

**Unity:**
1. Delete Library folder → Reopen project
2. Reimport all assets
3. Create new project → Import assets
4. Restart computer

**Emulators:**
1. Delete configuration files
2. Reinstall emulator
3. Try different emulator version

**General:**
1. Check file permissions
2. Disable antivirus temporarily
3. Update all drivers
4. Check disk space

---

**This guide is continuously updated. Submit issues or suggest improvements on GitHub!**
