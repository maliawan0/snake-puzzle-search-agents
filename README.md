# Snake Puzzle — Search Agent Comparison

Implementation and empirical comparison of classical search algorithms solving the Snake puzzle across maze maps with walls. Built for the Artificial Intelligence course at FAST-NUCES.

## The problem

The snake must reach food while avoiding walls and its own body. Each move changes the state — the body follows the head — so the search space is over *snake configurations*, not just grid positions. That makes naive breadth-first search expensive fast, which is the point of the comparison.

## Agents implemented

| Agent | Strategy |
|---|---|
| **A\*** | `f(n) = g(n) + h(n)` — optimal given an admissible heuristic |
| **Greedy Best-First** | `f(n) = h(n)` — fast, not optimal, can get trapped |
| **Uninformed baseline** | Explores without a heuristic, for comparison |

Heuristics are Manhattan-distance based, adjusted for wall layout.

## What's measured

Each agent runs across four maps of increasing difficulty (`Maze.txt`, `Maze0.txt`, `Maze1.txt`, `Maze2.txt`) and is compared on:

- Path length found (optimality)
- Nodes expanded (search effort)
- Whether a solution was found at all

The trade-off the experiment shows: A\* finds the shortest path but expands considerably more nodes; Greedy is quicker per solve but returns longer paths and fails on maps where the heuristic leads it into a dead end.

## Layout

```
main.py         # entry point — runs an agent on a chosen map
AgentSnake.py   # the search agents
State.py        # state representation and successor generation
View.py         # rendering
Maze*.txt       # four maps of increasing wall complexity
```

## Running it

```bash
python main.py
```

Select the agent and map inside `main.py`, or pass them at the prompt.

## Write-up

The full report — implementation notes and experimental results — is in [`AI_Assignement.docx`](AI_Assignement.docx).
