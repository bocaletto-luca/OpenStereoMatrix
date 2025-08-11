# OpenStereoMatrix

OpenStereoMatrix is a web-based, interactive speaker wiring designer supporting everything from basic stereo (2.0) to full 5.1 surround setups. Easily calculate impedance, power dissipation, and generate wiring schematics and BOMs. Perfect for both hobbyists and professionals, as well as complete neophytes.

---

## 🔗 Live Demo

Visit the live demo:  
https://bocaletto-luca.github.io/OpenStereoMatrix

---

## 🚀 Features

- Impedance calculation for series, parallel, and bridged configurations  
- SVG wiring diagrams for modes 2.0, 2.1, 4.0, 5.0, 5.1  
- Interactive calculator: impedance, total and per-speaker power  
- BOM generation guidelines for resistors and connectors  
- Thermal and mounting tips  
- Accessibility: `aria-label`, `<title>`, in-page anchor navigation  

---

## 📊 Supported Modes

| Mode     | Speakers        | Topology           | Impedance       | Notes                                    |
|----------|-----------------|--------------------|-----------------|------------------------------------------|
| 2.0      | 2 × 8 Ω         | Series / Parallel  | 16 Ω / 4 Ω      | Standard stereo                          |
| 2.1      | 2 × 8 Ω + Sub   | Stereo + LC Crossover | 4 Ω + sub     | Passive LC network for subwoofer         |
| 4.0      | 4 × 8 Ω         | Series–Parallel    | 8 Ω each        | Balanced quad setup                      |
| 5.0      | 5 × 8 Ω         | Surround           | 8 Ω each        | Front/Center/Rear                        |
| 5.1      | 6 × 8 Ω         | Surround + Sub     | 8 Ω each + sub  | Dedicated sub channel                    |
| Bridged  | 1 × 8 Ω         | Bridged Amp        | 8 Ω             | Doubles voltage swing                    |

---

## 🛠️ Quick Start

```bash
git clone https://github.com/bocaletto-luca/OpenStereoMatrix.git
cd OpenStereoMatrix
```

Simply open `index.html` in your browser—no server required.

---

## 📐 Example Calculations

**Series (2 × 8 Ω)**  
- Impedance: \(8 + 8 = 16\) Ω  
- Power at 20 Vrms: \(\frac{20^2}{16} = 25\) W per speaker  

**Parallel (2 × 8 Ω)**  
- Impedance: \(\frac{1}{\frac{1}{8} + \frac{1}{8}} = 4\) Ω  
- Power at 20 Vrms: \(\frac{20^2}{4} = 100\) W total (50 W per speaker)  

---

## 💻 Interactive Calculator

Located in the “Calculator” section, input:
1. Mode (series, parallel, bridged)  
2. Number of speakers  
3. Impedance per speaker (Ω)  
4. Voltage RMS (V)  

Click **Calculate** for instantaneous impedance and power results.

---

## 📋 Bill of Materials (BOM)

| Part            | Value         | Wattage | Footprint | Notes                      |
|-----------------|---------------|---------|-----------|----------------------------|
| Resistors       | 4.7 Ω         | 50 W    | TO-220    | Series/parallel damping    |
| Capacitor       | 100 µF        | —       | Radial    | Subwoofer LC filter        |
| Inductor        | 1.0 mH        | —       | Radial    | Subwoofer LC filter        |
| Connector Block | 3–6 pin       | —       | —         | Speaker output terminals   |

---

## 🌡️ Thermal & Mounting Guidelines

- Heatsink resistors ≥ 25 W  
- Minimum 20 mm clearance for airflow  
- Ferrite beads on long runs to limit EMI  

---

## 🎯 Contributing

Contributions, bug reports, and feature requests welcome!  
1. Fork the repo  
2. Create a branch (`git checkout -b feat/my-feature`)  
3. Commit changes (`git commit -m "Add feature"`)  
4. Push branch and open a Pull Request  

---

## 📄 License

GPL v3 License. See [LICENSE](LICENSE) for details.
