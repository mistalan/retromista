# Example Projects

Ready-to-use example projects to learn from and build upon.

## Available Examples

### 1. Pong Clone (Beginner)
**Platform:** Unity, C64 BASIC
**Difficulty:** ⭐ Easy
**What you'll learn:**
- Basic game loop
- Collision detection
- Score tracking
- Player input

**Files:**
- `/examples/pong-unity/` - Modern Unity version
- `/examples/pong-c64/` - C64 BASIC version

### 2. Breakout / Arkanoid (Beginner)
**Platform:** Unity
**Difficulty:** ⭐⭐ Easy-Medium
**What you'll learn:**
- Brick breaking mechanics
- Power-ups
- Level design
- Ball physics

**Files:**
- `/examples/breakout-unity/`

### 3. Space Invaders Style (Intermediate)
**Platform:** Unity, Godot
**Difficulty:** ⭐⭐⭐ Medium
**What you'll learn:**
- Enemy patterns
- Shooting mechanics
- Wave systems
- Sprite management

**Files:**
- `/examples/space-invaders-unity/`
- `/examples/space-invaders-godot/`

### 4. Platformer Basics (Intermediate)
**Platform:** Unity
**Difficulty:** ⭐⭐⭐ Medium
**What you'll learn:**
- Character movement
- Jumping mechanics
- Collision layers
- Level design

**Files:**
- `/examples/platformer-unity/`

### 5. Maze Game (Pac-Man Style)
**Platform:** C64 Assembly, Unity
**Difficulty:** ⭐⭐⭐⭐ Advanced
**What you'll learn:**
- Pathfinding
- Ghost AI
- Tile-based movement
- Pellet collection

**Files:**
- `/examples/maze-c64-asm/`
- `/examples/maze-unity/`

## How to Use These Examples

### Unity Projects

1. **Open in Unity:**
   ```bash
   # Clone the repository
   git clone https://github.com/mistalan/retromista.git
   cd retromista/examples/[project-name]
   ```

2. **Open in Unity Hub:**
   - Add project from disk
   - Select the project folder
   - Open with Unity 2022.3 LTS

3. **Study the code:**
   - Read README.md in project folder
   - Check commented scripts
   - Experiment with values

### C64 Projects

1. **Load in VICE:**
   - Download .prg file
   - File → Autostart Disk/Tape Image
   - Or type: `LOAD "GAME",8,1` then `RUN`

2. **View source:**
   - .bas files are BASIC listings
   - .asm files are Assembly source
   - Import in CBM prg Studio

### Godot Projects

1. **Open in Godot:**
   - Download Godot 4.x
   - Project Manager → Import
   - Select project.godot file

## Example Project Structure

Each example includes:

```
/example-name/
  ├── README.md              # Project description
  ├── SETUP.md              # How to run
  ├── TUTORIAL.md           # Step-by-step guide
  ├── /src                  # Source code
  ├── /assets               # Graphics, audio
  └── /docs                 # Additional documentation
```

## Learning Path

**Complete Beginner:**
1. Start with Pong (Unity or C64)
2. Try Breakout (Unity)
3. Build your own variation

**Some Experience:**
1. Study Space Invaders
2. Create Platformer
3. Add your own features

**Advanced:**
1. Maze game with AI
2. Combine multiple examples
3. Create original game

## Modifying Examples

### Tips for Customization

1. **Change visuals:**
   - Replace sprites with your own
   - Modify colors
   - Add particle effects

2. **Adjust gameplay:**
   - Change speed values
   - Modify difficulty
   - Add power-ups

3. **Add features:**
   - High score system
   - Sound effects
   - Multiple levels

4. **Learn from code:**
   - Add comments explaining what you learn
   - Refactor to your style
   - Improve efficiency

## Contributing Examples

Want to add your own example?

1. Fork the repository
2. Create your example in `/examples/your-game/`
3. Include:
   - README.md with description
   - Well-commented code
   - Assets (or links)
   - Tutorial (optional)
4. Submit pull request

**Requirements for examples:**
- Must run without errors
- Code should be commented
- Should teach specific concept
- Include learning objectives

## Example Comparisons

| Example | Unity | Godot | C64 | Complexity | Time to Complete |
|---------|-------|-------|-----|------------|------------------|
| Pong | ✅ | ❌ | ✅ | Low | 1-2 hours |
| Breakout | ✅ | ❌ | ❌ | Low-Med | 2-3 hours |
| Space Invaders | ✅ | ✅ | ❌ | Medium | 3-4 hours |
| Platformer | ✅ | ❌ | ❌ | Medium | 4-6 hours |
| Maze Game | ✅ | ❌ | ✅ | High | 6-8 hours |

## Additional Resources

### Video Tutorials
- Each example has video walkthrough (when available)
- Check project README for links

### Community
- Share your modifications
- Ask questions in GitHub Discussions
- Show off your games!

### Challenges
- Try to recreate without looking at code
- Combine elements from different examples
- Create new game from learned concepts

## Next Steps

1. Choose an example matching your skill level
2. Open and run it
3. Study the code
4. Modify and experiment
5. Build something new!

**Remember:** The best way to learn is by doing! Start with simple examples and gradually increase complexity.
