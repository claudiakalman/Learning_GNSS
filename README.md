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

## The GPS navigation message: interactive primer

Open [`GPS_Navigation_Message.html`](GPS_Navigation_Message.html) in any modern browser. It is one long, self-contained page (MathJax and fonts load from a CDN) about the legacy GPS navigation message (LNAV, IS-GPS-200): how it is built, what it contains, and how a receiver turns its bits into a satellite position and clock correction.

The page scrolls freely but is split into 19 numbered sections. A sticky top bar shows the current section, prev/next buttons, a segmented progress bar and a section menu. Keys: ← / → jump between sections, `F` dims the sections not in view, `M` opens the section list. Light and dark themes follow the system setting and can be switched in the bar.

Each section opens with an **"In plain words"** box, then derives the math step by step (boxed formulas are the ones engineers use), then shows a live figure computed from the same equations: sliders, presets, draggable points, hover read-outs and coloured result chips. Animations pause off-screen and respect reduced-motion settings.

| Part | Sections | Topics |
|---|---|---|
| I. Foundations | 1–3 | What the message is and how LNAV compares with CNAV, CNAV-2, Galileo I/NAV and GLONASS; 50 bit/s data on the C/A code; bits → words → subframes → frames → 12.5 min superframe |
| II. The math inside the message | 4–11 | TLM/HOW and the TOW count; parity (Hamming-type code, polarity recovery); scaled integers and semicircles; clock correction with the relativistic term; Kepler's equation; ECEF position; almanac, Klobuchar ionosphere and UTC; **worked example** from raw integers to satellite position |
| III. Real-world effects | 12–14 | Bit errors versus C/N₀ and time to first fix; week-number rollover and leap seconds; limits (Shannon bound, LSB sensitivity, model accuracy, no authentication) |
| IV. History and evolution | 15–16 | Transit to today's GNSS; CNAV/CNAV-2/I/NAV packets, CRC-24Q, convolutional coding gain, OSNMA |
| V–VI. Applications, industry | 17–18 | Use cases and their requirements; established and emerging companies (qualitative) |
| VII. Summary | 19 | Five things to remember, filterable glossary, pipeline recap |

The worked example (section 11) was computed independently twice in Python (the IS-GPS-200 scalar formulas, and Newton's method with rotation matrices; they agree to better than 10⁻⁸ m), and the page recomputes it in the browser and shows the difference. Parity was checked with two independent implementations (the IS-GPS-200 equations and 32-bit masks). The ephemeris values are invented but realistic, and each is an exact multiple of its LSB.
