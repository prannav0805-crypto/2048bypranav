# 2048 Game in Python (Turtle Version)

This is a simple implementation of the classic **2048 game** using Python’s built-in `turtle` graphics module.
The grid is drawn using `turtle`, and new tiles appear after each valid move.

> **Note:** In the current version of the code you shared, the **Up** and **Down** moves work, but the **Left** and **Right** functions are just placeholders (`pass`) and don’t contain movement logic yet.

---

## Features

* 4×4 2048 grid rendered with `turtle`
* Colored tiles depending on their value (2, 4, 8, 16, …)
* Randomly generated tiles (2 or 4) after each move
* Up and Down movement logic implemented
* Framework in place for Left and Right moves
* Keyboard controls using the arrow keys

---

## Requirements

* **Python 3.x**
* `turtle` module (included by default with most Python installations)
* Runs on:

  * Windows
  * macOS
  * Linux (with a GUI environment)

No extra third-party libraries are needed. Only:

```python
import turtle
import random
```

---

## How to Run

1. **Save the code** into a file, for example:

   ```text
   2048_turtle.py
   ```

2. Open a terminal / command prompt in the folder where the file is saved.

3. Run:

   ```bash
   python 2048_turtle.py
   ```

4. A new window will open showing the 4×4 grid and the starting tiles.

---

## Controls

Use your **keyboard arrow keys** to move the tiles:

* ⬆️ **Up Arrow** – moves tiles up
* ⬇️ **Down Arrow** – moves tiles down
* ⬅️ **Left Arrow** – currently bound but not implemented
* ➡️ **Right Arrow** – currently bound but not implemented

After each valid move:

* Tiles slide in the chosen direction.
* Tiles with the same value that collide are merged into one tile (their value is doubled).
* A new tile (2 or 4) appears at a random empty position.

---

## Code Structure

### 1. Imports and Setup

```python
import turtle
import random

wn = turtle.Screen()
wn.title("2048 by @Pranavdange")
wn.bgcolor("black")
wn.setup(width=450, height=400)
wn.tracer(0)
```

* Sets up the game window with a title, background color, and size.
* `wn.tracer(0)` turns off automatic screen updates to avoid flickering.

### 2. Game State

```python
score = 0

grid = [
    [0, 0, 0, 16],
    [0, 0, 8, 0],
    [0, 4, 0, 0],
    [2, 4, 8, 16]
]

grid_merged = [
    [False, False, False, False],
    [False, False, False, False],
    [False, False, False, False],
    [False, False, False, False]
]
```

* `grid` stores the current numbers on the 4×4 board.
* `grid_merged` tracks whether a tile has already merged during the current move (to prevent double merges).

### 3. Drawing with Turtle

A `turtle.Turtle()` object named `pen` is used to draw the grid and numbers:

```python
pen = turtle.Turtle()
pen.speed(0)
pen.shape("square")
pen.color("white")
pen.penup()
pen.hideturtle()
pen.turtlesize(stretch_wid=2, stretch_len=2, outline=2)
```

### 4. `draw_grid()` Function

* Loops through the `grid` list.
* Chooses a color based on the tile value.
* Stamps a colored square.
* Draws the number on top (if the value is not 0).

```python
def draw_grid():
    colors = {
        0: "white",
        2: "yellow",
        4: "orange",
        8: "pink",
        16: "red",
        32: "light green",
        64: "green",
        128: "light purple",
        256: "purple",
        512: "gold",
        1024: "silver",
        2048: "black"
    }
    # loops over grid and draws tiles...
```

### 5. `add_random()` Function

* Adds a new tile (2 or 4) at a random empty position:

```python
def add_random():
    added = False
    while not added:
        x = random.randint(0, 3)
        y = random.randint(0, 3)
        value = random.choice([2, 4])
        if grid[y][x] == 0:
            grid[y][x] = value
            added = True
```

### 6. Movement Functions

#### `up()`

* Moves tiles up, merging equal tiles once per move.
* After movement:

  * Resets `grid_merged`
  * Adds a random tile
  * Redraws the grid

#### `down()`

* Similar logic to `up()`, but moves and merges tiles downward.

#### `left()` and `right()`

Currently:

```python
def left():
    pass
    draw_grid()
    
def right():
    pass
    draw_grid()
```

* These are placeholders. Logic for sliding/merging tiles left and right still needs to be added.

### 7. Keyboard Bindings

```python
wn.listen()
wn.onkeypress(left, "Left")
wn.onkeypress(right, "Right")
wn.onkeypress(up, "Up")
wn.onkeypress(down, "Down")
wn.mainloop()
```

* Connects the arrow keys to the corresponding movement functions.
* `wn.mainloop()` keeps the window open and listens for events.

---

## Known Limitations / To-Do

* [ ] Implement **left** movement logic
* [ ] Implement **right** movement logic
* [ ] Add a **score** display that updates when tiles merge
* [ ] Add **game over** detection (no empty cells and no possible merges)
* [ ] Add **restart** button or key
* [ ] Smooth animations for movement (optional)

---

## Customization Ideas

* Change tile colors in the `colors` dictionary in `draw_grid()`.
* Adjust the window size and tile spacing for a different look.
* Modify the starting `grid` to always start with two tiles instead of a fixed layout.
* Add music/sound effects using another library (e.g. `pygame` for audio).

---

## Credits

* **Developer:** @Pranavdange
* **Language:** Python 3
* **Graphics:** `turtle` module

Feel free to edit and expand this project to make a full-featured 2048 clone!
