# OpenStereoMatrix

Adapting classic stereo amplifiers to multi-speaker layouts using simple, robust passive networks. This project documents how to drive 3.0, 4.0, 5.0, 2.1, and 5.1 speaker sets from a 2.0 amplifier using only resistive matrices and careful wiring. All schematics are provided as clean, self-contained HTML (no external images or CAD files).

- License: GPL-3.0-or-later
- Docs: see `docs/index.html` (HTML-only schematics and wiring walkthroughs)

---

## Why

Many systems still revolve around reliable 2.0 amplifiers, while available speakers are often multi-channel sets. With a small, passive adaptor network, it’s possible to create:
- a stable phantom center for dialogue intelligibility (L+R),
- rear ambience channels via the Hafler matrix (L−R),
- a line-level feed for an active sub (2.1/5.1 style),
without DSPs, additional amps, or irreversible modifications.

This is an elegant, low-cost, reversible approach to spatialization for stereo sources.

---

## What this is not

This is not discrete surround. It does not decode Dolby/DTS or carry independent surround information. It derives center and surrounds from the stereo program material using analog techniques that preserve tonal balance and stereo integrity when set up correctly.

---

## Design overview

- Phantom center: summed from L and R through power resistors, level-trimmed to avoid collapsing the stereo width.
- Hafler rears: connected across L+ and R+ to reproduce the difference signal (L−R), which emphasizes ambience and out-of-phase content.
- Active subwoofer feed: a high-impedance divider creates a safe line-level output from the speaker terminals (stereo or summed mono).

All modes are selectable and can coexist (e.g., 5.0 = center + rears; 5.1 = 5.0 + sub feed).

---

## Safety and compatibility

- Common-ground vs BTL/Class-D: on common-ground amplifiers the negative speaker terminals share a reference; on many BTL/Class-D amps they do not. Never tie negatives together on non–common-ground designs.
- Load limits: never drop below the amplifier’s minimum load. Two identical 8 Ω speakers in parallel yield \(R=\frac{8\cdot 8}{8+8}=4\,\Omega\). In series, \(R=8+8=16\,\Omega\).
- Power dissipation: summing and attenuation resistors can get hot. Use appropriate power ratings and provide airflow.
- Always start at low volume, check temperature rise after 15–30 minutes, and adjust values if needed.

When in doubt, run the Hafler rears (which do not tie negatives) and feed an active sub with isolated high-level inputs or transformer isolation.

---

## Supported layouts

- 2.0 (pass-through)
- 2.1 (stereo or mono sub feed from high-level divider)
- 3.0 (phantom center derived from L+R)
- 4.0 (Hafler rears derived from L−R)
- 5.0 (3.0 + 4.0 combined)
- 5.1 (5.0 + sub feed)

Each layout has an HTML-only schematic and step-by-step wiring guide in `docs/index.html`.

---

## How it works

### Phantom center (3.0, 5.0, 5.1)
- Take L+ and R+ through two equal power resistors into the center positive terminal.
- Optionally add a shunt load/attenuator across the center driver to stabilize level.
- Center negative returns to common ground only if the amplifier is common-ground.

Goal: anchor dialogue without collapsing stereo width. Balance is set by the summing resistor values and any added shunt.

### Hafler rears (4.0, 5.0, 5.1)
- Connect each rear speaker between L+ and R+ so they reproduce \(L - R\).
- Add attenuation (series resistor or L-pad) to taste; rears should be subtle.
- This topology typically avoids tying channel negatives, improving compatibility with many BTL/Class-D amplifiers.

Goal: extract ambience and out-of-phase cues that naturally exist in many stereo recordings.

### Active sub feed (2.1, 5.1)
- For each channel, tap a high-impedance divider from the speaker output to generate line-level.
- Use stereo into the sub’s L/R inputs, or sum to mono with two equal series resistors before the RCA.

Goal: integrate low frequencies via the sub’s own crossover/phase controls without burdening the main amp.

---

## Recommended starting values

These are conservative, proven starting points intended for typical home setups. They can be tuned based on speaker sensitivity and listening level.

| Section         | Topology                                 | Suggested values                                  | Power rating           | Notes |
|-----------------|-------------------------------------------|---------------------------------------------------|------------------------|-------|
| Phantom center  | L+ → R_sum, R+ → R_sum → Center+          | 2× 8.2 Ω from L+/R+ to Center+; optional 8.2–10 Ω shunt across center | 15–25 W (series), 25 W (shunt) | Adjust for center balance; higher series = lower center level |
| Hafler rears    | Rears between L+ and R+                   | Optional 3.3–10 Ω series per rear or 8 Ω L-pad     | 10–50 W                | Attenuate to keep rears as ambience, not dominant |
| Sub line feed   | High-level to line divider per channel    | 10 kΩ series to node, 1 kΩ to ground; RCA from node | 0.25 W is fine         | For mono sub: sum L/R via 2× 10 kΩ into one RCA |

Power ratings should be increased for high-power use or extended high-SPL sessions.

---

## Impedance reminders

- Parallel of two identical 8 Ω speakers: \(R=\frac{8\cdot 8}{8+8}=4\,\Omega\).
- Series of two identical 8 Ω speakers: \(R=8+8=16\,\Omega\).
- Avoid \(\,R<4\,\Omega\) unless the amplifier is specified stable into very low loads.

The Hafler matrix typically presents modest additional loading because rears see difference signals, but thermal checks are still essential.

---

## Repository structure

```
openstereomatrix/
├─ README.md
├─ LICENSE
└─ index.html   ← HTML-only, self-contained schematics + wiring guides
```

All diagrams are authored directly in HTML/SVG-like primitives without external images, to keep the project fully portable and easy to review.

---

## Usage

- Read `docs/index.html` and choose the target layout.
- Follow the wiring steps and tables; build on a terminal block or inside a ventilated enclosure.
- Start at low volume, verify temperatures and balance, then fine-tune resistor values if necessary.

---

## Contributing

Issues and pull requests are welcome. Especially valuable:
- measured resistor temperatures at typical listening levels,
- compatibility reports with specific amplifier models (common-ground vs BTL/Class-D),
- alternative value sets for different speaker sensitivities,
- improvements to the HTML schematics and explanatory text.

---

## License

GPL-3.0-or-later

SPDX-ID: `GPL-3.0-or-later`

---

## Disclaimer

Use at your own risk. Verify amplifier topology and minimum load specifications. Do not tie channel negatives together on non–common-ground amplifiers. Always validate at low volume before regular use.
