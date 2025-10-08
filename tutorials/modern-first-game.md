# Your First Modern Retro Game Tutorial

Build a complete retro-style game from scratch using Unity. Perfect for beginners!

## What We'll Build

A simple **Flappy Bird** style game with retro graphics and sounds.

**Features:**
- Pixel art graphics
- Chiptune music
- High score system
- Retro game feel

**Time needed:** 2-3 hours

## Prerequisites

- Unity installed (see [Unity Setup Guide](../modern-dev/unity/README.md))
- Basic understanding of Unity interface
- Pixel art sprites (we'll create simple ones)

## Step 1: Project Setup (15 min)

### Create New Project
1. Open Unity Hub
2. New Project → 2D (Core)
3. Name: "FlappyRetro"
4. Create

### Configure for Pixel Perfect
1. Window → Package Manager
2. Install "2D Pixel Perfect"
3. Select Main Camera
4. Add Component → Pixel Perfect Camera
5. Settings:
   - Assets PPU: 16
   - Reference Resolution: 320x180
   - Check all options

## Step 2: Create Player Sprite (20 min)

### Option A: Use Simple Square (Fastest)

1. Create → 2D → Sprites → Square
2. Rename to "Player"
3. Scale: 0.5, 0.5, 1
4. Add color: Create Material → Unlit/Color → Choose color

### Option B: Import Pixel Art

1. Use Piskel to create 16x16 bird sprite
2. Export as PNG
3. Import to Unity:
   - Filter Mode: Point
   - Compression: None
   - Pixels Per Unit: 16
4. Drag to scene

### Add Physics

1. Select Player
2. Add Component → Rigidbody 2D
3. Settings:
   - Gravity Scale: 2
   - Collision Detection: Continuous
4. Add Component → Circle Collider 2D

## Step 3: Player Movement Script (30 min)

### Create Script

1. Project → Create → C# Script → "PlayerController"
2. Double-click to open
3. Replace with:

```csharp
using UnityEngine;
using UnityEngine.SceneManagement;

public class PlayerController : MonoBehaviour
{
    public float flapForce = 5f;
    public GameManager gameManager;
    
    private Rigidbody2D rb;
    private bool isDead = false;
    
    void Start()
    {
        rb = GetComponent<Rigidbody2D>();
    }
    
    void Update()
    {
        // Flap on space or click
        if (Input.GetKeyDown(KeyCode.Space) || Input.GetMouseButtonDown(0))
        {
            if (!isDead)
            {
                Flap();
            }
        }
        
        // Rotate based on velocity
        float angle = Mathf.Lerp(0, 90, -rb.velocity.y / 10f);
        transform.rotation = Quaternion.Euler(0, 0, angle);
    }
    
    void Flap()
    {
        rb.velocity = Vector2.up * flapForce;
        // Play sound (we'll add later)
    }
    
    void OnCollisionEnter2D(Collision2D collision)
    {
        if (!isDead)
        {
            isDead = true;
            gameManager.GameOver();
        }
    }
}
```

4. Save and attach to Player

## Step 4: Create Obstacles (30 min)

### Create Pipe Sprite

1. Create → 2D → Sprites → Square
2. Rename "Pipe"
3. Scale: 1, 5, 1 (tall rectangle)
4. Add Component → Box Collider 2D

### Create Pipe Pair

1. Create Empty GameObject → "PipePair"
2. Add two Pipes as children:
   - Top Pipe: Position (0, 4, 0)
   - Bottom Pipe: Position (0, -4, 0)
3. Add gap in middle (3 units)

### Add Trigger for Score

1. Create → 2D → Sprites → Square (invisible)
2. Rename "ScoreTrigger"
3. Make child of PipePair
4. Position: (0, 0, 0)
5. Scale: (0.1, 10, 1)
6. Box Collider 2D:
   - Check "Is Trigger"

### Pipe Movement Script

1. Create script "PipeMove"
2. Code:

```csharp
using UnityEngine;

public class PipeMove : MonoBehaviour
{
    public float speed = 2f;
    
    void Update()
    {
        transform.position += Vector3.left * speed * Time.deltaTime;
        
        // Destroy when off screen
        if (transform.position.x < -10)
        {
            Destroy(gameObject);
        }
    }
}
```

3. Attach to PipePair

## Step 5: Pipe Spawner (20 min)

### Create Spawner Script

1. Create script "PipeSpawner"
2. Code:

```csharp
using UnityEngine;

public class PipeSpawner : MonoBehaviour
{
    public GameObject pipePrefab;
    public float spawnInterval = 2f;
    public float heightRange = 2f;
    
    private float timer;
    
    void Update()
    {
        timer += Time.deltaTime;
        
        if (timer > spawnInterval)
        {
            SpawnPipe();
            timer = 0;
        }
    }
    
    void SpawnPipe()
    {
        float randomY = Random.Range(-heightRange, heightRange);
        Vector3 spawnPos = new Vector3(10, randomY, 0);
        Instantiate(pipePrefab, spawnPos, Quaternion.identity);
    }
}
```

### Setup Spawner

1. Create Empty GameObject → "PipeSpawner"
2. Attach PipeSpawner script
3. Make PipePair a Prefab:
   - Drag PipePair to Project folder
   - Delete from scene
4. Assign prefab to spawner

## Step 6: Game Manager (25 min)

### Create Game Manager

1. Create script "GameManager"
2. Code:

```csharp
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.SceneManagement;

public class GameManager : MonoBehaviour
{
    public Text scoreText;
    public GameObject gameOverPanel;
    
    private int score = 0;
    
    void Start()
    {
        Time.timeScale = 1;
        gameOverPanel.SetActive(false);
    }
    
    public void AddScore()
    {
        score++;
        scoreText.text = score.ToString();
    }
    
    public void GameOver()
    {
        Time.timeScale = 0;
        gameOverPanel.SetActive(true);
    }
    
    public void Restart()
    {
        SceneManager.LoadScene(SceneManager.GetActiveScene().name);
    }
}
```

### Setup UI

1. Create → UI → Canvas
2. Create → UI → Text (for score)
   - Position: Top center
   - Font Size: 48
   - Anchor: Top center
3. Create → UI → Panel (for Game Over)
   - Add Text child: "GAME OVER"
   - Add Button: "RESTART"
4. Create Empty GameObject → "GameManager"
5. Attach GameManager script
6. Assign UI elements

### Score Trigger

1. Create script "ScoreTrigger"
2. Code:

```csharp
using UnityEngine;

public class ScoreTrigger : MonoBehaviour
{
    private GameManager gameManager;
    private bool triggered = false;
    
    void Start()
    {
        gameManager = FindObjectOfType<GameManager>();
    }
    
    void OnTriggerEnter2D(Collider2D collision)
    {
        if (collision.CompareTag("Player") && !triggered)
        {
            triggered = true;
            gameManager.AddScore();
        }
    }
}
```

3. Attach to ScoreTrigger object
4. Set Player tag to "Player"

## Step 7: Add Polish (20 min)

### Camera Background

1. Main Camera → Background: Choose dark color
2. Or import pixel art background

### Parallax Background (Optional)

1. Import cloud/mountain sprites
2. Create layers that move slower
3. Gives depth feeling

### Particle Effects

1. Add simple particle on flap
2. Add explosion on death (optional)

## Step 8: Add Audio (20 min)

### Import Sounds

1. Use Bfxr to create:
   - Flap sound (Jump preset)
   - Score sound (Pickup preset)
   - Death sound (Hit preset)
2. Export as WAV
3. Import to Unity

### Add Audio Sources

1. Player:
   - Add Audio Source
   - Assign flap sound
2. GameManager:
   - Add Audio Source for score/death

### Play Sounds in Scripts

In PlayerController:
```csharp
public AudioClip flapSound;
private AudioSource audioSource;

void Start()
{
    audioSource = GetComponent<AudioSource>();
}

void Flap()
{
    rb.velocity = Vector2.up * flapForce;
    audioSource.PlayOneShot(flapSound);
}
```

### Background Music

1. Import chiptune music (from BeepBox)
2. Add to Main Camera
3. Audio Source:
   - Loop: checked
   - Play On Awake: checked

## Step 9: Build and Test (10 min)

### Test in Editor

1. Press Play
2. Check all features work
3. Adjust difficulty:
   - Pipe speed
   - Spawn interval
   - Gap size

### Build Executable

1. File → Build Settings
2. Add current scene
3. Build and Run
4. Test standalone version

### Build for Web (Optional)

1. File → Build Settings
2. Switch to WebGL
3. Build
4. Upload to itch.io

## Step 10: Improvements (Optional)

### Add Features

1. **High Score:**
   - Use PlayerPrefs to save
   - Display on game over

2. **Difficulty Scaling:**
   - Increase speed over time
   - Smaller gaps at higher scores

3. **Power-ups:**
   - Slow motion
   - Shield
   - Extra points

4. **Better Graphics:**
   - Animated sprites
   - Particle trails
   - Screen shake on death

## Final Code Summary

### Scripts Created:
1. `PlayerController.cs` - Player movement and death
2. `PipeMove.cs` - Obstacle movement
3. `PipeSpawner.cs` - Spawning system
4. `GameManager.cs` - Game state and UI
5. `ScoreTrigger.cs` - Score detection

### GameObjects in Scene:
- Main Camera (Pixel Perfect)
- Player (Rigidbody2D, scripts, sprites)
- PipeSpawner (spawner script)
- GameManager (game logic)
- Canvas (UI elements)

## Troubleshooting

### Player falls through pipes
- Check colliders are not triggers
- Check physics layers

### Pipes don't spawn
- Check prefab is assigned
- Check spawner position

### Score doesn't increase
- Check trigger collider
- Check Player tag

### Game doesn't pause on death
- Check Time.timeScale in GameOver()

## What You Learned

✅ Unity 2D basics
✅ Physics and colliders
✅ Prefabs and instantiation
✅ UI system
✅ Audio integration
✅ Game loop and state management

## Next Steps

1. Polish your game
2. Add more features
3. Try a different game:
   - Pong
   - Breakout
   - Space Invaders
4. Learn more advanced Unity features
5. Publish on itch.io!

## Resources

- [Unity 2D Documentation](https://docs.unity3d.com/Manual/2D.html)
- [Brackeys Tutorials](https://www.youtube.com/c/Brackeys)
- [Unity Learn](https://learn.unity.com/)

**Congratulations!** You've made your first retro game! 🎮
