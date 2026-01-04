# Teeko Minimax AI Player

A lightweight AI player for the Teeko board game implemented in Python. The agent uses a depth-limited minimax search with a simple heuristic evaluation function and supports both the drop phase and move phase.

## What This Project Does

- Implements a playable Teeko agent that chooses moves via minimax search
- Handles both phases of the game:
  1) Drop phase: place pieces until 8 pieces are on the board
  2) Move phase: relocate pieces to adjacent squares
- Provides a text-based interactive CLI so a human can play against the AI
- Includes win-condition checks for lines and 2x2 boxes

## Rules Summary

Board: 5x5 grid
Pieces: two colors (b, r)
Phases:
- Drop phase (first 8 total placements): players alternate placing pieces on empty squares
- Move phase (after 8 pieces placed): players move one of their pieces to an adjacent empty square (8-neighborhood)

Win conditions (4-in-a-row or 2x2 box):
- Any 4 contiguous pieces in a row (horizontal)
- Any 4 contiguous pieces in a column (vertical)
- Any 4 contiguous pieces in a diagonal
- Any 2x2 box containing 4 of the same piece

## Repository Structure

.
`-- teeko_player.py    # Teeko AI agent + interactive CLI (rename your file to this if desired)

If your file currently has a different name, you can keep it as-is. The commands below assume the file is named `teeko_player.py`.

## Requirements

```text
Python 3.8+ (no external dependencies)
```

## How To Run

```text
python teeko_player.py
```

## How To Play (CLI)

- The game prints a 5x5 board with row indices 0-4 and columns A-E
- During your turn, input coordinates in the form "B3", "A0", "E4"
- In move phase, you will be prompted for:
  - Move from: where your piece currently is (e.g., B3)
  - Move to: adjacent empty destination (e.g., C4)

## AI Approach

Search:
- Depth-limited minimax with max depth = 3 (configurable via TeekoPlayer.max_depth)
- Successor generation depends on phase:
  - Drop phase: place a piece on any empty cell
  - Move phase: move any of your pieces to any adjacent empty cell

Evaluation:
- If the state is terminal (win/loss), return +/- 1
- Otherwise, return a heuristic score for non-terminal states

## Implementation Notes

Key methods:
- make_move(state): selects the best next move for the AI
- succ(state, piece): generates legal successor states for a given piece
- game_value(state): checks win conditions and returns {1, -1, 0}
- heuristic_game_value(state): returns heuristic score for non-terminal states
- max_value(state, depth): minimax recursion over alternating turns

## Configuration

```text
To change search depth:
- Edit TeekoPlayer.max_depth (default: 3)

To change heuristic:
- Edit heuristic_game_value(state)
```

## Example Output (Abbreviated)

```text
Hello, this is Samaritan
0:       ...
1:       ...
2:       ...
3:       ...
4:       ...
   A B C D E

Move (e.g. B3): B3
...
```

## License

```text
MIT
```
