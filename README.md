# Smart Crop Prediction & Disease Detection using ML

A machine learning system that predicts the best crop to grow and detects plant disease conditions using soil and environmental sensor readings — achieving **99.32% crop prediction accuracy** and **99.77% disease detection accuracy**.

---

## Overview

Traditional farming relies on manual observation and experience to decide which crop to grow and when a plant is unhealthy. This project automates both decisions using ML models trained on real agricultural sensor data — no images or hardware required.

Two models work together:
- **Crop Prediction** → recommends the best crop based on soil and weather conditions
- **Disease Detection** → identifies plant health issues from the same sensor readings

---

## Tech Stack

| Category | Tools / Technologies |
|---|---|
| Language | Python |
| ML Models | Random Forest, Gradient Boosting |
| Libraries | Scikit-learn, Pandas, NumPy, Matplotlib, Seaborn |
| Platform | Google Colab |
| Dataset | Crop Recommendation Dataset (Kaggle) |

---

## How It Works

### Part 1 — Crop Prediction
```
N, P, K, Temperature, Humidity, pH, Rainfall → Random Forest → Crop Name
```
- Trained on 2200 samples across 22 crop types
- Uses Random Forest (100 decision trees voting together)
- Predicts the most suitable crop for given soil/weather conditions

### Part 2 — Disease Detection
```
N, P, K, Temperature, Humidity, pH, Rainfall → Gradient Boosting → Disease / Healthy
```
Disease labels are generated from agricultural threshold rules:

| Sensor Condition | Disease Label |
|---|---|
| Temperature > 35°C and Humidity > 80% | Fungal Disease |
| pH < 5.5 | Nutrient Deficiency |
| N, P, K all < 20 | Nutrient Deficiency |
| Rainfall > 250mm and pH < 6.0 | Root Rot |
| Temperature < 10°C | Cold Stress |
| All values balanced | Healthy |

---

##  Results

### Model Performance

| Model | Accuracy | Precision | Recall |
|---|---|---|---|
| ✅ Crop Prediction | **99.32%** | 99% | 99% |
| ✅ Disease Detection | **99.77%** | 100% | 100% |

---

###  Crop Prediction — Classification Report (Top Classes)

| Crop | Precision | Recall | F1-Score |
|---|---|---|---|
| Apple | 1.00 | 1.00 | 1.00 |
| Rice | 1.00 | 0.89 | 0.94 |
| Jute | 0.92 | 1.00 | 0.96 |
| Maize | 1.00 | 1.00 | 1.00 |
| All 22 crops (avg) | 0.99 | 0.99 | 0.99 |

---

### Disease Detection — Sample Predictions

| Sensor Condition | Predicted Disease |
|---|---|
| High Temp + Humidity | Fungal Disease ✅ |
| Low pH + Low NPK | Nutrient Deficiency ✅ |
| Balanced Conditions | Healthy ✅ |
| High Rainfall + Low pH | Root Rot ✅ |

---

### Disease Label Distribution in Dataset

| Condition | Count |
|---|---|
| Healthy | 1969 |
| Nutrient Deficiency | 154 |
| Fungal Disease | 61 |
| Root Rot | 10 |
| Cold Stress | 6 |

---

##  Features

- ✅ Predicts from 22 crop types with 99.32% accuracy
- ✅ Detects 5 plant disease/stress conditions from sensor data
- ✅ No hardware or images required — purely software based
- ✅ Generates confusion matrices and feature importance charts
- ✅ Fast training — runs in minutes on Google Colab (free)
---

## Future Improvements

- Integrate with ESP32 for real-time sensor-based prediction
- Add a web dashboard for farmers to input values and get predictions
- Expand disease labels using real field survey data
- Deploy as a mobile app for rural accessibility

---

## Dataset

- **Source:** [Crop Recommendation Dataset — Kaggle](https://www.kaggle.com/datasets/atharvaingle/crop-recommendation-dataset)
- **Size:** 2200 samples, 22 crop types
- **Features:** N, P, K, Temperature, Humidity, pH, Rainfall

---

##  License

This project is open source and available under the [MIT License](LICENSE).
