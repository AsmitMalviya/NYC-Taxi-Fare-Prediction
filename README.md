# NYC Taxi Fare Prediction 🚕📊  
**Predicting taxi fares in New York City using machine learning**  

[![ReviewNB](https://img.shields.io/badge/ReviewNB-Interactive_Code_Review-00A98F?style=for-the-badge&logo=jupyter)](https://www.reviewnb.com/github/your-username/nyc-taxi-fare-prediction)  
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)  
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)  

---

## 📌 Table of Contents  
- [Problem Statement](#-problem-statement)  
- [Key Features](#-key-features)  
- [Dataset](#-dataset)  
- [Workflow](#-workflow)  
- [Installation & Usage](#-installation--usage)  
- [Results & Model Performance](#-results--model-performance)  
- [Future Improvements](#-future-improvements)  
- [Contributing](#-contributing)  
- [License](#-license)  
- [Acknowledgements](#-acknowledgements)  

---

## 🎯 Problem Statement  
Predict NYC taxi fares using spatial, temporal, and contextual features. The model addresses challenges like geospatial noise, outliers, and dynamic pricing patterns to deliver accurate fare estimates.

---

## ✨ Key Features  
- **Optimized Data Handling**: Efficiently load and sample 55M+ rows.  
- **Geospatial Analysis**: Haversine distance calculation for trip routes.  
- **Feature Engineering**: Temporal features (hour/day/month) and outlier detection.  
- **Model Comparison**: Linear Regression, Random Forest, and XGBoost.  
- **Interactive Notebooks**: ReviewNB integration for collaborative Jupyter notebook reviews.

---

## 📂 Dataset  
**Source**: [Kaggle NYC Taxi Fare Prediction](https://www.kaggle.com/c/new-york-city-taxi-fare-prediction)  
- **Training Data**: 55M+ rows (1% sampled for efficiency).  
- **Test Data**: 9,914 rows.  
- **Features**: `fare_amount`, `pickup/dropoff` coordinates, `pickup_datetime`, `passenger_count`.  

**Preprocessing**:  
- Removed invalid coordinates (lat: 40–42, lon: -75–-72).  
- Filtered negative fares and unrealistic passenger counts.  

---

## 🔄 Workflow  
1. **Data Acquisition**: Download from Kaggle using `opendatasets`.  
2. **EDA**: Analyze distributions, visualize geospatial clusters, and detect outliers.  
3. **Preprocessing**: Clean data and engineer features (Haversine distance, time-based features).  
4. **Model Training**: Train and compare Linear Regression, Random Forest, and XGBoost.  
5. **Evaluation**: Validate models using RMSE.  
6. **Submission**: Generate Kaggle-compatible predictions.  

---

## 💻 Installation & Usage  
### Prerequisites  
- Python 3.8+  
- Kaggle API token (save to `~/.kaggle/kaggle.json`).  

### Steps  
1. Clone the repository:  
   ```bash
   git clone https://github.com/your-username/nyc-taxi-fare-prediction.git
   cd nyc-taxi-fare-prediction
