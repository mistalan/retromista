# Asset Generation Guide

Creating graphics, sprites, and visual assets for retro games without being a designer.

## Overview

Don't worry if you're not a designer! There are many tools and techniques to create retro game assets easily.

## Tools for Non-Designers

### Pixel Art Tools (Recommended)

#### 1. Aseprite (Best Overall - $20)
- **Website:** [https://www.aseprite.org/](https://www.aseprite.org/)
- **Best for:** Sprites, animations, pixel art
- **Why it's good:** Designed specifically for pixel art, very intuitive
- **Free alternative:** Compile from source (free on GitHub)

#### 2. Piskel (Free Online Tool)
- **Website:** [https://www.piskelapp.com/](https://www.piskelapp.com/)
- **Best for:** Quick pixel art, browser-based
- **Why it's good:** No installation needed, easy to use
- **Perfect for:** Beginners

#### 3. LibreSprite (Free, Open Source)
- **Website:** [https://libresprite.github.io/](https://libresprite.github.io/)
- **Best for:** Free alternative to Aseprite
- **Why it's good:** Fork of old Aseprite, feature-rich

#### 4. GIMP (Free, Advanced)
- **Website:** [https://www.gimp.org/](https://www.gimp.org/)
- **Best for:** Advanced editing, backgrounds
- **Setup for pixel art:** Disable anti-aliasing, use pencil tool

### AI-Assisted Asset Generation

#### 1. Stable Diffusion (Free, Local)
- Generate concept art and backgrounds
- Use ControlNet for pixel art style
- Requires some technical setup

#### 2. DALL-E / Midjourney
- Quick concept generation
- Can generate retro-style inspiration
- May require subscription

⚠️ **Note:** Always check licensing for commercial use with AI tools

## Asset Creation Workflows

### Workflow 1: Start with Templates (Easiest)

1. **Find free asset packs:**
   - [OpenGameArt.org](https://opengameart.org/)
   - [itch.io Free Assets](https://itch.io/game-assets/free)
   - [Kenney.nl](https://www.kenney.nl/assets) - Excellent free assets

2. **Modify existing assets:**
   - Change colors in Aseprite/Piskel
   - Combine different pieces
   - Add your own touches

3. **Learn by copying:**
   - Recreate simple sprites
   - Understand pixel art principles
   - Build your skills gradually

### Workflow 2: Create from Scratch (Learning)

1. **Start with simple shapes:**
   - 8x8 or 16x16 pixel sprites
   - Use limited color palette (4-8 colors)
   - Focus on silhouette first

2. **Follow tutorials:**
   - [Pixel Art Tutorial by Pedro Medeiros](https://blog.studiominiboss.com/pixelart)
   - [Aseprite Tutorials](https://www.youtube.com/c/MortMort)
   - Practice daily with small sprites

3. **Use color palettes:**
   - [Lospec Palette List](https://lospec.com/palette-list)
   - Pick retro palettes (C64, CGA, etc.)
   - Stick to palette for consistency

### Workflow 3: Procedural Generation (Advanced)

For backgrounds and tilesets:
- **Tiled Map Editor:** [https://www.mapeditor.org/](https://www.mapeditor.org/)
- **Texture generators:** Generate seamless patterns
- **Noise generators:** For natural-looking backgrounds

## Quick Start Guide

### Your First Sprite (15 minutes)

1. **Open Piskel or Aseprite**
2. **Create 16x16 canvas**
3. **Choose 4 colors from a C64 palette**
4. **Draw a simple character:**
   - 2 pixels for eyes
   - Simple body shape
   - Basic legs/feet
5. **Save as PNG**

### Creating Animations

1. **Start with idle animation:**
   - 2-4 frames is enough
   - Simple bobbing motion
2. **Walk cycle:**
   - 4-6 frames minimum
   - Keep it simple
3. **Use onion skinning** (available in all pixel art tools)

## Retro Platform Limitations (For Authenticity)

### Commodore 64
- **Resolution:** 320x200 pixels (or 160x200)
- **Colors:** 16 colors total
- **Sprites:** 24x21 pixels, 1-3 colors per sprite
- **Screen:** 8x8 pixel character blocks

### Amiga
- **Resolution:** 320x200 up to 640x512
- **Colors:** 32 colors on screen (4096 total)
- **Sprites:** Hardware sprites available
- **More flexible than C64**

### Arcade
- **Varies by system**
- **Generally:** 256x224 or 256x240
- **Colors:** Usually 256+ colors
- **Larger sprites allowed**

## Asset Organization

```
/assets
  /sprites
    /characters
      player.png
      enemy1.png
    /items
      coin.png
      powerup.png
  /backgrounds
    level1_bg.png
  /tilesets
    platform_tiles.png
  /ui
    font.png
    buttons.png
```

## Free Asset Resources

### Sprite Packs
- **Kenney Assets:** High-quality, consistent style
- **OpenGameArt:** Community-driven
- **itch.io:** Many free/pay-what-you-want packs

### Fonts
- **Google Fonts:** Free, open source
- **DaFont - Pixel Section:** Free pixel fonts
- **Retro Font Pack:** In `/assets/fonts` directory

### Color Palettes
- **Lospec:** Huge collection of retro palettes
- **C64 Palette:** Authentic 16 colors
- **Amiga Palettes:** Various 32-color sets

## Tips for Non-Designers

1. **Start small:** 8x8 or 16x16 sprites
2. **Use references:** Look at classic games
3. **Limit colors:** Forces good design
4. **Iterate:** First version won't be perfect
5. **Get feedback:** Share with community
6. **Practice daily:** Even 15 minutes helps
7. **Don't compare:** Your art is unique

## Next Steps

1. Install Piskel or Aseprite
2. Follow a basic pixel art tutorial
3. Create your first character sprite
4. Try the [First Game Tutorial](../tutorials/modern-first-game.md)
5. Experiment and have fun!

## Additional Resources

- [Pixel Art Tutorial by Saint11](https://saint11.org/blog/pixel-art-tutorials/)
- [r/PixelArt Community](https://reddit.com/r/PixelArt)
- [Aseprite Community](https://community.aseprite.org/)
- [Game Art 2D Tutorials](https://www.gameart2d.com/freebies.html)
