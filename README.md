# Capstone Assignment Predictive Maintenance From RUL Modeling to Real World Telemetry
Final capstone project for the UC Berkeley ML &amp; AI Certificate, comparing predictive maintenance on benchmark RUL data vs real-world telemetry.

## Overview

This capstone project explores how machine learning performs in predictive maintenance under two very different conditions:

1. A **controlled benchmark dataset** with clear degradation behavior and labeled outcomes, and  
2. A **real-world telemetry dataset** with noisy operational data but no explicit failure labels.

The purpose of the project is not just to build models, but to evaluate how much the structure and quality of the data influence what machine learning can realistically achieve.

The analysis is split into two notebooks:

- **Notebook 1:** NASA C-MAPSS FD001 turbofan engine dataset  
- **Notebook 2:** Hospital equipment telemetry dataset  

Together, they show the difference between a well-defined predictive maintenance problem and a real operational setting where the problem is far less clear.

---

## Project Objective

The objective of this project is to evaluate how the presence (or absence) of degradation signals and failure labels impacts the effectiveness of machine learning in predictive maintenance.

Specifically, the project aims to:

- assess how well models can predict Remaining Useful Life (RUL) in a controlled, labeled environment  
- determine what type of insights can be extracted from real-world telemetry without labeled failures  
- highlight the limitations of applying standard machine learning approaches to operational data  

The goal is to understand not just model performance, but the conditions required for predictive maintenance to be feasible in practice.

---

## Datasets

### FD001 Turbofan (Benchmark)
- Simulated run-to-failure engine data  
- Clear degradation patterns  
- Remaining Useful Life (RUL) available  
- Suitable for supervised learning  

### Hospital Telemetry (Real-World)
- Electrical and temperature sensor data  
- Variable data quality over time  
- No labeled failures  
- No clear degradation trajectory  

---

## Approach

### Turbofan (Supervised Learning)
- Feature selection based on degradation trends  
- Multiple regression models trained and compared  
- Hyperparameter tuning using GridSearchCV  
- Evaluation using MAE, RMSE, and lifecycle analysis  

### Hospital (Unsupervised / Interpretive)
- Rule-based definition of ON/OFF and anomalies  
- Analysis of system-wide vs machine-specific behavior  
- PCA for dimensionality reduction  
- K-Means clustering to identify operating regimes  

---

## Key Findings

### Turbofan
- ~12 sensors identified as informative for RUL prediction  
- Models achieved ~29 MAE across full lifecycle  
- Best model (SVR) reached ~20.5 MAE on test data  
- Accuracy improves closer to failure as degradation signals become clearer  
- Model performance depends more on signal visibility than model complexity  

### Hospital
- Clear difference between unstable early data and stable operation  
- Many anomalies occur across multiple machines → system-level effects  
- No failure labels → predictive modeling not feasible  
- Clustering identifies operating regimes, not failure states  
- Main limitation is lack of degradation signals and labels  

---

## Conclusion

The project highlights the gap between benchmark and real-world predictive maintenance.

In controlled datasets like FD001, machine learning can effectively model degradation and predict outcomes. In real-world telemetry, the absence of labels and clear degradation patterns shifts the task from prediction to interpretation.

The key takeaway is that machine learning is less limited by model choice, and more by the structure and quality of the data available.

---

## Limitations

- FD001 is simulated and cleaner than real-world data  
- Hospital dataset lacks labeled failures and consistent degradation patterns  
- Many anomalies are system-level rather than equipment-specific  
- Results in the hospital case are interpretive, not predictive  

---

## Next Steps

- Incorporate maintenance or failure logs  
- Explore pre-shutdown pattern detection  
- Use distance-from-cluster as anomaly scoring  
- Apply time-series or anomaly detection models  
- Improve data labeling and context  

---

## Repository Structure

```text
.
├── data/
│   ├── train_FD001.txt
│   ├── test_FD001.txt
│   ├── RUL_FD001.txt
│   └── hospital_telemetry_jan_2025_to_mar_2026.csv
│
├── 1. Capstone_Assignment_24.1_Turbofan_FD001_Jonathan_O'Dea.ipynb
├── 2. Capstone_Assignment_24.1_Hospital_Telemetry_Jonathan_O'Dea.ipynb
└── README.md
```
---

## How to Run

1. Clone or download the repository
2. Ensure all datasets are located inside the `/data` folder
3. Run the notebooks in order:

   * `1. Capstone_Assignment_24.1_Turbofan_FD001_Jonathan_O'Dea.ipynb`
   * `2. Capstone_Assignment_24.1_Hospital_Telemetry_Jonathan_O'Dea.ipynb`

> Make sure the folder structure is preserved so the notebooks can locate the data files correctly.

---

## Author

Jonathan O'Dea  
Capstone Project  
UC Berkeley Professional Certificate in Machine Learning & Artificial Intelligence

---

## References

- NASA C-MAPSS Turbofan Engine Degradation Simulation Dataset (https://data.nasa.gov/dataset/cmapss-jet-engine-simulated-data) 
- UC Berkeley Professional Certificate in Machine Learning & Artificial Intelligence course materials  
- Scikit-learn Documentation: https://scikit-learn.org/  
- TensorFlow / Keras Documentation: https://www.tensorflow.org/
