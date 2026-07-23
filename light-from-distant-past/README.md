# Light from the Distant Past

A minimalist looping animation (16:9, ~33 s cycle) for public cosmology
lectures: one continuous zoom from Earth at night out to the cosmic
microwave background, with a synchronized distance / lookback-time
indicator. No narration, no sound.

**Looking farther into space is looking farther back in time.**

## Using it in a lecture

- Open `index.html` in any modern browser — a single self-contained file,
  no build step, no network. Fullscreen the window and let it loop.
- **Click** (or **Space**) pauses / resumes.
- **Drag horizontally** or press **← / →** to scrub the timeline
  (the loop itself only ever runs outward).
- `?t=SECONDS` starts at that point in the cycle; add `&pause=1` for a
  frozen still, e.g. `index.html?t=30.6&pause=1` for the CMB finale —
  handy for slides.

## Scenes (approximate loop time)

| t (s)  | scene                        | lookback readout          |
|--------|------------------------------|---------------------------|
| 0–3    | Earth at night               | now                       |
| 3–5    | Moon orbit                   | seconds                   |
| 6–7    | the Sun, 8 light-minutes away| ~8 minutes                |
| 8–9    | full Solar System            | hours                     |
| 12–14  | Milky Way                    | tens of thousands of years|
| 17–18  | Local Group, Andromeda       | millions of years         |
| 20–21  | nearby cosmic web            | hundreds of millions      |
| 23–25  | galaxy-survey wedge          | billions                  |
| 27–28  | young galaxies and quasars   | > 12 billion years        |
| 29–32  | cosmic microwave background  | 13.8 billion years        |

## Notes on the visualization

- The world unit is the light-second, and all distances are light-travel
  distances — so the distance and lookback-time readouts are literally the
  same number in two units. That identity is the point of the piece.
- It is a map of what we observe, not a faster-than-light flight. Earth
  sits at the frame centre only because every observer sits at the centre
  of their own observable universe.
- The cosmic web is a seeded Voronoi-foam toy model — galaxies on the
  walls and filaments between void cells, clusters where cells meet — and
  the survey wedge echoes DESI/PFS-style fan plots. Distant galaxies are
  drawn smaller, sparser, clumpier and slightly warmer.
- Galaxy symbols in the Local Group scene are gently enlarged (~2×) for
  legibility; positions and every HUD number stay to scale.
- The CMB ring is the earliest light we can observe, not a physical wall,
  and nothing here shows the Universe expanding "into" anything.
