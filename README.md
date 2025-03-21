# NYC Taxi Fare Prediction 🚕📊  
**Predicting taxi fares in New York City using machine learning**  

[![ReviewNB](https://img.shields.io/badge/ReviewNB-Interactive_Code_Review-00A98F?style=for-the-badge&logo=jupyter)](https://app.reviewnb.com/AsmitMalviya/NYC-Taxi-Fare-Prediction/blob/master/nyc-taxi-fare.ipynb/file) 
[![Python](https://img.shields.io/badge/Python-3.8%2B-blue?logo=python)](https://www.python.org/)  

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
- [Acknowledgements](#-acknowledgements)  

---

## 🎯 Problem Statement  
Taxi fare prediction is critical for both riders and drivers to ensure transparency and efficiency. This project tackles the challenge of predicting fares accurately using spatial, temporal, and contextual features like pickup/dropoff coordinates, timestamps, and passenger counts. The goal is to build a robust regression model that generalizes well to unseen data while handling real-world complexities like outliers and geospatial noise.

---

## ✨ Key Features  
- **Optimized Data Handling**: Load 55M+ rows efficiently using pandas with memory-friendly data types.  
- **Geospatial Analysis**: Calculate Haversine distance between pickup/dropoff points.
- **Feature Engineering**: Extract temporal features (hour, day, month) and detect outliers.  
- **Model Comparison**: Test Linear Regression, Random Forest, CatBoost, and LightBGM with hyperparameter tuning.  
- **Interactive Notebooks**: ReviewNB integration for collaborative Jupyter notebook reviews.

---

## 📂 Dataset  
**Source**: [Kaggle NYC Taxi Fare Prediction](https://www.kaggle.com/c/new-york-city-taxi-fare-prediction)  
- **Training Data**: 55M+ rows (1% sampled for efficiency).  
- **Test Data**: 9,914 rows.
- **Features**
  - **fare_amount**: Target variable (fare in USD).
  - **pickup_datetime**: Timestamp of the ride.
  - **pickup/dropoff_latitude/longitude**: GPS coordinatesd.
  - **passenger_count**: Number of passengers.    
  

**Data Challenges**:  
- Outliers (e.g., negative fares, invalid coordinates).  
- Temporal patterns (rush hours, holidays).  

---

## 🔄 Workflow  
1. **Data Acquisition**
   - **Kaggle Integration**: Use opendatasets to fetch data directly from Kaggle.
   - **Optimized Loading**: Reduce memory usage with dtype conversions (e.g., float32 for coordinates).
   - **Sampling**: Randomly select 1% of training data (~550K rows) for faster iteration.   
2. **Exploratory Data Analysis (EDA)**
   - **Descriptive Statistics**:
     - **Fare distribution**: 95% of fares are between 2.5 and 30.
     - **Geospatial Clusters**: Removed coordinates outside NYC bounds (Lat: 40–42, Lon: -75–-72)
    
   - **Visualizations**:
     - **Histogram of Fares**: Skewed distribution with a long tail.
     - **Outliers**: Pickups concentrated in Manhattan.
3. **Data Preprocessing**
   - **Cleaning**:
     - Drop rows with fare_amount ≤ 0 or passenger_count = 0.
     - Filter invalid coordinates using NYC bounding boxes.
   - **Feature Engineering**:
     - **Haversine Distance**: Compute trip distance (in km).
       ```python
       import numpy as np

       def haversine(lon1, lat1, lon2, lat2):
           """
           Calculate the great-circle distance between two points on Earth.
           
           Parameters:
           lon1, lat1: Longitude and latitude of point 1 (in degrees).
           lon2, lat2: Longitude and latitude of point 2 (in degrees).
           
           Returns:
           Distance in kilometers.
           """
           # Convert degrees to radians
           lon1, lat1, lon2, lat2 = map(np.radians, [lon1, lat1, lon2, lat2])
           
           # Haversine formula
           dlon = lon2 - lon1
           dlat = lat2 - lat1
           a = np.sin(dlat/2)**2 + np.cos(lat1) * np.cos(lat2) * np.sin(dlon/2)**2
           c = 2 * 6371 * np.arcsin(np.sqrt(a))  # Earth radius = 6371 km
           return c
     - **Temporal Features**: Extract hour, day_of_week, and month from pickup_datetime.
4. **Model Development**
     - **Algorithms**:   
       - **Linear Regression**: Baseline model.
       - **Random Forest**: Handles non-linear relationships.
       - **CatBoost**: Optimized for regression with hyperparameter tuning.
     - **Train-Test Split**: 80-20 split with sklearn.model_selection.train_test_split.
     - **Algorithms**: Use GridSearchCV for CatBoost.
5. **Evaluation**
   - **Metrics**: Root Mean Squared Error (RMSE) on the test set.
   - **Results**:
     
    | Model               | RMSE   |
    |---------------------|--------|
    | Linear Regression   | $5.45  |
    | Random Forest       | $4.12  |
    | **CatBoost**        | **$3.12** |  
   -
6. **Submission**
     - Generate predictions for the Kaggle test set and format into sample_submission.csv.

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
2. Install dependencies:  
   ```bash
   pip install -r requirements.txt
3. Run the Jupyter notebook:
   jupyter notebook nyc-taxi-fare.ipynb

## 🚀 Future Improvements 
- **Feature Engineering**: Add traffic data or weather conditions. 
- **Deep Learning**: Experiment with neural networks (e.g., LSTMs for temporal patterns).
- **Deployment**: Build a Flask API for real-time predictions.

## 🤝 Contributing 
1. Fork the repository.
2. Create a branch:
   ```bash
   git checkout -b feature/new-feature
3. Commit changes:
   ```bash
   git commit -m 'Add a new feature'
4. Push to the branch:
   ```bash
   git push origin feature/new-feature
5. Open a Pull Request.      
   
## 🙏 Acknowledgements
- Kaggle Community for the dataset and competition framework.
- ReviewNB for simplifying Jupyter notebook collaboration.
  - [![ReviewNB](https://img.shields.io/badge/ReviewNB-Interactive_Code_Review-00A98F?style=for-the-badge&logo=jupyter)](https://app.reviewnb.com/AsmitMalviya/NYC-Taxi-Fare-Prediction/blob/master/nyc-taxi-fare.ipynb/file ))    
