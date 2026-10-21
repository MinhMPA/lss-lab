# lss-lab

Visualization and animation tools for **large-scale structure** (LSS) — both
cosmological simulations and observational data such as galaxy surveys.

The goal is a small, self-contained collection of interactive tools that make
the physics of the cosmic web tangible: how structure grows under gravity, how
it responds to cosmological parameters, and how it appears in real vs. redshift
space.

## Tools

- **[cosmic-web-sandbox](cosmic-web-sandbox/)** — *The Cosmic Web Sandbox*, an
  interactive, in-browser cosmic web you reshape with cosmological dials. The
  whole physics pipeline runs client-side, so the controls respond in real time.
  Open `cosmic-web-sandbox/index.html` in a browser; no build step required.
  See its [README](cosmic-web-sandbox/README.md) for details.

- **[galaxy-sizes-and-shapes](galaxy-sizes-and-shapes/)** — *Galaxy Sizes &
  Shapes*, a looping lecture animation with an explore mode. Galaxy shapes
  align with the tidal field of the cosmic web and their sizes follow its
  density; then primordial non-Gaussianity adds scale-dependent responses, a
  local imprint to sizes and a directional one to shapes. Switch either
  observable off to watch the other alone. Open
  `galaxy-sizes-and-shapes/index.html`; no build step required. See its
  [README](galaxy-sizes-and-shapes/README.md) for the model and references.

- **[sampling-for-bayesian-inference](sampling-for-bayesian-inference/)** —
  *Sampling for Bayesian Inference*, interactive demonstrations for the talk
  "The Last 70 Years (and the Next 10) of Sampling". Importance nested sampling
  with frozen prior-volume shells, then a replay of an actual Nautilus run
  showing how its neural network learns proposal regions while the weights
  still use the true likelihood. Preview; more samplers to come. Built with
  Vite from a separate source repository and served over HTTP (it loads JSON
  traces, so it does not open from `file://`). See its
  [README](sampling-for-bayesian-inference/README.md).

## License

TBD.
