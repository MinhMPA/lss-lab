# Sampling for Bayesian Inference

Interactive demonstrations for the talk *The Last 70 Years (and the Next 10)
of Sampling* (IPMU/CD3 Numerics Forum, 16:9 projection). Every module uses the
same synthetic inverse problem: a signal amplitude `a` measured with an
uncertain background `b`, observed through a signal channel and a calibration
channel. A linear response gives a correlated Gaussian posterior. A quadratic
response gives a curved ridge (`B-curved`) or two separated solutions with
opposite signs of `a` (`B-separated`).

**Status: preview.** Each method is told as its key idea in three building
blocks plus one failure, one picture per clicker step. This build has two
modules:

1. **The inverse problem**: parameters predict data; many parameter pairs
   fit; projecting the posterior cloud widens the error bar (0.12 → 0.51).
2. **Learn where to propose** (importance nested sampling and Nautilus):
   - keep every evaluated point, weighted by its shell (a teaching demo);
   - a network learns the good region from an *actual* Nautilus 1.0.6 run;
   - candidates outside the region are rejected before any likelihood call;
   - failure: a hypothetical too-tight region leaves part of the ridge
     under-represented, because reweighting cannot create points that were
     never drawn.

Importance sampling, Metropolis, HMC, nested sampling and a closing "next
10 years" scene will be added in the same style.

## Using it

- The page loads its data (`traces/*.json`) over HTTP. Use it from GitHub Pages,
  or locally with `python3 -m http.server` in this folder. It does not work from
  `file://`. No other network access is needed: fonts and KaTeX are bundled.
- Each picture animates for a few seconds, then holds; titles are at most
  five words, and each module shows one number.
- Keys:
  - **PageDown / →**: next building block (it animates in place).
  - **PageUp / ←**: previous block.
  - **Space**: replay the current block.
  - **R**: back to the first block.
  - **Digits**: switch modules.
  - **E**: details overlay with the data behind the picture: trace label,
    settings, separate counters and diagnostics, and a note when the picture
    is a replay or hypothetical.
  - **N**: speaker notes.
  - **M**: formula.
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
