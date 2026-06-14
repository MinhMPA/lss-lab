# lss-lab

Visualization and animation tools for **large-scale structure** (LSS) — both
cosmological simulations and observational data such as galaxy surveys.

The aim is a small, self-contained collection of interactive tools that make the
physics of the cosmic web tangible: how structure grows under gravity, how it
responds to cosmological parameters, and how it appears in real vs. redshift
space.

## Tools

### cosmic-web-sandbox

**The Tunable Universe** — an interactive, in-browser cosmic web you can reshape
by dragging cosmological dials. The entire physics pipeline runs client-side
(Gaussian field generation, FFTs, Lagrangian perturbation theory, and a GPU
shader), so the sliders respond in real time.

Highlights:

- Tune matter density Ω<sub>m</sub>, clumpiness σ<sub>8</sub>, and spectral
  tilt n<sub>s</sub> with a fixed random seed (matched phases), so you compare
  *physics*, not *realizations*.
- 1LPT (Zel'dovich) and 2LPT displacement models with smooth morph transitions.
- Eisenstein–Hu (1998) no-wiggle transfer function, flat ΛCDM growth factor,
  and a Jacobian (single-stream) density coloring that lights up caustics.
- Cosmic-time playback over the scale factor *a*, redshift-space distortions
  (Kaiser), proxy halos and a Zheng et al. (2004) HOD galaxy model.
- Live measured power spectrum P(k) for matter, halos, and galaxies vs. the
  linear input, plus 2D slice and 2D P(k) insets.

Inspired by the Planck CMB Simulator and the AbacusSummit *Many Universes*
movie.

**Run it:** open `cosmic-web-sandbox/index.html` in any modern browser — no
build step or server required (Three.js loads from a CDN).

## License

TBD.
