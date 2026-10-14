# Galaxy Sizes & Shapes

A looping lecture animation (16:9, ~56 s cycle) with an explore mode. It shows
how galaxy **intrinsic shapes** (spin-2) and **intrinsic sizes** (spin-0) are
imprinted by the dark-matter web through its tidal field and density. It then
shows how **primordial non-Gaussianity** (PNG) adds a scale-dependent term to
each response:

- **local f_NL** reaches sizes (and counts);
- **directional (spin-2) f_NL**, written f_NL^(s=2), reaches shapes.

The two are separated by symmetry. Both grow as 1/[k²T(k)] on the largest scales.

## Using it

- Open `index.html` in any modern browser. It is a single self-contained file
  with no build step and no network access needed; a 2 Gpc/h universe is built
  in about a second on load.
- **Click** the map or press **Space** to pause. Pausing opens **explore mode**:
  - sliders for local f_NL, spin-2 f_NL, tidal-alignment strength, size–density
    response and zoom;
  - layer toggles;
  - drag to pan, scroll to zoom, *New universe* to re-seed.

  *Resume* returns to the narrative.
- **← / →** scrub by one second; drag the timeline to seek.
- **N** toggles between plain captions and research **notation**: equations,
  k in h/Mpc, bias symbols. **F** toggles fullscreen.
- URL parameters:

  | Parameter | Effect |
  |-----------|--------|
  | `?t=SECONDS` | start at that time |
  | `&pause=1` | frozen still for slides; clicks do nothing |
  | `&notation=1` | start in notation mode |
  | `&explore=1` | open paused in explore mode |
  | `&seed=N` | a different realization |

  Example: `index.html?t=19.5&pause=1&notation=1`.

## Scenes

| t (s) | scene | what changes |
|-------|-------|--------------|
| 0     | The dark-matter web | Zel'dovich web of a 2 Gpc/h slice; zoom toward the densest node near the centre |
| 7.2   | Its tidal field | headless streamlines along the stretching direction of K_ij |
| 13.4  | Galaxies feel the tide | ellipticals align: along filaments, radial around the cluster (on average) |
| 20.2  | …and their sizes feel the density, weakly | weak positive size–density response; galaxies tinted by size (amber larger, faint grey-violet smaller); zoom out |
| 26.6  | A local imprint changes sizes | local f_NL = 25 (above current limits, for visibility): sizes shrink where the long-wavelength φ is high (solid contours; b_φᴿ < 0); counts and sizes split in the plot |
| 38.0  | A directional imprint turns shapes | f_NL^(s=2) = 100: orientations follow the stretch pattern ψ_ij of φ; only the spin-2 curve moves |
| 49.4  | Two windows on inflation | both imprints on; fade and loop |

## Model

- **Slice.** A 2D slice, L = 2000 Mpc/h, on a 512² grid with Planck 2018
  parameters.
- **Primordial potential.** φ has P_φ(k) ∝ k^(n_s−3), the scale-invariant spectrum
  of a thin slice through a 3D field. Its sign follows +(3/5)ζ, so φ is positive
  in wells.
- **Density.** δ(k) = α(k) φ(k), with α(k) = 2k²T(k)D(z)/(3Ω_m H₀²) (c = 1,
  D = a during matter domination, EH98 transfer function).
- **Web.** Truncated Zel'dovich displacement (Gaussian cut at 5.5 Mpc/h) gives the web. The density image is
  rendered from 3×3 sub-particles per cell.
- **Tidal field.** It comes from the evolved density smoothed at 9 Mpc/h, the
  field-level analogue of NLA, so streamlines and galaxies agree where galaxies sit. Only the
  in-plane trace-free components are drawn: (K₁₁−K₂₂)/2 and K₁₂. The 3D trace
  convention (⅓δ_ij on screen) therefore does not affect what is drawn.
- **ψ_ij.** Uses the same operator on the long-wavelength φ, smoothed at
  40 Mpc/h, which keeps k ≪ k_galaxy as the peak–background split requires.
- **Galaxies.** Positions are frozen and drawn by biased sampling of displaced
  sub-particles. Their responses are:

  ```
  e      = e_rand − A_K K̃ − A_ψ (f_NL^(s=2)/100) ψ̃          (b_K < 0: long axis ∥ stretch)
  ln R   = s_rand + A_s [ln(1+δ_s)]̃ − A_φ (f_NL/25) φ̃        (b₁ᴿ > 0 small, b_φᴿ < 0)
  ```

  Here ˜ marks fields normalised to unit rms. The size term uses the
  log-density, which equals δ_s at linear order (so it still maps to b₁ᴿ δ) and
  keeps cluster galaxies from blowing up. The explore-mode alignment slider
  scales both spin-2 terms together. Ellipses keep their area as they stretch,
  so size and shape are independent.
- **Response plot.** One panel per spin, with b(k) = b + b_φ f / α(k) and
  illustrative biases:
  - counts: b₁ = 2, b_φ = 2δ_c(b₁ − 1);
  - sizes: b₁ᴿ = 0.3, b_φᴿ = −3;
  - shapes: b_K(k)/b_K with b_ψ = b_K.

  The shaded band marks the scales inside the current view, so zooming out shows
  the slice reaching the scales where the PNG terms live.

## What is exaggerated (and what is not)

- **The map is a cartoon of amplitudes.**
  - Real intrinsic alignments are ~1% (a few % for luminous red galaxies)
    against ~25% shape noise. Here they are drawn about 30× too strong.
  - PNG-induced per-galaxy size or shape shifts are ≲10⁻³ for allowed f_NL.
    Here they are about 10³× too strong.
- **The spatial structure is not a cartoon.**
  - The PNG terms follow φ and ψ_ij. Physically these are smoother than δ and
    K_ij by 1/α(k). Here φ is also smoothed at 40 Mpc/h (δ and K_ij at 9 Mpc/h),
    so only its long-wavelength part is drawn.
  - The plot uses the physical α(k) with the bias values above. The narrative
    local f_NL = 25 is about 5σ above the Planck limit, chosen so the upturn is
    visible. f_NL^(s=2) = 100 lies within the current BOSS bound.
- **Positions are frozen**, so you see only the size and shape responses. In
  reality local f_NL also shifts galaxy counts (Dalal et al. 2008). The dashed
  "counts" curve shows that.
- **Size response.** b₁ᴿ is kept small but positive so sizes visibly trace the
  web. For galaxy-mass halos the linear size–density bias is close to zero and
  b_φᴿ is sizable and negative (Nguyen, Akitsu & Taruya 2026).
- **Spin-2 PNG.** A box-wide coherent tilt would need modes larger than the
  slice. Its amplitude depends on the unknown superhorizon history (Schmidt,
  Chisari & Dvorkin 2015), so it is not drawn.

## References

**Alignments and the tidal field**
- Catelan, Kamionkowski & Blandford 2001, astro-ph/0005470
- Hirata & Seljak 2004, astro-ph/0406275
- Bridle & King 2007, arXiv:0705.0166
- Blazek, Vlah & Seljak 2015, arXiv:1504.02510
- Vlah, Chisari & Schmidt 2020, arXiv:1910.08085

**Local f_NL and scale-dependent bias**
- Dalal et al. 2008, arXiv:0710.4560
- Slosar et al. 2008, arXiv:0805.3580
- Barreira et al. 2020, arXiv:2006.09368

**Sizes**
- Ciarlariello, Crittenden & Pace 2015, arXiv:1412.4606
- Nguyen, Akitsu & Taruya 2026, *Galaxy sizes as complementary (zero-)bias
  tracers of local primordial non-Gaussianity*, arXiv:2603.20196

**Spin-2 PNG and shapes**
- Schmidt, Chisari & Dvorkin 2015, arXiv:1506.02671
- Chisari et al. 2016, arXiv:1607.05232
- Akitsu et al. 2021, arXiv:2007.03670
- Kurita & Takada 2023 (BOSS DR12: f_NL^(s=2) = −67 +285/−269), arXiv:2302.02925

**Constraints**
- Planck 2018 IX (f_NL^loc = −0.9 ± 5.1), arXiv:1905.05697
