# Physics-Boosted AI for Proactive Methane Leak Detection in Coal Mines

## Overview
This project demonstrates a physics-guided machine learning approach for early detection of methane leaks in coal mines. Traditional threshold-based methods detect leaks only after they become severe, while our model integrates domain knowledge, sensor data, and site-specific geological features to detect precursors, allowing proactive intervention.

---

## 🔍 Features
- Physics-informed feature engineering (flux anomaly, rate of change, seam depth, porosity, fault proximity)
- Leak simulation with precursor signals for realistic benchmarking
- Random Forest classifier trained to detect early warning signs of leaks
- Comparison with traditional threshold detection methods
- Performance metrics including classification reports and average proactive lead time
- Visualizations for time series and predictions

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
```

---

## ⚙️ Installation
This code requires Python 3.7+ and the following packages:
```bash
pip install numpy pandas matplotlib scikit-learn
```

---

## 🚀 Getting Started
1. Clone this repository  
2. Run the example script:
```bash
python enhanced_methane_leak_ai.py
```
3. Review the printed performance metrics and view the plotted results

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

The AI model accurately detects precursor conditions 1–2 months before the traditional system would react.

---

## 📈 Visualization
- Green `X`: AI predictions  
- Red dots: Ground truth leak periods (including precursors)  
- Blue circles: Threshold-based detections (reactive)  

The AI model consistently outperforms the baseline by both accuracy and timing.

---

## 📚 Theory
**Traditional Detection:** Relies on thresholds for methane flow/concentration, but lacks adaptability and is reactive.

**Physics-Guided AI:** Incorporates knowledge of methane emission dynamics in geological formations:
- **Flux anomaly** = difference from long-term moving average  
- **Rate of change** = first derivative of anomaly  
- **Seam depth and porosity** affect accumulation and flow  
- **Fault proximity** increases emission risk  

These features are used to train a classifier that anticipates leak events.

---

## 🛠️ Customization
To apply this to real-world sites:
- Replace simulated data with field sensor data and GIS layers
- Use the `data/` folder for inputs like:
  - EPA gridded CH₄ datasets (NetCDF)
  - Virginia geological shapefiles (e.g., fault lines, coal seams)
- Extend the ML pipeline with temporal models (e.g., LSTM, probabilistic models)

---

## 📌 Roadmap
- [ ] Integrate real-time GIS inputs  
- [ ] Incorporate LSTM for sequential prediction  
- [ ] Build a Streamlit web dashboard  
- [ ] Support uncertainty quantification and early warning thresholds  

---

## 🤝 Contributing
We welcome feedback, real-world datasets, or collaborations to improve and extend the tool.

---

## 📄 License
MIT License. See `LICENSE` file for details.

---

## 📬 Contact
Lead developer: **Leo Liu**, University of Virginia  
Email: `liurguva@gmail.com`  

This project was developed to support coal mine methane management and research initiatives in Virginia and beyond.
