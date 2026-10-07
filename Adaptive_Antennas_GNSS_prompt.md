# Prompt: Adaptive antennas for GNSS (filled-in presentation template)

This is `presentation_prompt_template.md` filled in for the adaptive-antennas presentation. It produced [`Adaptive_Antennas_GNSS.html`](Adaptive_Antennas_GNSS.html). Reuse it to regenerate or extend that file, or copy it as a starting point for a related subject.

---

Write a single self-contained HTML presentation on **adaptive antennas (controlled reception pattern antennas, CRPAs) for GNSS applications**.

**Hard requirement: it must work fully offline.** I will present it from a laptop with no internet. The final file must open by double-click (a `file://` URL) and look and work exactly the same with the network unplugged: equations typeset, fonts correct, every figure and animation working. Network access is allowed while you build it, never when the page is viewed. If any part cannot be made to work offline, tell me before delivering.

## Inputs

- **Audience:** a novice engineer who knows basic algebra, trigonometry and a little about GNSS, but nothing about antennas, arrays or complex numbers.
- **Purpose:** start from basic concepts (waves, wavelength, phase, what one antenna does, phasors), build up through two antennas and arrays to the adaptive algorithms, then cover the real-world limits, history, industry and regulation.
- **Scope:** receive-side antenna arrays for GNSS user equipment: interference and jamming suppression, spoofing detection, direction finding, and the side effects on precise measurements. Out of scope: satellite transmit antennas, radar and communications arrays except as history, and classified details.
- **Length:** about 27 sections (28 after adding the two-antenna part below).
- **Language:** English.
- **File name:** `Adaptive_Antennas_GNSS.html`
- **Reference:** match the structure, components and visual style of `LPS_Local_Positioning_Systems.html` in this repository (read it first).

## Content

Cover these topics in a teaching order: foundations → two antennas → arrays → interference → adaptive algorithms → wideband processing → beyond jamming → engineering → history and industry → applications → summary.

- **Title section:** animated sky map of a 7-element array whose null follows a moving jammer.
- **Introduction:** why GNSS needs adaptive antennas (signal below the noise, FRPA versus CRPA), power-level ladder with a jammer, auto-generated table of contents.
- **Foundations:** waves, wavelength and phase (plane wave crossing two antennas); a single antenna's gain pattern and RHCP polarisation; phasors and adding signals.
- **Two antennas (added on request):** simulations of two antennas with an applied phase and their **polar gain** pattern (spacing, phase, amplitude, presets, element pattern multiplication, animated phase sweep); the two-element null cone in 3D aimed at a jammer, with a sky map and azimuth and vertical polar cuts.
- **Arrays:** uniform linear array and array factor (closed form, beamwidth, grating lobes); weights as draggable phasors (beam steering, deterministic null steering); planar arrays and CRPA layouts with a sky map.
- **Interference:** kinds of interference and their spectra; the jamming budget (effective C/N₀, J/S, denial radius versus suppression).
- **Adaptive algorithms:** signal model, covariance and eigenvalues; power inversion (derivation, closed form, interactive playground with draggable jammers); MVDR and beam-per-satellite; SMI (Reed–Mallett–Brennan) and LMS adaptation; degrees of freedom.
- **Wideband processing:** bandwidth, channel mismatch, STAP and SFAP; carrier-phase and group-delay biases caused by adaptive weights.
- **Beyond jamming:** spoofing detection with phase single differences; direction finding with MUSIC.
- **Worked numerical example:** a 2 × 2 array at L1, one 50 dB jammer at az 60°, el 10°, one satellite at az 200°, el 50°. Steering vectors, covariance, Woodbury inverse, power-inversion weights, null depth, output JNR, satellite gain and phase change, C/N₀ before and after, plus a steepest-descent iteration log. Compute the numbers independently first (Python) and use exactly those values.
- **Real hardware limits:** null depth versus amplitude and phase mismatch, ADC dynamic range, mutual coupling, size, installation.
- **History:** sidelobe canceller, Applebaum, Widrow LMS, Capon MVDR, Frost, RMB SMI, Compton power inversion, MUSIC, STAP for GNSS; animated timeline and a comparison table.
- **Leading technologies and companies** as cards, plus an array-size-to-scale comparison.
- **Emerging technologies:** multi-band CRPAs, miniaturisation, beam-per-satellite receivers, machine learning, synthetic arrays, polarisation-sensitive arrays, LEO PNT, distributed arrays (qualitative bubble chart).
- **Use cases** with a qualitative requirements map (threat level versus antenna size) and domain cards.
- **Regulation and standards:** jamming law, ITU bands and neighbours (L-band chart), RTCA/EUROCAE antenna and interference standards, EASA bulletins, resilient-PNT policy, export control.
- **Summary:** five things to remember, glossary, and a jammer-to-tracking waterfall figure.

**Must include:** FRPA/CRPA, power inversion, MVDR, SMI/LMS, STAP/SFAP, MUSIC, spoofing detection, two-antenna polar gain simulations with applied phase.
**Exclude:** transmit-side and radar/communications arrays except as history.

## Page format, section anatomy, teaching style, figures, visual design, offline requirements, build approach, verification checklist and deliverables

As in `presentation_prompt_template.md`, unchanged.
