# 🔴 Connect Four AI with Minimax & Alpha-Beta Pruning

A Python implementation of the classic **Connect Four** strategy game, featuring a graphical interface built with **Pygame** and an intelligent AI opponent powered by the **Minimax algorithm** with **Alpha-Beta Pruning**.

![Python](https://img.shields.io/badge/Python-3.x-blue.svg)
![Pygame](https://img.shields.io/badge/Library-Pygame-yellow.svg)
![NumPy](https://img.shields.io/badge/Library-NumPy-green.svg)

## 🎮 Key Features

* **Graphical User Interface (GUI):** A clean, interactive game board built using `pygame`.
* **Intelligent AI Opponent:** The computer calculates the best possible move using the Minimax algorithm.
* **Alpha-Beta Pruning:** Optimized decision-making that prunes irrelevant branches of the game tree to improve performance and search depth.
* **Heuristic Evaluation:** The AI uses a custom scoring system to evaluate non-terminal board states (e.g., controlling the center, blocking wins).
* **Mouse Input:** Smooth player interaction via mouse movement and clicking.

## 🧠 How It Works (The AI Logic)

The core of this project is the AI's decision-making process, which simulates future moves to determine the optimal strategy.

### 1. Minimax Algorithm
The AI looks ahead **4 moves deep** (`MAX_DEPTH = 4`) into the game tree. It alternates between:
* **Maximizing (AI Turn):** Trying to get the highest possible score.
* **Minimizing (Player Turn):** Assuming the human player will play perfectly to minimize the AI's score.

### 2. Alpha-Beta Pruning
To optimize the expensive Minimax search, the algorithm "prunes" (cuts off) branches of the decision tree that don't need to be explored. If the algorithm finds a move that is worse than a move already examined, it stops looking further down that path.

### 3. Heuristic Scoring Function
Since the AI cannot calculate every possible outcome until the end of the game, it evaluates the board state using a **Sliding Window** technique. It scans every "window" of 4 slots (horizontal, vertical, diagonal) and assigns points:

| Scenario | Score Impact | Reasoning |
| :--- | :--- | :--- |
| **4 in a Row (AI)** | `+100` points | Immediate Win. |
| **3 in a Row + Empty** | `+5` points | Setting up a win. |
| **2 in a Row + Empties** | `+2` points | Early game development. |
| **Opponent 3 in a Row** | `-4` points | **Defensive Priority:** Block the player immediately. |
| **Center Column** | `+3` points per piece | **Strategy:** Controlling the center offers more winning lines. |

## 🛠️ Installation & Setup

### Prerequisites
Ensure you have Python installed. You will need the `pygame` and `numpy` libraries.


***

## 🕹️ Controls
- Mouse Movement: Move your cursor horizontally across the top of the window to position your piece.

- Left Click: Drop your piece into the selected column.

- Wait: Wait for the AI to calculate and make its move.

*** 

## 📂 Project Structure
- connect4_ai.py: Contains the main game loop, Pygame rendering, and the Minimax class structure.

- create_board(): Initializes the 6x7 NumPy matrix.

- minimax(): The recursive algorithm driving the AI.

- score_position(): The heuristic function that evaluates board states.

***

### 🚀 Future Improvements
- Add a "Difficulty Select" menu (changing the MAX_DEPTH variable).

- Add a "Restart" button after the game ends.
