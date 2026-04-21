# Spin

A simple browser-based spinner wheel for picking a random name from a list,
with the picked name removed from future spins.

Built for use in CS 6501 (Agents) at UVA to randomly call on students.

## Usage

1. Open `index.html` in a browser. No build step, no server required.
2. The wheel loads with a default class roster (edit `DEFAULT_NAMES` in
   `index.html` to change it).
3. Click **LOAD** to paste a different list of names (one per line) and
   press **Apply**.
4. Click **SPIN**. The wheel animates for a random 10–20 seconds, easing
   to a stop with a clicking sound as each segment crosses the pointer.
5. The winning segment flashes white. Click **OKAY** to accept the
   winner — that segment turns gray and is excluded from future spins.
6. Repeat until everyone has been picked, or press **LOAD** to reset.

## Implementation notes

- Single-file HTML / vanilla JS, no dependencies.
- Wheel rendered on a `<canvas>`; segment colors are random HSL hues.
- Spin animation pre-picks a target from active segments, then computes
  a final rotation that lands inside it after 6–10 full revolutions,
  animated with `easeOutQuart`.
- Tick sound is synthesized via the Web Audio API (no audio assets).
- Pointer is fixed at the 3 o'clock position so the winning segment ends
  horizontal and easy to read.
