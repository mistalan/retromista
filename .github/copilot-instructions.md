# Copilot Instructions for RetroMista

## Repository Overview

**RetroMista** is a **documentation-only repository** providing comprehensive guides for building retro game ports from classic platforms (C64, Amiga, Arcade) to modern systems. This repository contains NO executable code, build systems, or test infrastructure.

**Key Facts:**
- **Type:** Pure documentation repository (20+ markdown files, ~2100 lines)
- **Languages:** Markdown only
- **No compilation:** No build steps, package managers, or dependencies to install
- **No tests:** Documentation has no automated test infrastructure
- **No CI/CD:** No GitHub Actions workflows or automated validation
- **Target Audience:** Complete beginners to experienced game developers
- **License:** GNU General Public License v3.0

## Repository Structure

```
retromista/
├── .github/                    # GitHub configuration
│   └── copilot-instructions.md # This file
├── .gitignore                  # Excludes Unity/Godot/C64 build artifacts
├── README.md                   # Main entry point - comprehensive overview
├── CONTRIBUTING.md             # Contribution guidelines and code of conduct
├── QUICK_REFERENCE.md          # Quick reference card for developers
├── SUMMARY.md                  # Framework summary and statistics
├── LICENSE                     # GPL v3.0 license
│
├── docs/                       # Core documentation
│   ├── GETTING_STARTED.md     # Beginner's guide - START HERE
│   ├── FAQ.md                 # 60+ common questions answered
│   └── TROUBLESHOOTING.md     # Platform-specific solutions
│
├── emulators/                  # Classic platform development
│   └── README.md              # WinVICE, WinUAE, MAME setup guides
│
├── modern-dev/                 # Modern game engines
│   ├── README.md              # Framework overview
│   ├── unity/README.md        # Unity setup (recommended for beginners)
│   ├── godot/README.md        # Godot setup (open source)
│   └── visual-studio/README.md # VS + SDL2/SFML/MonoGame/Raylib
│
├── tutorials/                  # Step-by-step tutorials
│   ├── c64-basics.md          # C64 BASIC and Assembly
│   └── modern-first-game.md   # Complete Unity game tutorial (2-4 hours)
│
├── assets/                     # Asset creation guides
│   └── README.md              # Graphics without design skills
│
├── audio/                      # Music and sound guides
│   └── README.md              # Chiptune music and SFX creation
│
├── examples/                   # Example project structures
│   └── README.md              # Templates and guidelines
│
└── tools/                      # Tool recommendations
    └── README.md              # 50+ tools catalog with comparisons
```

## Working with This Repository

### What You CAN Do
- ✅ Edit markdown documentation files
- ✅ Add new documentation pages
- ✅ Update tool recommendations
- ✅ Improve tutorials and examples
- ✅ Fix typos, formatting, and broken links
- ✅ Add new guides for platforms/frameworks

### What You CANNOT Do (Because They Don't Exist)
- ❌ Run build commands (no build system exists)
- ❌ Run tests (no test infrastructure)
- ❌ Install dependencies (no package.json, requirements.txt, etc.)
- ❌ Compile code (this is markdown only)
- ❌ Run linters (no markdown linting configured)

### Validation Steps for Changes

Since this is a documentation repository with no automated validation, **manually verify** your changes:

1. **Check Markdown Syntax:**
   ```bash
   # Use any markdown preview tool or GitHub preview
   # Ensure proper formatting: headings, lists, code blocks, tables
   ```

2. **Verify Links:**
   ```bash
   # Check all internal links point to existing files
   # Example: [Getting Started](docs/GETTING_STARTED.md)
   # Ensure relative paths are correct
   ```

3. **Review File Structure:**
   ```bash
   # Ensure new files follow naming conventions:
   # - Use kebab-case: modern-first-game.md
   # - Place in appropriate directory
   # - Update parent README.md with links
   ```

4. **Check Consistency:**
   - Use existing documentation style (see CONTRIBUTING.md)
   - Match tone: beginner-friendly, encouraging, step-by-step
   - Include code blocks with proper language tags
   - Add tables for comparisons

## Key Documentation Guidelines

### Writing Style (Critical for This Repository)
- **Target audience:** Complete beginners
- **Language:** Simple, clear, encouraging
- **Format:** Step-by-step instructions with examples
- **Include:** Screenshots when helpful (though not in repo currently)
- **Structure:** Use H2 (##) for sections, H3 (###) for subsections
- **Code blocks:** Always specify language (```bash, ```csharp, etc.)

### File Modification Patterns

**When updating README.md:**
- Main entry point for users
- Keep tool recommendations current
- Maintain clear navigation to other docs
- Update learning paths if adding new content

**When updating CONTRIBUTING.md:**
- Guidelines for contributors
- Code style examples for Unity/C64
- License requirements (GPL v3 compatible only)
- PR process and templates

**When adding tutorials (tutorials/):**
- Follow structure of existing tutorials
- Include: Learning outcomes, requirements, step-by-step guide
- Provide code examples with explanations
- Add to main README.md and docs/GETTING_STARTED.md

**When adding guides (modern-dev/, emulators/):**
- Platform-specific setup instructions
- Tool recommendations with version numbers
- Troubleshooting section
- Link from docs/GETTING_STARTED.md

**When updating tools (tools/README.md):**
- Categorize properly (Graphics, Audio, Development, etc.)
- Include: Tool name, cost, platform, link
- Update "Recommended Tool Stacks" section
- Maintain comparison tables

### Common Documentation Tasks

**Adding a new tutorial:**
```bash
# 1. Create file in tutorials/
# 2. Follow template from existing tutorials
# 3. Update README.md in "Tutorials & Examples" section
# 4. Update docs/GETTING_STARTED.md with link
# 5. Add to QUICK_REFERENCE.md if major content
```

**Adding a new platform guide:**
```bash
# 1. Create README.md in appropriate directory (emulators/ or modern-dev/)
# 2. Include: Setup, First Steps, Troubleshooting
# 3. Update parent directory README.md
# 4. Update main README.md platform list
# 5. Add FAQs to docs/FAQ.md
# 6. Add common issues to docs/TROUBLESHOOTING.md
```

**Updating tool recommendations:**
```bash
# 1. Edit tools/README.md
# 2. Add to appropriate category
# 3. Update comparison tables
# 4. Update "Recommended Tool Stacks" section
# 5. Consider updating main README.md if widely useful
```

## Important Files and Their Purpose

### Critical Entry Points (Always Check These)
- **README.md** - First file users see, navigation hub
- **docs/GETTING_STARTED.md** - Primary beginner guide, path selection
- **CONTRIBUTING.md** - Contributor guidelines, standards

### Configuration Files
- **.gitignore** - Excludes Unity/Godot/C64 build artifacts (Library/, Temp/, *.prg, etc.)
- **LICENSE** - GPL v3.0 - ALL contributions must be compatible

### Reference Files
- **QUICK_REFERENCE.md** - One-page cheat sheet for developers
- **SUMMARY.md** - Statistics, overview, maintenance notes
- **docs/FAQ.md** - 60+ Q&A, frequently updated
- **docs/TROUBLESHOOTING.md** - Platform-specific issue solutions

## Content Completeness Checklist

When adding major new content, ensure:

- [ ] Main README.md updated with navigation links
- [ ] docs/GETTING_STARTED.md updated if adds new path/option
- [ ] Appropriate section README.md updated (emulators/, modern-dev/, etc.)
- [ ] QUICK_REFERENCE.md updated if fundamental change
- [ ] Related FAQs added to docs/FAQ.md
- [ ] Common issues added to docs/TROUBLESHOOTING.md
- [ ] Tool recommendations in tools/README.md if applicable
- [ ] All internal links tested and working
- [ ] Markdown formatting consistent with existing files
- [ ] Beginner-friendly language maintained

## Special Considerations

### No Build/Test Commands to Run
This repository has **no commands to execute**. Do NOT attempt to:
- Run `npm install`, `pip install`, or similar (not applicable)
- Execute build scripts (none exist)
- Run test suites (no tests)
- Compile anything (markdown only)

### Git Ignore Patterns
The .gitignore is configured for **users of the guides** (not this repo):
- Unity artifacts: Library/, Temp/, *.csproj, *.sln
- Godot artifacts: .import/, export_presets.cfg
- C64/Amiga: *.prg, *.d64 (except in examples/)
- IDE: .vscode/, .vs/, .idea/

### License Compliance
**Critical:** All contributions must be GPL v3.0 compatible:
- ✅ GPL v3, Public Domain (CC0), CC-BY
- ❌ Proprietary licenses, incompatible copyrights
- Document license for any external content referenced

## Workflow for Changes

### Standard Documentation Update
1. **Identify files to modify** (use structure above)
2. **Make surgical changes** - minimal necessary edits
3. **Check markdown syntax** - preview formatting
4. **Verify all links** - ensure relative paths work
5. **Update navigation** - parent READMEs, main README if needed
6. **Review for consistency** - match existing style and tone
7. **Commit with clear message** - describe what changed

### Adding New Content
1. **Determine location** - which directory fits best?
2. **Check existing structure** - follow established patterns
3. **Create content** - follow style guidelines in CONTRIBUTING.md
4. **Link from navigation** - README.md, GETTING_STARTED.md
5. **Add supporting info** - FAQ entries, troubleshooting tips
6. **Update indexes** - QUICK_REFERENCE.md if major addition

## Trust These Instructions

The information in this file is **accurate and complete** for this repository. You do NOT need to:
- Search for build files (none exist)
- Look for test infrastructure (not present)
- Find CI/CD configs (no workflows)
- Locate package managers (not applicable)

This is a **pure documentation repository**. Focus on markdown quality, navigation clarity, and maintaining the beginner-friendly tone that makes RetroMista accessible to everyone.

## Quick Reference for Common Tasks

**Fix typo:** Edit file directly, verify markdown renders correctly
**Add tool:** Update tools/README.md, add to category and comparison tables
**New tutorial:** Create in tutorials/, link from README.md and GETTING_STARTED.md
**Update FAQ:** Add Q&A to docs/FAQ.md, categorize appropriately
**Fix broken link:** Update relative path, verify target file exists
**Add platform:** Create guide in emulators/ or modern-dev/, update all navigation

---

**Remember:** This repository helps beginners build retro games. Keep content accessible, encouraging, and well-organized. Quality documentation is the only product here.
