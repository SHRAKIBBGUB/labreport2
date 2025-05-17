
# Iterative Deepening DFS (IDDFS) Maze Solver

This Python program implements **Iterative Deepening Depth-First Search (IDDFS)** to find a path from a start to a target cell in a 2D maze.

## 📌 Description

* The maze is a grid where:

  * `0` = free path
  * `1` = wall/block
* Input is taken from the user for:

  1. Maze size (`rows cols`)
  2. Maze matrix (0s and 1s)
  3. Start position (`x y`)
  4. Target position (`x y`)
* The algorithm uses **depth-limited DFS**, increasing the depth limit until the target is found or the maximum possible depth is reached.

## ✅ Sample Input

```
5 5
0 0 1 0 0
1 0 1 0 1
0 0 0 0 0
1 1 1 1 0
0 0 0 1 0
0 0
4 4
```

## ▶️ How to Run

```bash
python iddfs_maze_solver.py
```

Follow the prompts to input maze dimensions, the maze, and start/target coordinates.

## 🧠 Key Components

* `depth_limited_search(current, visited, depth)`: Recursively explores paths up to a given depth.
* `iterative_deepening()`: Increases depth limit until the goal is found.
* `read_input()`: Reads input from the user (maze + start and target).

## 📤 Output Example

```
Path found at depth 12 using IDDFS
Traversal Order: [(0, 0), (0, 1), (1, 1), (2, 1), (2, 0), (2, 2), (2, 3), (1, 3), (0, 3), (0, 4), (1, 4), (2, 4), (3, 4), (4, 4)]
```

## ❗ Error Handling

* If the input format is incorrect, it prints:

  ```
  Wrong Input format
  ```



