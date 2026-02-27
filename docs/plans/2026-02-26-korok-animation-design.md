# Korok Slide-In Animation Design

## Summary

Add a Korok character image that slides in from a random screen edge when the player answers a question. Happy Korok on correct answers, sad Korok on wrong answers, synced with the existing sound effects.

## Images

- `korok-happy.png` — transparent PNG, happy expression, ~120-150px
- `korok-sad.png` — transparent PNG, sad/hurt expression, ~120-150px
- Sourced from Zelda fan resources

## Animation

1. Player answers a question
2. Korok image slides in from a random edge (left, right, or bottom) over ~300ms
3. Stays visible for ~1.5 seconds (synced with sound)
4. Slides back out over ~300ms

## Implementation

**HTML**: Single `<img id="korok">` element, fixed position, hidden by default.

**CSS**: Fixed positioning with `transition: transform 0.3s ease-out`. Three directional classes (`from-left`, `from-right`, `from-bottom`) control the off-screen starting position via `translateX`/`translateY`. An `active` class triggers the slide to visible position.

**JS**: `showKorok(type)` function called from `selectAnswer()` after playing sound. Sets the image src, picks a random direction class, adds `active` to slide in, then uses `setTimeout` to remove `active` and slide out.
