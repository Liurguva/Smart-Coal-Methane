# Physics-Boosted AI for Proactive Methane Leak Detection in Coal Mines

## Overview
This repository presents physics-boosted AI methods for early detection of methane leaks in coal mines. Traditional threshold-based methods detect leaks only after they become severe, while our models integrate domain knowledge, sensor data, site-specific geological features, and even inverse physics modeling to detect precursors, allowing proactive intervention. To better illustrate the ideas, five simple examples were adopted in which the mine site information, geological information, physics laws, and machine learning algorithms were simplified.

---

## 🔍 Features
- Physics-informed feature engineering (flux anomaly, rate of change, seam depth, porosity, fault proximity)
- Leak simulation with precursor signals for realistic benchmarking
- Random Forest and Physics-Informed Neural Network (PINN) classifiers
- Inverse analysis to infer unknown material properties (permeability, viscosity) and physics laws
- Multi-location modeling to capture inter-site gas transfer behavior
- Comparison with traditional threshold detection methods
- Performance metrics including classification reports and average proactive lead time
- Visualizations for time series and predictions across locations

---

## 📁 Repository Structure
```
.
├── Single-Known-Material.py      # Demo to show how the inclusion of (known) material properties can enhance coal methane leak predictions at a single location
├── Single-Known-Material-Mechanism.py      #  Demo to show how the inclusion of (known) material properties and transport mechanisms can enhance coal methane leak predictions at a single location
├── Single-Unknown-Material-Mechanism.py      # Demo to show how the inference of (unknown) material properties and transport mechanisms (using differentiable modeling) can enhance coal methane leak predictions at a single location
├── Multiple-Known-Material-Mechanism.py      # Demo to show how the inclusion of (known) material properties and transport mechanisms can enhance coal methane leak predictions at multiple locations, which are related by the methane transfer between them
├── Multiple-Unknown-Material-Mechanism.py      # Demo to show how the inference of (unknown) material properties and transport mechanisms (using differentiable modeling) can enhance coal methane leak predictions at multiple locations, which are related by the methane transfer between them
├── README.md                        # This file
├── data/                            # Folder for future real-world data
│   ├── EPA_methane_flux.nc          # Placeholder NetCDF file (not included)
│   └── gis_shapefiles/              # Placeholder for geological shapefiles
├── LICENSE
```

---

## ⚙️ Installation
This project requires Python 3.7+ and the following packages:
```bash
pip install numpy pandas matplotlib scikit-learn torch
```

For CPU-only environments:
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
```

---

## 🚀 Getting Started

Run any script depending on your objective:

### Single-Location Examples
```bash
python Single-Known-Material.py
python Single-Known-Material-Mechanism.py
python Single-Unknown-Material-Mechanism.py
```

### Multi-Location Examples
```bash
python Multiple-Known-Material-Mechanism.py
python Multiple-Unknown-Material-Mechanism.py
```

---

## 📊 Sample Output
```
=== Physics-Guided AI ===
Precision: 0.95
Recall:    0.90
F1-score:  0.92

=== Traditional Method ===
Precision: 0.72
Recall:    0.45
F1-score:  0.55

Avg. AI Lead Time: 1.75 months
```

```
=== Inverse Modeling ===
Precision: 1.00
Recall:    0.97
F1-score:  0.98

Learned Parameters:
Permeability: 1.65e-13 m²
Viscosity:    2.21e-05 Pa·s
Pressure factor: 0.105

Average Lead Time: 9.00 months
```

---

## 📈 Visualization
Each script produces time series plots by location:
- **Green `X`**: AI predictions  
- **Red dots**: Ground truth leak periods (including precursors)  
- **Blue circles**: Threshold-based detections

---

## 📚 Theory

### Traditional Detection
- Based on thresholds of methane concentration
- Misses early signals and has low recall

### Physics-Boosted AI
- Uses geophysical knowledge like:
  - **Flux anomaly**: deviation from rolling average
  - **Rate of change**: slope of anomaly
  - **Seam depth**, **porosity**, **fault proximity**
- Optional physics equation:

  $$
  \text{Transport} = \frac{{\text{Permeability} \times \text{Porosity} \times \Delta P}}{{\text{Depth} \times \text{Viscosity}}}
  $$

### Inverse Modeling
- Learns unknown material properties using PyTorch and differentiable modeling
- Enables real-time adaptation to new environments

---

## 🛠️ Customization
To use with real mine data:
- Replace synthetic data with field sensor logs
- Use `data/` folder for:
  - Satellite CH₄ flux (NetCDF)
  - Geological shapefiles (e.g., fault zones)
- Extend models with:
  - LSTM/RNN for sequence memory
  - Bayesian neural nets for uncertainty

---

## 📌 Roadmap
- [x] Single-location models with known physics
- [x] Multi-location gas transport integration
- [x] Inverse modeling for unknown physics
- [ ] Real-time data ingestion
- [ ] LSTM-based sequential learning
- [ ] Streamlit dashboard
- [ ] Geospatial mapping of risk zones

---

## 🤝 Contributing
We welcome real-world data, code enhancements, or collaboration from mine operators and researchers.

---

## 📄 License
MIT License. See `LICENSE` file for details.

---

## 📬 Contact
Lead developer: **Leo Liu**, University of Virginia  
Email: `liurguva@gmail.com`

This project supports coal mine methane management and safety through proactive, physics-guided AI modeling.
