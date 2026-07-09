# The Cosmic Web Sandbox

An interactive, in-browser cosmic web you can reshape by dragging cosmological
dials. The full physics pipeline runs client-side — Gaussian white-noise field,
FFTs, Lagrangian perturbation theory, Eisenstein–Hu (1998) transfer function,
and a GPU shader — so the controls respond in real time on a 250 Mpc/h box with
a **fixed random seed** (matched phases), letting you compare *physics* rather
than *realizations*.

## Running it

Open `index.html` in any modern browser. No build step, server, or internet
connection is required — Three.js is bundled inline, so the page is fully
self-contained and works offline.

**Navigation:** drag to rotate · scroll or pinch to zoom. On narrow screens the
control panel collapses behind a **Controls** button.

## Control panel

The panel on the right is grouped into the sections below. Buttons highlighted
in amber are the currently active choice.

### Universe ingredients

The three primary cosmological parameters. Changing Ωm or nₛ rebuilds the field
(with a smooth morph between the old and new structure); σ₈ is applied live in
the shader.

| Setting | Symbol | Range | Default | Effect |
|---------|--------|-------|---------|--------|
| Matter density | Ωₘ | 0.10 – 0.60 | 0.315 | More matter → stronger gravity, more small-scale structure |
| Clumpiness | σ₈ | 0.30 – 1.50 | 0.811 | Amplitude of fluctuations — smooth sea vs. dense knots |
| Spectral tilt | nₛ | 0.70 – 1.30 | 0.965 | < 1 favours large structures, > 1 favours small ones |

### Views

How the box is rendered and which tracers are overlaid.

- **Splats** — default point-cloud render of the matter field, colored by
  Jacobian (single-stream) density so caustics light up.
- **Clouds** — volumetric ray-marched rendering of the same field.
- **Density / Web type colors** — how the splats are colored. *Density colors*
  follows the local (single-stream) density. *Web type colors* classifies each
  particle by how many axes of its deformation tensor are gravitationally
  collapsing (a T-web-style eigenvalue threshold): 0 = void (dark),
  1 = **sheet** (green), 2 = **filament** (blue), 3 = **node** (orange).
  Combined with *Grow the universe* this shows the anisotropic-collapse
  sequence sheets → filaments → nodes explicitly.
- **Matter 2D slice (inset)** — toggles a 2D column-density inset (top-left).
- **Halos** — overlays proxy halos (density peaks).
- **Galaxies (HOD)** — overlays galaxies populated from halos via the
  Zheng et al. (2004) Halo Occupation Distribution model (cluster-scale here).
- **Box boundary** — toggles the wireframe outline of the periodic box.

HOD parameters (used by the Halos / Galaxies overlays):

| Setting | Symbol | Range | Default | Effect |
|---------|--------|-------|---------|--------|
| HOD minimum mass | log Mₘᵢₙ | 13.0 – 14.8 | 13.5 | Halo mass threshold for hosting a central galaxy |
| HOD satellite mass | log M₁ | 13.8 – 16.0 | 15.6 | Mass scale for hosting one satellite galaxy |
| Satellite slope | α | 0.4 – 2.0 | 1.6 | Power-law slope of the satellite count vs. halo mass |

### Power spectrum

Toggles that measure P(k) directly from the box (dots) and overlay it on the
linear input spectrum (line). Halos and galaxies show bias and shot noise
relative to the matter field.

- **Matter** — measured matter P(k).
- **Halos** — measured halo P(k).
- **Galaxies** — measured galaxy P(k).

### Cosmic time

- **Scale factor a** — slider over `0.05 – 1.0` (default `1.0`). Sets the epoch;
  the redshift `z = 1/a − 1` is shown beneath the slider. Growth is applied live.
- **Grow the universe** — plays the structure-formation animation forward in
  cosmic time; toggles to **Pause** while running. While it plays, the 2D
  matter slice, halo/galaxy overlays, volume render, and measured P(k) all
  update live, so the insets grow together with the box (a full-quality pass
  runs when the animation pauses or finishes).

### Cosmology presets

One-click parameter sets for Ωₘ, σ₈, nₛ:

| Preset | Ωₘ | σ₈ | nₛ |
|--------|----|----|----|
| Planck 2018 | 0.315 | 0.811 | 0.965 |
| Matter-heavy | 0.550 | 0.811 | 0.965 |
| Smooth | 0.315 | 0.450 | 0.965 |
| Blue tilt | 0.315 | 0.811 | 1.250 |

### Simulation configurations

Controls for how the field is computed and viewed.

- **1LPT / 2LPT** — Lagrangian perturbation theory order. 1LPT is the Zel'dovich
  approximation; 2LPT adds the second-order term, sharpening filaments and knots
  (closer to a full N-body result).
- **Real space / x LOS / y LOS / z LOS** — redshift-space distortions. Real space
  is undistorted; the LOS options place the line of sight along the chosen axis,
  stretching structure with redshift-space (Kaiser) infall.
- **New realization** — re-seeds the random phases to draw a different universe.
- **Resolution** — particle grid size: `32³` (fast), `64³` (default),
  `128³` (slow, desktop).

## Insets and readouts

- **Power spectrum P(k)** (bottom-left, always visible) — the linear input P(k)
  for the current cosmology; the Power-spectrum toggles overlay the measured P(k)
  from the box on top of it.
- **Matter column density** slice (top-left) appears when toggled from the
  panel. It is contrast-stretched between percentiles of the column density
  (rather than normalized to the brightest cluster pixel), so filaments and
  sheets stay visible, and it animates during *Grow the universe*.
- On narrow screens the insets and footer are hidden; only the collapsible
  **Controls** panel is shown.
- The footer reports the box size, particle count, and approximate mass per point.

## Physics references

Lagrangian perturbation theory (1LPT / 2LPT) · Eisenstein–Hu (1998) transfer
function · flat ΛCDM growth factor (Carroll et al. 1992) · Zheng et al. (2004)
HOD model. Inspired by the Planck CMB Simulator and the AbacusSummit
*Many Universes* movie.
