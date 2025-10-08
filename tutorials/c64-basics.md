# C64 Basics Tutorial

Learn to create simple games on the Commodore 64 using BASIC and Assembly.

## Prerequisites

- WinVICE emulator installed (see [Emulator Setup](../../emulators/README.md))
- Basic understanding of programming concepts

## Getting Started with BASIC

### Your First Program

1. **Start WinVICE (x64sc.exe)**
2. You'll see the blue C64 screen with cursor
3. Type this program:

```basic
10 PRINT "HELLO RETRO WORLD"
20 GOTO 10
```

4. Type `RUN` and press ENTER
5. You'll see scrolling "HELLO RETRO WORLD"
6. Press `RUN/STOP` key to stop (ESC in WinVICE)

### Understanding C64 BASIC

#### Basic Commands
- `PRINT` - Display text or numbers
- `GOTO` - Jump to line number
- `IF...THEN` - Conditional logic
- `FOR...NEXT` - Loops
- `INPUT` - Get user input
- `POKE` - Write to memory
- `PEEK` - Read from memory

#### Screen Control
- `CLR` - Clear variables
- `PRINT CHR$(147)` - Clear screen
- `POKE 53280,X` - Border color (0-15)
- `POKE 53281,X` - Background color (0-15)

## Simple Game: Guess the Number

```basic
10 PRINT CHR$(147)
20 PRINT "GUESS THE NUMBER (1-10)"
30 N=INT(RND(1)*10)+1
40 INPUT "YOUR GUESS";G
50 IF G=N THEN PRINT "CORRECT!":GOTO 100
60 IF G<N THEN PRINT "HIGHER!"
70 IF G>N THEN PRINT "LOWER!"
80 GOTO 40
100 PRINT "PLAY AGAIN? (Y/N)"
110 GET A$:IF A$="" THEN 110
120 IF A$="Y" THEN 10
130 END
```

**How it works:**
- Line 30: Generate random number 1-10
- Line 40: Get player's guess
- Lines 50-70: Check guess and give hint
- Lines 100-120: Ask to play again

## Graphics on C64

### Character Graphics (Easiest)

The C64 screen is 40x25 characters. Each character can be changed.

```basic
10 PRINT CHR$(147):REM CLEAR SCREEN
20 FOR I=1 TO 40
30 POKE 1024+I,160:REM DRAW LINE AT TOP
40 NEXT I
50 POKE 55296,1:REM COLOR WHITE
```

### PETSCII Graphics

Use built-in character graphics:

```basic
10 PRINT CHR$(147)
20 PRINT "    ****    "
30 PRINT "   *    *   "
40 PRINT "   * ** *   "
50 PRINT "   *    *   "
60 PRINT "    ****    "
```

### Using Sprites (Hardware Sprites)

C64 has 8 hardware sprites (24x21 pixels, 3 colors).

```basic
10 PRINT CHR$(147)
20 POKE 53269,1:REM ENABLE SPRITE 0
30 POKE 2040,13:REM SPRITE POINTER
40 POKE 53287,1:REM SPRITE COLOR (WHITE)
50 POKE 53248,100:REM X POSITION
60 POKE 53249,100:REM Y POSITION
```

## Simple Game: PONG Clone

```basic
5 REM === C64 PONG ===
10 PRINT CHR$(147)
20 POKE 53280,0:POKE 53281,0
30 P1=12:P2=12:BX=20:BY=12:DX=1:DY=1
40 S=0

50 REM DRAW PADDLES AND BALL
60 POKE 1024+P1*40,93:REM LEFT PADDLE
70 POKE 1024+P2*40+39,93:REM RIGHT PADDLE
80 POKE 1024+BY*40+BX,81:REM BALL

90 REM MOVE BALL
100 BX=BX+DX:BY=BY+DY

110 REM BOUNCE TOP/BOTTOM
120 IF BY<1 OR BY>23 THEN DY=-DY

130 REM CHECK PADDLE HITS
140 IF BX<2 AND BY=P1 THEN DX=1:S=S+1
150 IF BX>37 AND BY=P2 THEN DX=-1:S=S+1

160 REM CHECK SCORE
170 IF BX<1 OR BX>38 THEN PRINT "SCORE:";S:END

180 REM PLAYER CONTROLS
190 GET K$
200 IF K$="W" AND P1>1 THEN P1=P1-1
210 IF K$="S" AND P1<23 THEN P1=P1+1
220 IF K$="I" AND P2>1 THEN P2=P2-1
230 IF K$="K" AND P2<23 THEN P2=P2+1

240 REM CLEAR OLD POSITIONS
250 PRINT CHR$(147)

260 GOTO 50
```

**Controls:**
- W/S: Move left paddle
- I/K: Move right paddle

## Sound on C64

The C64 has a SID chip (3 voices).

### Simple Sound Effect

```basic
10 S=54272:REM SID BASE ADDRESS
20 POKE S+24,15:REM MAX VOLUME
30 POKE S+5,9:POKE S+6,0:REM ATTACK/DECAY
40 POKE S+1,50:REM FREQUENCY
50 POKE S+4,17:REM WAVEFORM (TRIANGLE)
60 FOR I=1 TO 100:NEXT:REM DELAY
70 POKE S+4,16:REM SOUND OFF
```

### Music Note

```basic
10 S=54272
20 FOR N=1 TO 8
30 READ F
40 POKE S+24,15
50 POKE S+1,F
60 POKE S+4,17
70 FOR D=1 TO 200:NEXT
80 POKE S+4,16
90 NEXT N
100 DATA 50,60,70,80,90,100,110,120
```

## Advanced: Moving to Assembly

For fast games, you need 6502 Assembly.

### Why Assembly?
- BASIC is slow (interpreted)
- Assembly is 100x faster
- Required for smooth action games

### Tools for Assembly
1. **CBM prg Studio** (Windows) - Easiest IDE
2. **ACME** - Cross assembler
3. **Kick Assembler** - Modern assembler
4. **64TASS** - Fast assembler

### Simple Assembly Example

```asm
* = $1000           ; Start address

lda #$00           ; Load 0 into A
sta $d020          ; Store in border color
sta $d021          ; Store in background color

loop:
    inc $d020      ; Increment border color
    jmp loop       ; Jump back

    rts            ; Return
```

## Resources & Next Steps

### Learn More BASIC
- [C64 BASIC Programming](https://www.c64-wiki.com/wiki/BASIC)
- [Retro Game Programming Book](https://www.c64-wiki.com/wiki/Book:Retro_Game_Programming)

### Learn Assembly
- [Easy 6502](https://skilldrick.github.io/easy6502/) - Interactive tutorial
- [6502 Assembly Tutorial](https://www.youtube.com/watch?v=oO8_If1bh3c)
- [Dustlayer C64 Tutorials](https://dustlayer.com/c64-coding-tutorials/)

### Development Tools
- **CBM prg Studio:** [Download](https://www.ajordison.co.uk/)
- **VICE Monitor:** Built-in debugger
- **SpritePad:** Sprite editor
- **CharPad:** Character editor

### Example Projects
1. Start with text-based games
2. Move to character graphics
3. Add sprites for smooth movement
4. Learn assembly for speed
5. Create full game!

## Tips for C64 Development

1. **Start simple:** Text games first
2. **Use tools:** CBM prg Studio makes life easier
3. **Plan memory:** C64 has only 64KB
4. **Save often:** VICE saves states
5. **Study classics:** Load old games and learn
6. **Join community:** Lemon64, CSDB forums

## Common C64 Memory Locations

| Address | Purpose |
|---------|---------|
| 1024-2023 | Screen memory |
| 53248+ | Sprite registers |
| 53280 | Border color |
| 53281 | Background color |
| 54272+ | SID (sound) chip |
| 55296+ | Color RAM |

## Next Steps

1. Try all example programs
2. Modify them to learn
3. Create your own simple game
4. Download CBM prg Studio
5. Try sprite graphics
6. Learn basic assembly
7. Create a full game!

## Additional Resources

- [C64-Wiki](https://www.c64-wiki.com/)
- [Lemon64 Forums](https://www.lemon64.com/)
- [CSDB](https://csdb.dk/) - C64 Scene Database
- [Codebase64](http://codebase64.org/) - Code examples
