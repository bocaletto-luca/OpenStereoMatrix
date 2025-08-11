# OpenStereoMatrix

OpenStereoMatrix is a web-based tool for designing and visualizing speaker wiring topologies—from simple stereo (2.0) setups to full 5.1 arrays and bridged configurations. It calculates combined impedance, power dissipation, and generates SVG schematics plus a complete Bill of Materials (BOM) to guide both hobbyists and professionals.

---

## 🔗 Live Demo

Explore the interactive demo at  
https://bocaletto-luca.github.io/OpenStereoMatrix

---

## 🚀 Features

- Automatic impedance calculation for series, parallel, and bridged speaker networks  
- Real-time SVG wiring diagrams with component labels  
- Example calculations for power dissipation using \(P = \frac{V^2}{R}\)  
- Detailed BOM lists (resistor values, wattage, footprints)  
- Thermal guidance: temperature vs. load tables and mounting tips  
- Accessible markup (`aria-label`, alt text) and anchor links for each section  

---

## 📊 Supported Configurations

| Mode     | Speakers      | Topology           | Resulting Impedance | Notes                                    |
|----------|---------------|--------------------|---------------------|------------------------------------------|
| 2.0      | 2 × 8 Ω       | Parallel / Series  | 4 Ω / 16 Ω          | Standard stereo                          |
| 2.1      | 2 × 8 Ω + Sub | Stereo + Crossover | 4 Ω + sub (8 Ω)     | Add low-pass filter for subwoofer        |
| 5.1      | 6 × 8 Ω       | Surround           | 8 Ω each            | L/R, Center, Ls/Rs, Sub independently    |
| Bridged  | 2 × 8 Ω       | Bridge Amp Output  | 8 Ω                | Doubles available voltage swing          |
| Custom   | N speakers    | Mixed              | Calculated live     | Any combination—view impedance chart     |

---

## 🛠️ Quick Start

1. Clone the repository  
   ```bash
   git clone https://github.com/bocaletto-luca/OpenStereoMatrix.git
   cd OpenStereoMatrix
   ```  
2. Open `index.html` in your browser (no server required)  
3. Select your mode, enter speaker counts/values, and review the schematic + BOM  

---

## 📐 Example Calculations

### Parallel Connection (2 × 8 Ω)
- Combined impedance: \(\frac{1}{\frac{1}{8} + \frac{1}{8}} = 4\) Ω  
- Power on each speaker at 20 Vrms:  
  \[
    P = \frac{V^2}{R} = \frac{20^2}{4} = 100\text{ W total (50 W/speaker)}
  \]

### Series Connection (2 × 8 Ω)
- Combined impedance: \(8 + 8 = 16\) Ω  
- Power on each speaker at 20 Vrms:  
  \[
    P = \frac{20^2}{16} = 25\text{ W per speaker}
  \]

---

## 📋 Bill of Materials (BOM)

| Part            | Value  | Wattage | Package/Footprint | Notes                          |
|-----------------|--------|---------|-------------------|--------------------------------|
| Resistor R1, R2 | 4.7 Ω  | 50 W    | TO-220           | For series/parallel damping    |
| Resistor R3     | 8.2 Ω  | 25 W    | SIP              | Subwoofer crossover            |
| Connector Block | —      | —       | 5-pin             | Speaker output terminals       |

---

## 🌡️ Thermal & Mounting Guidelines

- Use heatsinks on resistors ≥ 25 W  
- Maintain at least 20 mm clearance for airflow  
- Refer to the temperature rise table below:

| Load (W) | No Heatsink (°C rise) | With Heatsink (°C rise) |
|----------|-----------------------|-------------------------|
| 50       | 80                    | 40                      |
| 100      | 120                   | 60                      |

---

## 🖥️ Accessibility & Usability

- All SVGs include `aria-label` and `<title>` tags  
- In-page anchor links for instant navigation  
- High-contrast mode available via query parameter `?theme=dark`

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome!  
1. Fork the repo  
2. Create a feature branch (`git checkout -b feat/my-feature`)  
3. Commit your changes (`git commit -m "Add awesome feature"`)  
4. Push and open a Pull Request  

---

## 📄 License

This project is released under the MIT License. See [LICENSE](LICENSE) for details.
