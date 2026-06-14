# Galaxy Size — LSS Correlation Explorer

An interactive, in-browser toy model of how **member-galaxy sizes inside
dark-matter host halos correlate with their large-scale environment** — the
cosmic-web gravitational potential well and the matter density perturbation
field. The whole pipeline runs client-side on a 2D canvas, so every control
responds in real time.

This is the size analog of *intrinsic alignments*: just as galaxy shapes are
weakly aligned by the large-scale tidal field, galaxy sizes carry a coherent
correlation with their environment. That signal is both a probe of
galaxy–halo physics and a contaminant for weak-lensing **magnification**
measurements.

## Running it

Open `index.html` in any modern browser. No build step, server, or internet
connection is required — everything (Canvas 2D, no external libraries) is in
the single file and works offline. Fonts load from Google Fonts when online
and fall back to system fonts otherwise.

**Interaction:** click any halo to make it the **host** and highlight its
member galaxies (in both the field view and the scatter plot). On narrow
screens the control panel collapses behind a **Controls** button.

## What you are looking at

- **Background heatmap** — the large-scale field, either the gravitational
  **potential well depth −Φ** (warm = deep wells) or the **density
  perturbation δ** (warm = overdense). The field is built from a handful of
  Fourier modes; the potential follows from Poisson's equation
  (Φₖ = −δₖ / k²), which suppresses small scales so Φ is dominated by the
  largest structures — the cosmic-web nodes.
- **Halo disks** — translucent circles mark host dark-matter halos, placed by
  environment-biased sampling so they cluster in overdense regions. Disk
  radius scales with halo mass. The selected **host** halo is outlined in
  amber.
- **Galaxies** — ellipses orbiting inside each halo, **colored and sized by
  their modeled physical size** (cyan = small, amber = large).
- **Scatter inset** (bottom-left) — galaxy size vs. the chosen large-scale
  field value, one point per galaxy, with a best-fit line. Host-halo members
  are emphasized. The Pearson correlation coefficients r(size, −Φ) and
  r(size, δ) are reported live.

## The size model

Each galaxy's size is drawn log-normally and coupled to its host halo's
large-scale environment plus a within-halo term:

```
log R = log R₀ + b_Φ · ŵ + b_δ · δ̂ − tidal · f(r/r_vir) + σ · ξ
```

- **ŵ** — host halo's large-scale potential-well depth (−Φ), as a z-score.
- **δ̂** — host halo's large-scale overdensity, as a z-score.
- **b_Φ, b_δ** — the couplings you set with the sliders (can be negative).
- **tidal · f(r/r_vir)** — tidal truncation: galaxies deeper inside the halo
  potential are stripped and so appear smaller.
- **σ · ξ** — log-normal intrinsic scatter (ξ is a fixed per-galaxy Gaussian
  draw, so moving the sliders re-mixes the same population smoothly).

## Control panel

### Large-scale field

| Control | Effect |
|---------|--------|
| **−Φ / δ** | Choose which field is shown as the background heatmap |
| Field amplitude | Contrast of the heatmap (display only) |
| Large-scale tilt | Spectral slope; more negative favors large-scale structure |
| New realization | Re-seeds the random phases — a different universe |
| Contours | Toggle iso-contours of the displayed field |

### Size – environment coupling

| Control | Effect |
|---------|--------|
| Potential-well coupling `b_Φ` | How strongly size tracks well depth |
| Density coupling `b_δ` | How strongly size tracks overdensity |
| Tidal truncation | Strength of central truncation within each halo |
| Intrinsic scatter | Log-normal size scatter at fixed environment |

### Halos & galaxies

| Control | Effect |
|---------|--------|
| Host halos | Number of host halos placed |
| Members / halo | Member galaxies per halo |
| Size exaggeration | Visual size scaling (display only) |
| Orbits | Animate members orbiting their halo |
| Halo disks | Show/hide the translucent halo disks |

### Scatter plot x-axis

Plot size against the background field (**Match background**), or pin it to
**−Φ** or **δ**.

## Try this

- Set both couplings to zero, then raise **Potential-well coupling** and watch
  r(size, −Φ) climb while the scatter cloud tilts into a line.
- Crank **Intrinsic scatter** to see how easily a real correlation hides in
  noise.
- Flip a coupling negative to model a regime where dense environments host
  *smaller* galaxies (e.g., strong tidal stripping / ram-pressure).
- Note that −Φ and δ are themselves correlated, so coupling to one induces a
  weaker correlation with the other — exactly the degeneracy that complicates
  real measurements.

## Physics references

Poisson's equation for the peculiar potential · environment-dependent galaxy
sizes and intrinsic *size* correlations (the size analog of intrinsic
alignments) · weak-lensing magnification and its size–density contaminant ·
tidal truncation of satellites in host halos.
