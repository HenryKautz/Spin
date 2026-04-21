# Project: Spin

A single-page spinner wheel web app for randomly picking a student to
call on in CS 6501 (Agents) at UVA.

## Structure

- `index.html` — the entire app: HTML, CSS, and vanilla JS in one file.
  No build, no dependencies, no server. Open it directly in a browser.
- `README.md` — user-facing usage instructions.

## Conventions

- Keep everything in `index.html`. Do not introduce a build step,
  framework, or external assets unless asked.
- Audio is synthesized via Web Audio API — do not add sound files.
- The default roster lives in the `DEFAULT_NAMES` array near the top of
  the `<script>` block. Edit it there to change the class list.

## Key implementation details

- Pointer is fixed at the 3 o'clock position; the winning segment ends
  horizontal so the name is easy to read.
- `segmentUnderPointer(rot)` is the source of truth for which segment
  the pointer is over at any rotation.
- Spin algorithm: pick target from active segments first, compute the
  final rotation that lands inside it (random 10–90% offset within the
  segment), add 6–10 full revolutions, then animate with
  `easeOutQuart` over a random 10–20 s.
- Inactive (already-picked) segments stay drawn as gray and are
  excluded from target selection — the wheel still has the same number
  of physical slices.
