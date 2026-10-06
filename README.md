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
