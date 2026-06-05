# Triangle Territory

## Run

This game must be served over HTTP because it loads board files with `fetch()`.

From the repo root:

```bash
python3 -m http.server 8765
```

Then open:

```text
http://localhost:8765/src/index.html
```

## Add New Boards

1. Put a new SVG in `boards/`.
2. Keep the same outer triangle size and `viewBox` as the existing board.
3. Make the divider lines available as `<line>` elements.
4. Add the board to `boards/boards.json`:

```json
{
  "id": "triangle-2",
  "name": "Triangle 2",
  "file": "triangle-2.svg"
}
```

The game reads divider lines from `line.inner-line` if present, otherwise it uses all `<line>` elements in the SVG.

## How To Play

- Three players take turns claiming cells.
- On your turn, click one highlighted frontier cell.
- A frontier cell is any unclaimed cell adjacent to one of your owned cells.
- If your move encloses neutral cells, those cells are captured automatically.
- The game ends when no valid moves remain or the board is full.
- Highest cell count wins.
