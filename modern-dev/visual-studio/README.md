# Visual Studio Setup for Retro Game Development

Guide to setting up Visual Studio with C++/C# frameworks for retro game development.

## Why Visual Studio?

- **Professional IDE:** Industry-standard development environment
- **Full Control:** Maximum flexibility and performance
- **Multiple Languages:** C++, C#, and more
- **Great Debugging:** Best-in-class debugging tools
- **Free Version:** Community edition is free

## Installation

### Step 1: Download Visual Studio

1. Visit [visualstudio.microsoft.com](https://visualstudio.microsoft.com/)
2. Download **Visual Studio Community** (free)
3. Run installer

### Step 2: Choose Workloads

Select based on your needs:

**For C++ Game Development:**
- ✅ Desktop development with C++
- ✅ Game development with C++ (optional, includes Unreal)

**For C# Game Development:**
- ✅ .NET desktop development
- ✅ Game development with Unity (if using Unity)

**For Both:**
- ✅ Desktop development with C++
- ✅ .NET desktop development

Click **Install** (may take 30-60 minutes)

## Choose Your Framework

### Option 1: SDL2 (C/C++) - Recommended for Beginners

**Why SDL2?**
- Simple to learn
- Cross-platform
- Low-level control
- Industry standard
- Great for retro games

### Option 2: SFML (C++) - Modern C++ API

**Why SFML?**
- Modern C++ API
- Easy to use
- Object-oriented
- Good documentation

### Option 3: MonoGame (C#) - XNA Successor

**Why MonoGame?**
- C# language (easier than C++)
- Good for XNA developers
- Cross-platform
- Active community

### Option 4: Raylib (C/C++) - Simplest Option

**Why Raylib?**
- Extremely simple API
- Perfect for learning
- Retro-friendly
- Minimal setup

## Setup SDL2 (C++)

### Step 1: Install vcpkg (Package Manager)

```bash
# Open PowerShell
cd C:\
git clone https://github.com/Microsoft/vcpkg.git
cd vcpkg
.\bootstrap-vcpkg.bat
.\vcpkg integrate install
```

### Step 2: Install SDL2

```bash
.\vcpkg install sdl2 sdl2-image sdl2-mixer sdl2-ttf
```

### Step 3: Create Project

1. Open Visual Studio
2. **Create new project**
3. Choose **Empty Project** (C++)
4. Name: "MyRetroGame"
5. Create

### Step 4: Configure Project

1. **Right-click project** → Properties
2. **C/C++** → General:
   - Additional Include Directories: (vcpkg handles this)
3. **Linker** → Input:
   - Additional Dependencies: (vcpkg handles this)
4. Click OK

### Step 5: First SDL2 Program

Create `main.cpp`:

```cpp
#include <SDL.h>
#include <iostream>

const int SCREEN_WIDTH = 320;
const int SCREEN_HEIGHT = 180;
const int SCALE = 4;

int main(int argc, char* argv[]) {
    // Initialize SDL
    if (SDL_Init(SDL_INIT_VIDEO) < 0) {
        std::cout << "SDL Error: " << SDL_GetError() << std::endl;
        return 1;
    }

    // Create window
    SDL_Window* window = SDL_CreateWindow(
        "My Retro Game",
        SDL_WINDOWPOS_CENTERED,
        SDL_WINDOWPOS_CENTERED,
        SCREEN_WIDTH * SCALE,
        SCREEN_HEIGHT * SCALE,
        SDL_WINDOW_SHOWN
    );

    // Create renderer
    SDL_Renderer* renderer = SDL_CreateRenderer(
        window, -1, 
        SDL_RENDERER_ACCELERATED | SDL_RENDERER_PRESENTVSYNC
    );
    
    // Set logical size for pixel-perfect scaling
    SDL_RenderSetLogicalSize(renderer, SCREEN_WIDTH, SCREEN_HEIGHT);

    // Main game loop
    bool running = true;
    SDL_Event event;
    int playerX = SCREEN_WIDTH / 2;
    int playerY = SCREEN_HEIGHT / 2;

    while (running) {
        // Handle events
        while (SDL_PollEvent(&event)) {
            if (event.type == SDL_QUIT) {
                running = false;
            }
        }

        // Handle input
        const Uint8* keys = SDL_GetKeyboardState(NULL);
        if (keys[SDL_SCANCODE_LEFT]) playerX -= 2;
        if (keys[SDL_SCANCODE_RIGHT]) playerX += 2;
        if (keys[SDL_SCANCODE_UP]) playerY -= 2;
        if (keys[SDL_SCANCODE_DOWN]) playerY += 2;

        // Clear screen (black)
        SDL_SetRenderDrawColor(renderer, 0, 0, 0, 255);
        SDL_RenderClear(renderer);

        // Draw player (white square)
        SDL_Rect player = {playerX, playerY, 16, 16};
        SDL_SetRenderDrawColor(renderer, 255, 255, 255, 255);
        SDL_RenderFillRect(renderer, &player);

        // Present
        SDL_RenderPresent(renderer);
        
        SDL_Delay(16); // ~60 FPS
    }

    // Cleanup
    SDL_DestroyRenderer(renderer);
    SDL_DestroyWindow(window);
    SDL_Quit();

    return 0;
}
```

Press **F5** to build and run!

## Setup SFML (C++)

### Step 1: Install via vcpkg

```bash
cd C:\vcpkg
.\vcpkg install sfml
```

### Step 2: Create Project

1. Visual Studio → New Project
2. Empty Project (C++)
3. Name: "MyRetroGameSFML"

### Step 3: First SFML Program

Create `main.cpp`:

```cpp
#include <SFML/Graphics.hpp>

int main() {
    // Create window
    sf::RenderWindow window(sf::VideoMode(1280, 720), "My Retro Game");
    window.setFramerateLimit(60);

    // Create player
    sf::RectangleShape player(sf::Vector2f(16.f, 16.f));
    player.setFillColor(sf::Color::White);
    player.setPosition(320.f, 180.f);

    float speed = 200.f;

    // Game loop
    sf::Clock clock;
    while (window.isOpen()) {
        float deltaTime = clock.restart().asSeconds();

        // Events
        sf::Event event;
        while (window.pollEvent(event)) {
            if (event.type == sf::Event::Closed)
                window.close();
        }

        // Input
        sf::Vector2f movement(0.f, 0.f);
        if (sf::Keyboard::isKeyPressed(sf::Keyboard::Left))
            movement.x -= speed * deltaTime;
        if (sf::Keyboard::isKeyPressed(sf::Keyboard::Right))
            movement.x += speed * deltaTime;
        if (sf::Keyboard::isKeyPressed(sf::Keyboard::Up))
            movement.y -= speed * deltaTime;
        if (sf::Keyboard::isKeyPressed(sf::Keyboard::Down))
            movement.y += speed * deltaTime;

        player.move(movement);

        // Render
        window.clear(sf::Color::Black);
        window.draw(player);
        window.display();
    }

    return 0;
}
```

## Setup MonoGame (C#)

### Step 1: Install MonoGame

1. Download [MonoGame](https://www.monogame.net/downloads/)
2. Install MonoGame SDK
3. Install Visual Studio templates

### Step 2: Create Project

1. Visual Studio → New Project
2. Search "MonoGame"
3. Choose **MonoGame Cross-Platform Desktop Application**
4. Name: "MyRetroGame"
5. Create

### Step 3: First MonoGame Program

Edit `Game1.cs`:

```csharp
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;
using Microsoft.Xna.Framework.Input;

namespace MyRetroGame
{
    public class Game1 : Game
    {
        private GraphicsDeviceManager graphics;
        private SpriteBatch spriteBatch;
        private Texture2D pixel;
        private Vector2 playerPos;
        private float speed = 200f;

        public Game1()
        {
            graphics = new GraphicsDeviceManager(this);
            Content.RootDirectory = "Content";
            IsMouseVisible = true;
            
            // Set resolution
            graphics.PreferredBackBufferWidth = 1280;
            graphics.PreferredBackBufferHeight = 720;
        }

        protected override void LoadContent()
        {
            spriteBatch = new SpriteBatch(GraphicsDevice);
            
            // Create 1x1 pixel texture
            pixel = new Texture2D(GraphicsDevice, 1, 1);
            pixel.SetData(new[] { Color.White });
            
            playerPos = new Vector2(320, 180);
        }

        protected override void Update(GameTime gameTime)
        {
            if (Keyboard.GetState().IsKeyDown(Keys.Escape))
                Exit();

            var deltaTime = (float)gameTime.ElapsedGameTime.TotalSeconds;
            var keyState = Keyboard.GetState();

            if (keyState.IsKeyDown(Keys.Left))
                playerPos.X -= speed * deltaTime;
            if (keyState.IsKeyDown(Keys.Right))
                playerPos.X += speed * deltaTime;
            if (keyState.IsKeyDown(Keys.Up))
                playerPos.Y -= speed * deltaTime;
            if (keyState.IsKeyDown(Keys.Down))
                playerPos.Y += speed * deltaTime;

            base.Update(gameTime);
        }

        protected override void Draw(GameTime gameTime)
        {
            GraphicsDevice.Clear(Color.Black);

            spriteBatch.Begin(samplerState: SamplerState.PointClamp);
            
            // Draw player (16x16 white square)
            spriteBatch.Draw(pixel, 
                new Rectangle((int)playerPos.X, (int)playerPos.Y, 16, 16), 
                Color.White);
            
            spriteBatch.End();

            base.Draw(gameTime);
        }
    }
}
```

## Setup Raylib (C/C++)

### Step 1: Install Raylib

```bash
cd C:\vcpkg
.\vcpkg install raylib
```

### Step 2: Create Project

1. Visual Studio → New Project
2. Empty Project (C++)
3. Name: "MyRetroGameRaylib"

### Step 3: First Raylib Program

Create `main.cpp`:

```cpp
#include "raylib.h"

int main() {
    // Initialize
    const int screenWidth = 1280;
    const int screenHeight = 720;
    
    InitWindow(screenWidth, screenHeight, "My Retro Game");
    SetTargetFPS(60);

    Vector2 playerPos = { 320, 180 };
    float speed = 200.0f;

    // Game loop
    while (!WindowShouldClose()) {
        // Update
        if (IsKeyDown(KEY_LEFT)) playerPos.x -= speed * GetFrameTime();
        if (IsKeyDown(KEY_RIGHT)) playerPos.x += speed * GetFrameTime();
        if (IsKeyDown(KEY_UP)) playerPos.y -= speed * GetFrameTime();
        if (IsKeyDown(KEY_DOWN)) playerPos.y += speed * GetFrameTime();

        // Draw
        BeginDrawing();
            ClearBackground(BLACK);
            DrawRectangle(playerPos.x, playerPos.y, 16, 16, WHITE);
        EndDrawing();
    }

    CloseWindow();
    return 0;
}
```

## Pixel Perfect Rendering

### SDL2 Pixel Perfect

```cpp
// Use logical size
SDL_RenderSetLogicalSize(renderer, 320, 180);
SDL_RenderSetIntegerScale(renderer, SDL_TRUE);
```

### SFML Pixel Perfect

```cpp
// Create render texture
sf::RenderTexture renderTexture;
renderTexture.create(320, 180);

// In render loop
renderTexture.clear();
// Draw to renderTexture
renderTexture.display();

// Draw to window scaled
sf::Sprite sprite(renderTexture.getTexture());
sprite.setScale(4.f, 4.f); // 4x scale
window.draw(sprite);
```

## Debugging Tips

### Visual Studio Debugging

- **F5:** Start debugging
- **F9:** Set breakpoint
- **F10:** Step over
- **F11:** Step into
- **Watch window:** Monitor variables

### Common Issues

**Linker errors:**
- Check vcpkg integration
- Verify library paths
- Rebuild solution

**SDL/SFML not found:**
- Reinstall via vcpkg
- Check include directories

## Framework Comparison

| Framework | Language | Difficulty | Best For |
|-----------|----------|------------|----------|
| SDL2 | C/C++ | Medium | Control, Performance |
| SFML | C++ | Easy | Modern C++, Quick start |
| MonoGame | C# | Easy | C# developers, XNA |
| Raylib | C/C++ | Very Easy | Beginners, Learning |

## Recommended Learning Path

### Week 1: Setup & Basics
1. Install Visual Studio
2. Choose framework (Raylib for beginners)
3. Create window and render loop
4. Handle input

### Week 2: Game Objects
1. Create player class
2. Add movement
3. Collision detection
4. Basic physics

### Week 3: Complete Game
1. Add enemies
2. Scoring system
3. Sound effects
4. Polish and release

## Resources

### SDL2
- [Lazy Foo' Tutorials](https://lazyfoo.net/tutorials/SDL/)
- [SDL Wiki](https://wiki.libsdl.org/)

### SFML
- [SFML Tutorials](https://www.sfml-dev.org/tutorials/)
- [SFML Game Dev Book](https://www.packtpub.com/game-development/sfml-game-development)

### MonoGame
- [MonoGame Docs](https://docs.monogame.net/)
- [RB Whitaker Tutorials](http://rbwhitaker.wikidot.com/monogame-tutorials)

### Raylib
- [Raylib Examples](https://www.raylib.com/examples.html)
- [Raylib Cheatsheet](https://www.raylib.com/cheatsheet/cheatsheet.html)

## Next Steps

1. Complete framework setup
2. Build Pong clone
3. Add sprites and audio
4. Create Space Invaders
5. Design original game!

**Happy coding!** 🚀
