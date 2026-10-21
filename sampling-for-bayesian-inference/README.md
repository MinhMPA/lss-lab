# Sampling for Bayesian Inference

Interactive demonstrations for the talk *The Last 70 Years (and the Next 10)
of Sampling* (IPMU/CD3 Numerics Forum, 16:9 projection). Every module uses the
same synthetic inverse problem: a signal amplitude `a` measured with an
uncertain background `b`, observed through a signal channel and a calibration
channel. A linear response gives a correlated Gaussian posterior. A quadratic
response gives a curved ridge (`B-curved`) or two separated solutions with
opposite signs of `a` (`B-separated`).

**Status: preview.** This build contains two modules:

1. **INS: frozen shells.** Importance nested sampling as a stratified estimator,
   Ẑ = Σᵢ Vᵢ · mean(L)ᵢ. Fresh samples are drawn in disjoint prior-volume shells
   and weighted by L·Vᵢ/Nᵢ. The shell volumes come from an independent
   geometry-only random stream. This is a pedagogical construction, labelled
   "Nautilus-inspired".
2. **Nautilus: learned proposals.** A replay of an *actual* Nautilus 1.0.6 run.
   One neural bound is frozen and shown in six steps:
   1. the evaluated points;
   2. the enclosing ellipsoid;
   3. local coordinates and the split-rank score targets;
   4. the regression, including the calibrated cut (which is not 0.5);
   5. the learned proposal region;
   6. candidates filtered by the network before any true-likelihood call.

   Posterior and evidence use the true likelihood with Nautilus's own importance
   weights. *Learn where to propose; evaluate what is true.*

Modules on importance sampling, random-walk Metropolis vs HMC, classical
nested sampling, a hierarchical funnel and research frontiers will be added.

## Using it

- The page loads its data (`traces/*.json`) over HTTP. Use it from GitHub Pages,
  or locally with `python3 -m http.server` in this folder. It does not work from
  `file://`. No other network access is needed: fonts and KaTeX are bundled.
- Keys:
  - **Space**: play/pause.
  - **← / →**: one recorded event back or forward.
  - **PageUp / PageDown**: previous or next storyboard beat; works with
    presentation clickers.
  - **R**: reset.
  - **1–3**: switch modules.
  - **E**: expert view, which includes the proposal-only cut-sensitivity view
    and the `n_networks` 4-vs-0 comparison.
  - **M**: math captions.
  - **T**: dark theme.
- The stage is a fixed 1280×720 logical canvas, scaled to fit any 16:9 screen.

## What the numbers are

Nothing on screen is computed in the browser. Each panel reads values stored in
versioned traces produced by Python (NumPy/SciPy, `nautilus-sampler` 1.0.6).
Each trace carries:
- its settings and seeds;
- separate counters for likelihood calls, neural predictions, geometric
  candidates and training operations;
- validity flags;
- a content hash.

Reference values (analytic or 1-D quadrature) are used only for validation and
for overlays labelled "reference"; they never enter a sampler or a training set.
Multi-seed validation (20 seeds, with 100-seed confirmations) is summarized in
the source repository.

The model is a teaching toy, not a cosmological likelihood. A two-dimensional
demonstration says nothing about high-dimensional scaling.

## Source

Built from `web/` of the
[CD3NumericsForum sampling-for-Bayesian-inference](https://github.com/IPMUCD3/CD3NumericsForum_sampling-for-Bayesian-inference)
project (React + TypeScript + Vite; `npm run build`, then copy `dist/` here).
That repository holds:
- the specification;
- the trace generators;
- the scientific tests and validation reports;
- the design notes (`docs/design-decisions.md`).

## References

- J. U. Lange (2023), *Nautilus: boosting Bayesian importance nested sampling
  with deep learning*, MNRAS 525, 3181; arXiv:2306.16923.
- J. Skilling (2004), *Nested Sampling*, AIP Conf. Proc. 735, 395.
- F. Feroz, M. P. Hobson, E. Cameron, A. N. Pettitt (2019), *Importance Nested
  Sampling and the MultiNest Algorithm*, OJAp 2, 10; arXiv:1306.2144.
- Nautilus documentation: <https://nautilus-sampler.readthedocs.io/>
