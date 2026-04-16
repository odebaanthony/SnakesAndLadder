SnakesAndLadder
This is a Snakes and Ladder Game that was created by Group 7 Data Structure and Algorithms students and Odeba Anthony at Victoria University Kampala, 
🐍 Snakes and Ladders

A fully animated, two-player **Snakes and Ladders** desktop game built in **Java Swing** — featuring smooth token movement, a rolling dice animation, and a classic 10×10 zigzag board rendered entirely with Java2D graphics.

🎮 Features

- Animated dice roll — 14-frame shuffle animation before landing on the final face
- Smooth token movement — tokens step square-by-square across the board via a `javax.swing.Timer` at 80 ms intervals
- Visual board — fully drawn 10×10 grid with alternating cell colours, correct zigzag numbering (bottom-left → top), snake and ladder graphics rendered using `Path2D` and custom line drawing
- Snake & ladder detection — instant O(1) lookup using `HashMap` after each move
- Two-player hot-seat — Red and Blue take turns; the game announces the winner and exits cleanly
- Pure Java — no external libraries; runs anywhere with a JDK

---

 🗂️ Project Structure

com/student/gamez/
└── SnakesAndLadder.java   # Single-file implementation
    ├── SnakesAndLadder     # JFrame — game controller & state
    ├── BoardPanel          # Inner JPanel — board, snakes, ladders, tokens
    ├── DicePanel           # Inner JPanel — animated dice face
    └── RollListener        # Inner ActionListener — roll & move pipeline
```

---

🧱 Data Structures & Algorithms

| Structure | Field | Purpose |
|---|---|---|
| `HashMap<Integer, Integer>` | `snakes` | Head → tail lookup in O(1) |
| `HashMap<Integer, Integer>` | `ladders` | Base → top lookup in O(1) |
| `HashMap<String, Integer>` | `positions` | Player name → current square |
| `ArrayList<String>` | `playerNames` | Ordered turn list |
| Circular index | `(i + 1) % size` | Turn rotation without a queue |
| Bijective function | `getSquareNumber()` / `getPositionCoordinates()` | O(1) square ↔ pixel mapping |
| Callback chain | `RollListener → DiceTimer → moveTimer → finishMove()` | Deferred animation pipeline |

---

 🐍 Board Layout

```
100  99  98  97  96  95  94  93  92  91
 81  82  83  84  85  86  87  88  89  90
 80  79  78  77  76  75  74  73  72  71
 61  62  63  64  65  66  67  68  69  70
 60  59  58  57  56  55  54  53  52  51
 41  42  43  44  45  46  47  48  49  50
 40  39  38  37  36  35  34  33  32  31
 21  22  23  24  25  26  27  28  29  30
 20  19  18  17  16  15  14  13  12  11
  1   2   3   4   5   6   7   8   9  10
```

 Snakes (head → tail)

| Head | Tail |
|------|------|
| 98 | 78 |
| 95 | 75 |
| 93 | 73 |
| 87 | 24 |
| 64 | 60 |
| 62 | 19 |
| 56 | 53 |
| 49 | 11 |
| 47 | 26 |
| 16 | 6  |

Ladders (base → top)

| Base | Top |
|------|-----|
| 80 | 100 |
| 71 | 91  |
| 51 | 67  |
| 36 | 44  |
| 28 | 84  |
| 21 | 42  |
| 9  | 31  |
| 4  | 14  |
| 1  | 38  |

---

🚀 Getting Started

 Prerequisites

- Java 17 or later (uses switch expressions)
- Any IDE (IntelliJ IDEA, Eclipse, VS Code + Java Extension Pack) or plain `javac`

 Compile & Run

```bash
 From the project root
javac -d out src/com/student/gamez/SnakesAndLadder.java
java -cp out com.student.gamez.SnakesAndLadder
```

Or run directly in your IDE by executing the `main` method in `SnakesAndLadder`.

---

 🕹️ How to Play

1. Launch the application — a 10×10 board appears with Red going first.
2. Click **ROLL DICE** — the dice animates through 14 random faces before settling.
3. Your token steps across the board one square at a time.
4. Land on a **ladder base** → climb up automatically.
5. Land on a **snake head** → slide down automatically.
6. First player to reach exactly **square 100** wins. Overshooting keeps you in place.
7. Players alternate turns. Blue plays after Red each round.

 🔧 Customisation

| What to change | Where |
|---|---|
| Add more players | Append names to `playerNames` in the constructor |
| Change snake/ladder positions | Edit `initSnakesAndLadders()` |
| Adjust animation speed | Change `80` (ms) in `moveTimer` or `65` (ms) in `DicePanel.rollTo()` |
| Resize the board | Change `CELL_SIZE` in `BoardPanel` |

---

📄 License

This project is open source and available under the [MIT License](LICENSE).

---

> Built as a Java Swing learning project demonstrating GUI programming, event-driven architecture, 2D graphics rendering, and core data structures.
