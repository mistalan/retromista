# Frequently Asked Questions (FAQ)

## General Questions

### What is RetroMista?
RetroMista is a comprehensive framework for building retro game ports from classic platforms (C64, Amiga, Arcade) to modern systems. It includes guides, tools, and examples for both emulator-based development and modern remakes.

### Do I need programming experience?
No! We have paths for complete beginners. Start with our visual tools (Unity) and beginner tutorials. Basic programming knowledge helps, but you can learn as you go.

### Which path should I choose?

**Choose Emulator Development if you:**
- Want to learn how classic platforms worked
- Enjoy programming challenges and limitations
- Want authentic retro experience
- Are interested in computer history

**Choose Modern Development if you:**
- Want to create games for modern audiences
- Need cross-platform distribution
- Prefer modern tools and workflows
- Want to publish on Steam/itch.io

### How long until I can make a game?
- **Simple game (Pong):** 2-4 hours with Unity
- **Medium game (Space Invaders):** 1-2 days
- **Complex game (Platformer):** 1-2 weeks
- **C64 game:** 1-2 weeks learning + development time

## Technical Questions

### What platforms are supported?

**Development platforms:**
- Windows (all tools supported)
- macOS (Unity, Godot, VICE)
- Linux (Unity, Godot, VICE, UAE)

**Target platforms:**
- C64 (via emulator or real hardware)
- Amiga (via emulator or real hardware)
- Modern PC (Windows, Mac, Linux)
- Web (via WebGL)
- Mobile (with Unity/Godot)

### Do I need expensive software?
No! Free options for everything:
- **Game Engine:** Unity (free), Godot (free)
- **Graphics:** Piskel (free), GIMP (free)
- **Music:** BeepBox (free), FamiStudio (free)
- **Sound FX:** Bfxr (free)
- **Emulators:** VICE, WinUAE (free)

### What computer specs do I need?

**For Modern Development:**
- CPU: Dual-core 2GHz+
- RAM: 4GB+ (8GB recommended)
- GPU: Integrated graphics OK
- Storage: 10GB+ free space

**For Emulator Development:**
- CPU: Any modern processor
- RAM: 2GB+
- GPU: Not needed
- Storage: 1GB+

## Asset Creation Questions

### I can't draw. Can I still make games?
Yes! Several options:
1. **Use free assets:** Kenney.nl, OpenGameArt
2. **Simple shapes:** Squares and circles work for retro
3. **AI generation:** Use Stable Diffusion for inspiration
4. **Modify existing:** Change colors and combine parts
5. **Procedural:** Generate assets programmatically

See [Asset Guide](../assets/README.md) for details.

### How do I create pixel art?
1. Start with Piskel (browser-based, free)
2. Use small sizes (8x8, 16x16)
3. Limit colors (4-8 colors)
4. Focus on silhouette first
5. Practice with simple shapes

Full tutorial in [Asset Guide](../assets/README.md).

### Can I use AI to create assets?
Yes, but:
- ✅ Use for inspiration and concepts
- ✅ Modify AI output significantly
- ⚠️ Check licensing for commercial use
- ⚠️ Be transparent about AI use
- ❌ Don't use copyrighted training material

### I'm not a musician. How do I make music?
1. **BeepBox:** Click squares = instant music
2. **Randomize:** Bfxr creates sounds instantly
3. **Free music:** Incompetech, OpenGameArt
4. **Learn basics:** We provide simple music theory
5. **Samples:** Use and modify existing chiptunes

See [Audio Guide](../audio/README.md).

## Platform-Specific Questions

### C64 Development

**Do I need real C64 hardware?**
No! WinVICE emulator works perfectly. But real hardware is more fun if you have it.

**What language should I use?**
- **BASIC:** Easy to learn, good for simple games
- **Assembly:** Required for action games, harder to learn
- **C (CC65):** Good middle ground

**Where do I get C64 ROMs?**
You need to own original C64 for legal ROM use. VICE includes some open-source ROMs.

### Unity Development

**Unity or Godot?**
- **Unity:** More tutorials, larger community, industry standard
- **Godot:** Fully free, open source, lighter weight
- Both are excellent - we recommend Unity for beginners

**Do I need Unity Pro?**
No! Unity Personal (free) is perfect for learning and indie development.

**Can I make 2D games in Unity?**
Yes! Unity has excellent 2D support. Use the 2D template when creating projects.

### Amiga Development

**Is Amiga development harder than C64?**
Yes, more complex hardware, but also more capable. Start with AMOS BASIC for easier learning.

**Do I need Kickstart ROMs?**
Yes, for WinUAE. You must own original Amiga to use legally.

## Legal Questions

### Can I sell games I create?
Yes! If you:
- ✅ Create original code
- ✅ Use your own assets (or properly licensed)
- ✅ Don't use copyrighted material
- ✅ Follow platform terms of service

### Can I recreate classic games?
You can recreate game *mechanics*, but:
- ✅ Game mechanics can't be copyrighted
- ✅ Study and learn from classics
- ❌ Don't copy code
- ❌ Don't use original assets
- ❌ Don't use same names/trademarks

### What about fan games?
Fan games exist in legal gray area:
- ⚠️ Can receive cease & desist
- ⚠️ Can't sell without permission
- ✅ Better to create "inspired by" originals
- ✅ Use own IP and assets

### Can I use ROMs from the internet?
No! Downloading copyrighted ROMs is illegal unless:
- ✅ You own the original game
- ✅ ROM is homebrew/free
- ✅ ROM is abandonware (debatable)

## Workflow Questions

### What's the fastest way to make a game?
1. Use Unity or Godot
2. Start with free asset packs
3. Use BeepBox for music
4. Follow our [First Game Tutorial](../tutorials/modern-first-game.md)
5. Total time: 2-4 hours

### Should I start with emulators or modern dev?
**Modern development** is easier to start:
- Faster results
- Better tools
- Easier debugging
- More resources

**Emulator development** for purists:
- Learn retro computing
- Authentic experience
- More challenging
- Historical interest

### How do I publish my game?
**Free options:**
- **itch.io:** Upload WebGL or executables
- **GitHub:** Open source your game
- **Newgrounds:** Share with retro community

**Commercial options:**
- **Steam:** Requires $100 fee + approval
- **itch.io:** Can set price
- **Your own website:** Full control

### Can I work on multiple platforms?
Yes! Many developers:
1. Prototype in Unity (fast)
2. Port to C64 (authentic)
3. Polish Unity version (commercial)

Or specialize in one platform.

## Learning Questions

### What should I learn first?
**Day 1:** Read Getting Started Guide
**Day 2:** Install tools (Unity or VICE)
**Day 3:** Complete first tutorial
**Week 1:** Build simple game (Pong)
**Week 2:** Add your own features
**Week 3:** Start original game

### Are there video tutorials?
Yes! We link to:
- Brackeys (Unity)
- GDQuest (Godot)
- 8-Bit Show and Tell (C64)
- Platform-specific tutorials

### How do I get help?
1. Check this FAQ
2. Read [Troubleshooting](TROUBLESHOOTING.md)
3. Search GitHub Issues
4. Ask in GitHub Discussions
5. Join Discord/Reddit communities

### What game should I make first?
Start simple:
1. **Pong:** Learn basics (2 hours)
2. **Breakout:** Add complexity (4 hours)
3. **Space Invaders:** Enemy patterns (8 hours)
4. **Your own idea:** Apply learnings

## Common Mistakes

### What should I avoid?

**Don't:**
- ❌ Start with complex 3D games
- ❌ Try to make perfect game first time
- ❌ Spend months on assets before coding
- ❌ Use copyrighted material
- ❌ Try to learn everything at once

**Do:**
- ✅ Start small and simple
- ✅ Finish small projects
- ✅ Iterate and improve
- ✅ Share early and often
- ✅ Learn one thing at a time

### How do I avoid getting stuck?

1. **Break down problems:** Smaller steps
2. **Google errors:** Someone solved it
3. **Ask for help:** Community is friendly
4. **Take breaks:** Fresh perspective helps
5. **Simplify:** Maybe it's too complex for now

## Community Questions

### How do I share my work?
- Post in GitHub Discussions
- Share on itch.io
- Tweet with #retrogamedev
- Post in r/gamedev or r/retrogaming
- Share source code on GitHub

### Can I contribute to RetroMista?
Yes! We welcome:
- New tutorials
- Example projects
- Bug fixes
- Documentation improvements
- Tool recommendations

See [CONTRIBUTING.md](../CONTRIBUTING.md)

### Where is the community?
- GitHub Discussions (here)
- r/gamedev (Reddit)
- r/retrogaming (Reddit)
- Lemon64 Forums (C64)
- English Amiga Board (Amiga)

## Still Have Questions?

- 📖 Check [Getting Started Guide](GETTING_STARTED.md)
- 🔧 See [Troubleshooting](TROUBLESHOOTING.md)
- 💬 Ask in [GitHub Discussions](https://github.com/mistalan/retromista/discussions)
- 🐛 Report bugs in [Issues](https://github.com/mistalan/retromista/issues)

---

**This FAQ is regularly updated. Suggest improvements via GitHub Issues!**
