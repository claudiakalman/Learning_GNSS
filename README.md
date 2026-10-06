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

## Local Positioning Systems (LPS) vs GNSS: interactive presentation

Open [`LPS_Local_Positioning_Systems.html`](LPS_Local_Positioning_Systems.html) in any modern browser. It is one self-contained page that scrolls freely but is divided into 27 presentable sections (title plus 26 numbered). Use ← / → to jump between sections, `F` to toggle focus dimming of the sections not in view, and `M` for the section list. Equations (MathJax) and fonts load from a CDN; every figure is computed live in the browser, and most are interactive (drag points, move sliders).

The scope is **outdoor and wide-area** positioning: indoor-only solutions are deliberately left out.

| Part | Sections | Topics |
|---|---|---|
| Introduction | 00–01 | What an LPS is, scale versus GNSS |
| Foundations | 02–06 | Time of flight and the Cramér–Rao bound, TOA/TDOA/AoA/RSSI, trilateration, two-way ranging (SS/DS-TWR with clock-drift math), LPS versus GNSS |
| The math | 07, 11 | Linearised least squares (Gauss–Newton), full worked numerical example (4 beacons, matrices, DOP, CEP, 2DRMS) |
| Geometry · GDOP | 08–10 | Two-anchor HDOP = √2/sin θ, covariance and the DOP family, error ellipses with Monte Carlo, 4-satellite sky plot and tetrahedron volume |
| Real-world errors | 12–13 | LOS/NLOS and multipath versus bandwidth, urban canyons |
| Platforms | 14–15 | Ground vehicles and the open-pit vertical problem, air platforms (closed-form HDOP/VDOP vs altitude) |
| Design | 16–17 | Accuracy maps of planned networks, accuracy by technology, resolution limits |
| History & backup | 18–19 | LORAN-A/C, Decca, Chayka, Omega, Alpha (RSDN-20), eLoran; receiver and antenna size, Chu limit, minimal receiver systems |
| Industry | 20–24 | Technologies and companies (Locata and NextNav spotlights), passive LEO positioning (Starlink, OneWeb, Iridium, Orbcomm), use cases, E911/E112, emerging technologies |
| Wrap-up | 25–26 | GNSS + LPS + inertial fusion, summary and glossary |
