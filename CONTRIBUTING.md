# Contributing to RetroMista

Thank you for your interest in contributing to RetroMista! This document provides guidelines for contributing.

## Ways to Contribute

### 1. Documentation
- Improve existing guides
- Add new tutorials
- Fix typos and errors
- Translate documentation
- Add examples and clarifications

### 2. Example Projects
- Create example games
- Port classic games (legally)
- Add code examples
- Create video tutorials

### 3. Tools and Resources
- Recommend new tools
- Create utility scripts
- Share asset packs
- Contribute templates

### 4. Bug Reports
- Report issues
- Suggest improvements
- Test on different platforms

### 5. Code Contributions
- Fix bugs
- Add features
- Improve performance
- Refactor code

## Getting Started

### 1. Fork the Repository
```bash
# Click "Fork" on GitHub
# Clone your fork
git clone https://github.com/YOUR_USERNAME/retromista.git
cd retromista
```

### 2. Create a Branch
```bash
git checkout -b feature/your-feature-name
# or
git checkout -b fix/bug-description
```

### 3. Make Your Changes
- Follow existing code style
- Add documentation
- Test your changes
- Commit with clear messages

### 4. Submit Pull Request
- Push to your fork
- Create PR on GitHub
- Describe your changes
- Link related issues

## Contribution Guidelines

### Documentation Style

**Markdown formatting:**
- Use clear headings (H1 for title, H2 for sections)
- Include code blocks with language tags
- Add links to related resources
- Use tables for comparisons
- Include examples

**Writing style:**
- Write for beginners
- Use simple language
- Include step-by-step instructions
- Add screenshots when helpful
- Provide context and explanations

**Example:**
```markdown
## Installing Unity

1. **Download Unity Hub**
   - Visit [unity.com/download](https://unity.com/download)
   - Choose your platform
   - Run the installer

2. **Install Unity Editor**
   - Open Unity Hub
   - Click "Installs" → "Add"
   - Select Unity 2022.3 LTS
```

### Code Style

**Unity/C# code:**
```csharp
// Use clear variable names
public class PlayerController : MonoBehaviour
{
    // Group related variables
    [Header("Movement")]
    public float speed = 5f;
    public float jumpForce = 10f;
    
    // Cache components in Start
    private Rigidbody2D rb;
    
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }
    
    // Use meaningful method names
    void HandleMovement()
    {
        float moveInput = Input.GetAxis("Horizontal");
        rb.velocity = new Vector2(moveInput * speed, rb.velocity.y);
    }
}
```

**C64 BASIC code:**
```basic
10 REM === GAME TITLE ===
20 REM CLEAR SCREEN
30 PRINT CHR$(147)
40 REM MAIN GAME LOOP
50 GOSUB 1000
60 GOTO 40
```

**Comments:**
- Explain "why" not "what"
- Document complex logic
- Add section headers
- Include usage examples

### Example Projects

**Structure:**
```
/examples/your-project/
├── README.md           # Project description
├── SETUP.md           # How to run
├── TUTORIAL.md        # Step-by-step guide (optional)
├── /Assets            # Unity/Godot project
├── /src               # Source code
└── /docs              # Additional docs
```

**README.md template:**
```markdown
# Project Name

Brief description of the game.

## What You'll Learn
- Feature 1
- Feature 2
- Feature 3

## Requirements
- Unity 2022.3 LTS
- Basic C# knowledge

## How to Run
1. Open in Unity
2. Load MainScene
3. Press Play

## Controls
- Arrow keys: Move
- Space: Jump

## Credits
- Code: Your Name
- Assets: Source/License
```

### Asset Contributions

**For graphics:**
- Provide source files (.aseprite, .psd)
- Include export settings
- Add license information
- Credit original artists

**For audio:**
- Include project files (.ftm, .mmpz)
- Export in common formats (WAV, OGG)
- Document creation process
- Specify licensing

### License Requirements

All contributions must be compatible with GPL v3:
- ✅ GPL v3 compatible licenses
- ✅ Public Domain / CC0
- ✅ CC-BY (attribution)
- ❌ Proprietary licenses
- ❌ Copyrighted material

**Specify license in contributions:**
```markdown
## License
This example is released under GPL v3.
Assets from Kenney.nl (CC0).
```

## Pull Request Process

### 1. Before Submitting

- [ ] Test your changes
- [ ] Update documentation
- [ ] Follow style guidelines
- [ ] Check for conflicts
- [ ] Write clear commit messages

### 2. PR Description Template

```markdown
## Description
Brief description of changes.

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Documentation
- [ ] Example project

## Related Issues
Fixes #123

## Testing
How to test the changes.

## Screenshots
If applicable.

## Checklist
- [ ] Code follows style guidelines
- [ ] Documentation updated
- [ ] No breaking changes
- [ ] Tested on multiple platforms
```

### 3. Review Process

1. Maintainer reviews PR
2. Feedback provided
3. Make requested changes
4. PR approved and merged

## Code of Conduct

### Our Standards

**Positive behavior:**
- Be respectful and inclusive
- Welcome newcomers
- Accept constructive feedback
- Focus on what's best for community
- Show empathy

**Unacceptable behavior:**
- Harassment or discrimination
- Trolling or insulting comments
- Personal or political attacks
- Publishing private information
- Unprofessional conduct

### Enforcement

Violations may result in:
1. Warning
2. Temporary ban
3. Permanent ban

Report issues to: [GitHub Issues](https://github.com/mistalan/retromista/issues)

## Recognition

Contributors will be:
- Listed in CONTRIBUTORS.md
- Credited in relevant documentation
- Mentioned in release notes
- Acknowledged in the community

## Questions?

- 💬 Ask in [GitHub Discussions](https://github.com/mistalan/retromista/discussions)
- 📧 Contact maintainers via GitHub
- 📚 Read the [Documentation](docs/)

## Quick Links

- [Getting Started](docs/GETTING_STARTED.md)
- [FAQ](docs/FAQ.md)
- [Troubleshooting](docs/TROUBLESHOOTING.md)
- [Example Projects](examples/)

---

**Thank you for contributing to RetroMista!** 🎮

Your contributions help preserve retro gaming history and inspire new developers.
