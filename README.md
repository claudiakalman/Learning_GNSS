# Learning GNSS

## PRN codes in GPS signal evaluation: interactive presentation

Open [`PRN_GPS_Signal_Evaluation.html`](PRN_GPS_Signal_Evaluation.html) in any modern browser. It is a single self-contained file; equations (MathJax) and fonts load from a CDN.

Navigate with ← / →, Space, or the bar at the bottom. Every plot is computed live in the browser from the real GPS L1 C/A codes, generated with the G1/G2 LFSRs and self-checked against IS-GPS-200. Sliders and selectors let you change parameters, and hovering a plot shows its values.

Each technical slide starts with an **"In plain words"** box (intuition and an analogy), then gives the math, then shows a figure or simulation.

| Part | Slides | Topics |
|---|---|---|
| Basics | 1–3 | Title, roadmap, GPS-as-a-timing-system and glossary |
| I. The signal | 4–6 | Power budget (signal below the noise), the three jobs of a PRN code, L1 C/A structure and BPSK |
| II. The code | 7–14 | LFSR generator (step it chip by chip), Gold codes and PRN table, balance and run lengths, correlation intuition, autocorrelation, correlation triangle, cross-correlation, spectrum |
| III. Spreading & despreading | 15–18 | Despreading demo, **processing gain**, interference rejection, received-signal model |
| IV. Acquisition | 19–22 | Code-phase × Doppler search, FFT acquisition, live search simulation, grid losses, detection theory (Rayleigh/Rice) |
| V. Tracking | 23–24 | DLL (Early/Prompt/Late, S-curves), Costas PLL and bit recovery |
| VI. Measurement & evaluation | 25–29 | Pseudorange, ranging precision, multipath error envelopes, C/N₀ estimation (NWPR) and signal-quality monitoring, modern codes |
| Summary | 30 | The PRN at every receiver stage |

## Adaptive antennas for GNSS: interactive presentation

Open [`Adaptive_Antennas_GNSS.html`](Adaptive_Antennas_GNSS.html) in any modern browser. It is one self-contained page that scrolls freely but is divided into 29 presentable sections (title plus 28 numbered). Use ← / → (or `n` / `p`, PageUp / PageDown) to jump between sections, Home / End for the first and last, `F` to toggle focus dimming of the sections not in view, and `M` for the section list. Every figure is computed live in the browser from the equations shown, and most are interactive: drag jammers and weight phasors, move sliders, pick presets, hover maps.

The file works **fully offline**: all 141 equations are pre-rendered to inline SVG with MathJax at build time (no MathJax script is loaded), and the Inter and JetBrains Mono fonts (Latin, Latin Extended and Greek) are embedded. It makes no network requests, so it is safe to present from a laptop without internet.

It starts from basic concepts (waves, phase, a single antenna, phasors), then builds a two-antenna array with an applied phase and its polar gain pattern, before moving on to full adaptive arrays. The prompt used to create it is in [`Adaptive_Antennas_GNSS_prompt.md`](Adaptive_Antennas_GNSS_prompt.md).

| Part | Sections | Topics |
|---|---|---|
| Introduction | 00–01 | Animated null-steering hero, why GNSS needs adaptive antennas, power levels of signal, noise and jammer |
| Foundations | 02–04 | Wavelength and phase (plane wave across two antennas), one antenna's gain pattern and RHCP, phasors |
| Two antennas | 05–06 | Polar gain of two antennas with an applied phase (spacing, amplitude, grating lobes, element pattern), the two-element null cone aimed at a jammer (sky map and polar cuts) |
| Arrays | 07–09 | Uniform linear array and array factor, weights as draggable phasors (beams and nulls), planar arrays and CRPA layouts |
| Interference | 10–11 | Kinds of interference and their spectra, the jamming budget (effective C/N₀, denial radius) |
| Adaptive algorithms | 12–16 | Covariance and eigenvalues, power inversion (playground with draggable jammers), MVDR and beam-per-satellite, SMI (Monte Carlo vs Reed–Mallett–Brennan) and LMS, degrees of freedom |
| Wideband processing | 17–18 | Channel mismatch, STAP and SFAP, carrier-phase and group-delay biases |
| Beyond jamming | 19–20 | Spoofing detection with phase single differences, MUSIC direction finding |
| Engineering | 21–22 | Worked numerical example (2 × 2 array, every intermediate number, iteration log), real hardware limits (mismatch, ADC) |
| History & industry | 23–25 | From radar sidelobe cancellers to GNSS CRPAs, technologies and companies, array sizes to scale, emerging technologies |
| Applications | 26–27 | Use cases and requirements map, regulation, standards and export control |
| Wrap-up | 28 | Five things to remember, glossary, jammer-to-tracking chain |
