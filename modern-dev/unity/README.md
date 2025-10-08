# Unity Setup Guide for Retro Game Development

Complete guide to setting up Unity for creating retro-style games.

## Installation

### Step 1: Install Unity Hub

1. Download Unity Hub from [https://unity.com/download](https://unity.com/download)
2. Install Unity Hub (it's a launcher for Unity versions)
3. Create a Unity account (free)

### Step 2: Install Unity Editor

1. Open Unity Hub
2. Go to "Installs" tab
3. Click "Install Editor"
4. Choose **Unity 2022.3 LTS** (Long Term Support)
5. Select modules:
   - ✅ Visual Studio (Windows) or Visual Studio for Mac
   - ✅ WebGL Build Support (for browser games)
   - ✅ Windows Build Support (if on Mac/Linux)
   - ✅ Documentation

### Step 3: Create Your First Project

1. Click "New Project" in Unity Hub
2. Choose template: **2D (Core)** or **2D (URP)**
   - Use "2D Core" for simplest retro games
3. Name your project (e.g., "MyFirstRetroGame")
4. Choose save location
5. Click "Create Project"

## Unity Interface Overview

When Unity opens, you'll see:
- **Scene View:** Where you build your game
- **Game View:** Preview of your game
- **Hierarchy:** List of objects in scene
- **Inspector:** Properties of selected object
- **Project:** Your assets and files
- **Console:** Errors and messages

## Setting Up for Pixel Perfect Retro Graphics

### 1. Install 2D Pixel Perfect Package

1. Go to `Window > Package Manager`
2. Click the `+` button
3. Select "Install package by name"
4. Enter: `com.unity.2d.pixel-perfect`
5. Click "Install"

### 2. Configure Pixel Perfect Camera

1. Select "Main Camera" in Hierarchy
2. Click "Add Component" in Inspector
3. Add "Pixel Perfect Camera"
4. Settings for retro look:
   - Assets Pixels Per Unit: 16
   - Reference Resolution: 320x180 (or 640x360)
   - Check "Upscale Render Texture"
   - Check "Pixel Snapping"

### 3. Import Settings for Pixel Art

For all pixel art sprites:
1. Select sprite in Project window
2. In Inspector:
   - Texture Type: Sprite (2D and UI)
   - Sprite Mode: Single (or Multiple for spritesheets)
   - Pixels Per Unit: 16 (match camera setting)
   - Filter Mode: **Point (no filter)**
   - Compression: None
   - Click "Apply"

## Project Structure

Organize your project:

```
Assets/
  ├── Scenes/
  │   ├── MainMenu.unity
  │   └── Level1.unity
  ├── Scripts/
  │   ├── PlayerController.cs
  │   └── GameManager.cs
  ├── Sprites/
  │   ├── Characters/
  │   └── Tiles/
  ├── Audio/
  │   ├── Music/
  │   └── SFX/
  └── Prefabs/
      └── Player.prefab
```

## Essential Packages for Retro Games

### 1. TextMeshPro (for pixel fonts)
- Built-in with Unity
- Better text rendering
- `Window > TextMeshPro > Import TMP Essential Resources`

### 2. Cinemachine (for camera control)
- `Window > Package Manager`
- Find "Cinemachine"
- Click "Install"

### 3. Input System (modern input handling)
- `Window > Package Manager`
- Find "Input System"
- Click "Install"

## Quick Example: Simple Player Movement

### 1. Create Player Sprite

1. Import a player sprite (16x16 pixels)
2. Set import settings as above (Point filter, PPU=16)
3. Drag sprite to Scene
4. Rename to "Player"

### 2. Add Rigidbody2D

1. Select Player
2. Add Component > Physics 2D > Rigidbody 2D
3. Set:
   - Gravity Scale: 3
   - Collision Detection: Continuous

### 3. Add Collider

1. Add Component > Physics 2D > Box Collider 2D
2. Adjust size to fit sprite

### 4. Create Movement Script

1. Right-click in Project > Create > C# Script
2. Name it "PlayerController"
3. Double-click to open in Visual Studio
4. Replace with this code:

```csharp
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    public float speed = 5f;
    public float jumpForce = 10f;
    
    private Rigidbody2D rb;
    private bool isGrounded;
    
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }
    
    void Update()
    {
        // Movement
        float moveInput = Input.GetAxis("Horizontal");
        rb.velocity = new Vector2(moveInput * speed, rb.velocity.y);
        
        // Jump
        if (Input.GetButtonDown("Jump") && isGrounded)
        {
            rb.velocity = new Vector2(rb.velocity.x, jumpForce);
        }
    }
    
    void OnCollisionEnter2D(Collision2D collision)
    {
        if (collision.gameObject.CompareTag("Ground"))
        {
            isGrounded = true;
        }
    }
    
    void OnCollisionExit2D(Collision2D collision)
    {
        if (collision.gameObject.CompareTag("Ground"))
        {
            isGrounded = false;
        }
    }
}
```

5. Drag script onto Player object

### 5. Create Ground

1. Create > 2D Object > Sprite > Square
2. Rename to "Ground"
3. Scale it: X=10, Y=1
4. Position below player
5. Add Component > Box Collider 2D
6. Set Tag to "Ground" (in Inspector, top dropdown)

### 6. Test Your Game

1. Click Play button ▶️
2. Use Arrow Keys to move
3. Press Space to jump

## Building Your Game

### For Windows/Mac/Linux

1. Go to `File > Build Settings`
2. Click "Add Open Scenes"
3. Select platform (PC, Mac & Linux Standalone)
4. Click "Build"
5. Choose save location
6. Run the executable!

### For WebGL (Browser)

1. Go to `File > Build Settings`
2. Select "WebGL"
3. Click "Switch Platform"
4. Click "Build"
5. Upload to itch.io or host yourself

## Useful Unity Shortcuts

- `Ctrl/Cmd + S`: Save
- `Ctrl/Cmd + P`: Play/Stop
- `F`: Focus on selected object
- `W/E/R`: Move/Rotate/Scale tools
- `V`: Vertex snap

## Common Issues & Solutions

### Sprite looks blurry
- Change Filter Mode to "Point (no filter)"
- Set Compression to "None"

### Player moves through walls
- Add Rigidbody2D to player
- Add Collider2D to both player and walls
- Check layers aren't set to ignore collision

### Pixel art doesn't align
- Enable Pixel Snapping in Pixel Perfect Camera
- Use PPU of 16 or 32 consistently
- Make sure sprite positions snap to grid

## Next Steps

1. Complete the [First Game Tutorial](../../tutorials/modern-first-game.md)
2. Watch [Brackeys Unity 2D Tutorial](https://www.youtube.com/watch?v=on9nwbZngyw)
3. Try creating a simple Pong or Breakout clone
4. Explore Unity Learn: [https://learn.unity.com/](https://learn.unity.com/)

## Additional Resources

- [Unity 2D Documentation](https://docs.unity3d.com/Manual/2D.html)
- [Unity Learn - 2D Game Kit](https://learn.unity.com/project/2d-game-kit)
- [Brackeys YouTube Channel](https://www.youtube.com/c/Brackeys)
- [Unity Retro Games Tutorial](https://learn.unity.com/search?k=%5B%22q%3Aretro%22%5D)

## Tips for Retro Games in Unity

1. **Use limited color palettes:** Create materials with specific colors
2. **Pixel perfect scaling:** Use Pixel Perfect Camera
3. **Retro fonts:** Import pixel fonts from Google Fonts
4. **Scanlines/CRT effect:** Use post-processing shaders
5. **Limited animations:** 2-4 frames is enough for retro feel
6. **Simple particles:** Use small sprites, not Unity's particle system
7. **Chiptune audio:** Import 8-bit music and SFX
