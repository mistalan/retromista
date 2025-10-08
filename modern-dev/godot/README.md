# Godot Setup Guide for Retro Game Development

Complete guide to setting up Godot Engine for creating retro-style games.

## Why Godot?

- **100% Free & Open Source:** No licensing fees, ever
- **Lightweight:** Small download, runs on older hardware
- **Great 2D Support:** Built for 2D games
- **No Programming Required:** Visual scripting option (GDScript is easy too)
- **Cross-Platform:** Export to desktop, mobile, web

## Installation

### Step 1: Download Godot

1. Visit [godotengine.org](https://godotengine.org/download)
2. Choose **Godot 4.x** (latest stable)
3. Select your platform:
   - **Windows:** Download .exe
   - **macOS:** Download .dmg or .zip
   - **Linux:** Download .AppImage or use package manager

### Step 2: Run Godot

**Windows:**
1. Extract ZIP (if downloaded ZIP)
2. Run `Godot_v4.x_win64.exe`
3. No installation needed!

**macOS:**
1. Open DMG or extract ZIP
2. Drag to Applications (optional)
3. Right-click → Open (first time only)

**Linux:**
```bash
# AppImage
chmod +x Godot_v4.x_linux.x86_64
./Godot_v4.x_linux.x86_64

# Or use package manager
sudo apt install godot  # Ubuntu/Debian
sudo dnf install godot  # Fedora
```

## Create Your First Project

### Step 1: Project Manager

1. Launch Godot
2. Click **"New Project"**
3. Fill in details:
   - **Project Name:** MyRetroGame
   - **Project Path:** Choose location
   - **Renderer:** Choose **Forward+** or **Mobile** (2D works with both)
4. Click **"Create & Edit"**

### Step 2: Understanding the Interface

When Godot opens:
- **FileSystem (left):** Your project files
- **Scene (center):** Visual editor
- **Inspector (right):** Properties
- **Bottom:** Output, debugger, animation

## Setting Up for Pixel Perfect Graphics

### Step 1: Project Settings

1. **Project → Project Settings**
2. **Display → Window:**
   - Viewport Width: `320`
   - Viewport Height: `180`
   - Window Width Override: `1280` (4x scale)
   - Window Height Override: `720` (4x scale)
   - Stretch Mode: `canvas_items`
   - Stretch Aspect: `keep`

### Step 2: Import Settings

For pixel art textures:
1. Select texture in FileSystem
2. In Import dock (next to Scene):
   - Filter: **Nearest**
   - Compress: **Lossless**
   - Click **"Reimport"**

### Step 3: Set Default Import

1. **Project → Project Settings**
2. **Rendering → Textures:**
   - Default Texture Filter: **Nearest**
3. All new textures will use pixel-perfect settings

## Your First Retro Game

### Create Player Character

1. **Scene → New Scene**
2. Choose **2D Scene**
3. Rename root node to "Player"
4. Add child nodes:
   - Click **"+"** on Player
   - Add **Sprite2D** (for graphics)
   - Add **Area2D** (for collision)
   - Add **CollisionShape2D** (child of Area2D)

### Add Sprite

1. Select **Sprite2D**
2. In Inspector:
   - Texture → Quick Load (or drag sprite)
3. Or use built-in icon:
   - Texture → Load
   - Navigate to `res://icon.svg`

### Add Movement Script

1. Select **Player** node
2. Click **"Attach Script"** button (scroll icon)
3. Keep defaults, click **"Create"**
4. Replace with:

```gdscript
extends CharacterBody2D

const SPEED = 300.0
const JUMP_VELOCITY = -400.0

func _physics_process(delta):
    # Add gravity
    if not is_on_floor():
        velocity += get_gravity() * delta
    
    # Handle jump
    if Input.is_action_just_pressed("ui_accept") and is_on_floor():
        velocity.y = JUMP_VELOCITY
    
    # Handle movement
    var direction = Input.get_axis("ui_left", "ui_right")
    if direction:
        velocity.x = direction * SPEED
    else:
        velocity.x = move_toward(velocity.x, 0, SPEED)
    
    move_and_slide()
```

5. Save: **File → Save** (Ctrl/Cmd+S)

### Create Ground

1. Click **"+"** on root (Scene panel)
2. Add **StaticBody2D**
3. Add **Sprite2D** as child (for visual)
4. Add **CollisionShape2D** as child
5. For CollisionShape2D:
   - Shape → New RectangleShape2D
   - Adjust size in editor

### Test Your Game

1. Press **F5** (or Play button ▶️)
2. Choose main scene when prompted
3. Use arrow keys to move
4. Press Space to jump

## Project Structure

Organize files in FileSystem:

```
res://
├── scenes/
│   ├── main.tscn
│   ├── player.tscn
│   └── levels/
├── scripts/
│   ├── player.gd
│   └── game_manager.gd
├── assets/
│   ├── sprites/
│   ├── audio/
│   └── fonts/
└── project.godot
```

## Essential Godot Concepts

### Nodes and Scenes

- **Nodes:** Building blocks (Sprite, Area2D, etc.)
- **Scenes:** Collection of nodes (reusable)
- **Scene Tree:** Hierarchy of nodes

### Signals (Events)

Connect events to functions:

```gdscript
# Connect in editor or code
$Area2D.body_entered.connect(_on_body_entered)

func _on_body_entered(body):
    print("Hit something!")
```

### Input Handling

```gdscript
# In _process() or _physics_process()
if Input.is_action_pressed("ui_left"):
    position.x -= speed * delta

# Or use get_axis
var direction = Input.get_axis("ui_left", "ui_right")
```

### Timers

```gdscript
# Create Timer node or in code
var timer = Timer.new()
timer.wait_time = 1.0
timer.one_shot = true
add_child(timer)
timer.start()
```

## Simple Complete Game Example

### Flappy Bird Style Game

**Player Script (player.gd):**
```gdscript
extends CharacterBody2D

const FLAP_FORCE = -300
const GRAVITY = 800

func _physics_process(delta):
    # Apply gravity
    velocity.y += GRAVITY * delta
    
    # Flap on input
    if Input.is_action_just_pressed("ui_accept"):
        velocity.y = FLAP_FORCE
    
    # Rotate based on velocity
    rotation = velocity.y / 500.0
    
    move_and_slide()

func _on_area_2d_body_entered(body):
    get_tree().reload_current_scene()
```

**Pipe Spawner Script:**
```gdscript
extends Node2D

var pipe_scene = preload("res://scenes/pipe.tscn")

func _ready():
    $Timer.start()

func _on_timer_timeout():
    var pipe = pipe_scene.instantiate()
    pipe.position = Vector2(500, randf_range(50, 250))
    add_child(pipe)
```

## Retro Effects

### CRT Shader

1. Add **ColorRect** covering screen
2. Attach shader:
   - Material → New ShaderMaterial
   - Shader → New Shader
   - Add scanline effect

### Pixel Art Camera

```gdscript
extends Camera2D

func _ready():
    # Snap camera to pixels
    position_smoothing_enabled = true
    position_smoothing_speed = 10.0
```

## Exporting Your Game

### Export to Windows

1. **Project → Export**
2. **Add → Windows Desktop**
3. Configure settings
4. **Export Project**
5. Choose save location

### Export to Web (HTML5)

1. **Project → Export**
2. **Add → Web**
3. Configure settings
4. **Export Project**
5. Upload to itch.io

### Export to Linux/Mac

1. **Project → Export**
2. **Add → Platform**
3. Configure and export

## Useful Godot Features

### Tilemap for Levels

1. Create **TileMap** node
2. Create **TileSet** resource
3. Draw levels visually
4. Auto-tiling support

### Animation Player

1. Add **AnimationPlayer**
2. Create animations
3. Control via code
4. Blend animations

### Particle Effects

1. Add **GPUParticles2D**
2. Configure in Inspector
3. Simple retro effects

## Common Issues

### Sprite is blurry
- Import settings → Filter: Nearest
- Project settings → Default filter: Nearest

### Input not working
- Check Input Map in Project Settings
- Verify action names match code

### Game runs slow
- Use Compatibility renderer for older hardware
- Reduce particle count
- Optimize draw calls

## Learning Resources

### Official Documentation
- [Godot Docs](https://docs.godotengine.org/)
- [Your First 2D Game](https://docs.godotengine.org/en/stable/getting_started/first_2d_game/)

### Video Tutorials
- [GDQuest](https://www.gdquest.com/) - Professional tutorials
- [Brackeys Godot](https://www.youtube.com/results?search_query=brackeys+godot)
- [HeartBeast](https://www.youtube.com/c/uheartbeast) - Game dev focus

### Communities
- [Godot Forums](https://godotengine.org/community)
- [r/godot](https://reddit.com/r/godot)
- [Godot Discord](https://discord.gg/godot)

## GDScript vs Visual Scripting

### GDScript (Recommended)
- Python-like syntax
- Easy to learn
- Full engine access
- Better performance

### Visual Scripting
- No code required
- Drag and drop
- Good for beginners
- Can mix with GDScript

## Next Steps

1. Complete [Your First 2D Game](https://docs.godotengine.org/en/stable/getting_started/first_2d_game/)
2. Build a simple Pong clone
3. Create a platformer
4. Try making Space Invaders
5. Design your own game!

## Godot vs Unity

| Feature | Godot | Unity |
|---------|-------|-------|
| Cost | Free | Free (with limits) |
| Size | ~50MB | ~3GB |
| 2D | Excellent | Good |
| Learning Curve | Easier | Moderate |
| Community | Growing | Huge |
| Jobs | Fewer | Many |

**Choose Godot if:**
- You want 100% free
- Making 2D games
- Prefer lightweight tools
- Want open source

**Choose Unity if:**
- Need huge asset store
- Want industry standard
- Making 3D games
- Need more tutorials

## Tips for Retro Games in Godot

1. **Use CanvasLayer** for UI (stays on screen)
2. **Keep it simple:** Focus on gameplay
3. **Low resolution:** 320x180 or 640x360
4. **Limited colors:** Create palette materials
5. **Pixel fonts:** Import .ttf pixel fonts
6. **Simple particles:** Small sprites work great
7. **Chiptune audio:** Import .wav or .ogg

## Conclusion

Godot is perfect for retro game development:
- ✅ Free and open source
- ✅ Excellent 2D support
- ✅ Easy to learn
- ✅ Great for pixel art
- ✅ Cross-platform export

Start creating your retro masterpiece today! 🎮
