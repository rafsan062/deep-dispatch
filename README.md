# deep-dispatch

DeepDispatch is an end-to-end spatiotemporal machine learning system designed to improve taxi fleet positioning in New York City. By analyzing historical taxi trip data and forecasting revenue potential one hour in advance, the system provides proactive guidance to drivers through an interactive geographic heatmap.

The project combines spatial clustering, advanced feature engineering, classical machine learning, and deep learning models to transform large-scale transportation data into actionable dispatch recommendations.

---

# Overview

Urban transportation often suffers from **spatial mismatch**, where taxi supply fails to align with passenger demand. Drivers frequently rely on intuition and end up circling empty streets, wasting time and fuel while missing profitable areas. DeepDispatch replaces reactive intuition with **data-driven demand forecasting**. Using the NYC Yellow Taxi dataset, the system predicts future revenue potential across different city zones and visualizes these predictions through an interactive heatmap that highlights high-value areas for repositioning. Instead of predicting unstable raw revenue values, DeepDispatch converts revenue into **five interpretable classes** ranging from low demand to surge demand, allowing drivers to quickly identify profitable zones.

---

# Dataset
The project uses historical taxi trip records containing information such as:

- Pickup and dropoff timestamps  
- Geographic coordinates  
- Trip distance and duration  
- Fare and revenue information  

These features allow the system to analyze both **temporal patterns** and **spatial mobility behavior** across the city.

---

# System Pipeline
DeepDispatch transforms raw taxi logs into predictions through a multi-stage pipeline.

### 1. Data Cleaning
Invalid trips and unrealistic values are removed to ensure reliable modeling.

### 2. Spatial Clustering
K-Means clustering divides New York City into **150 demand zones**, allowing the system to analyze mobility patterns without relying on arbitrary geographic boundaries.

### 3. Temporal Aggregation
Taxi trips are aggregated **hourly per zone**, forming the time-series structure used for forecasting.

### 4. Feature Engineering
The system generates extensive spatiotemporal features, including:

- Lag features
- Rolling averages
- Cyclical time encoding 
- Weekend indicators
- Special events and anomaly flags

These features capture the strong weekly patterns present in urban mobility data.

### 5. Revenue Potential Target
A custom **profit_index** metric combines total revenue and earning efficiency to represent economic value per zone.
This metric is converted into **five revenue classes**:

1. Quiet  
2. Steady  
3. Busy  
4. High Value  
5. Surge  

This classification produces a more stable and interpretable signal for dispatch decisions.

---

# Models

DeepDispatch evaluates both classical machine learning models and deep learning architectures.

## Classical Machine Learning
Baseline models include:

- Logistic Regression  
- Random Forest  
- **XGBoost**

XGBoost achieved the strongest performance with approximately **79% test accuracy** and strong ordinal consistency across revenue classes.

---

## Deep Learning Models
To capture sequential patterns in taxi demand, we implemented two neural architectures using PyTorch:

### LSTM (Long Short-Term Memory)
Processes a **24-hour sequence of historical activity** per zone to learn temporal demand dynamics.

### Transformer Encoder
Uses **self-attention mechanisms** to model relationships between different time steps within the sequence.
Both models achieve competitive performance while learning temporal patterns directly from raw sequences.

---

# Interactive Revenue Heatmap
The final output of the DeepDispatch pipeline is an **interactive geographic heatmap**.

Model predictions for each zone are projected onto the NYC road network and visualized using a color-coded revenue scale.

Features of the heatmap include:

- Color-coded demand intensity  
- Hour-by-hour demand predictions  
- Spatial visualization of profitable zones  
- Animated temporal demand flow across the city  

This interface converts model predictions into a **practical decision-support tool for taxi drivers and fleet operators**.

---

# Results

Performance comparison across models shows:

| Model | Accuracy |
|------|------|
| Logistic Regression | ~75% |
| Random Forest | ~78% |
| **XGBoost** | **~79%** |
| LSTM | ~78% |
| Transformer | ~78% |

More importantly, the system achieves **~99.7% 1-class tolerance accuracy**, meaning prediction errors almost never exceed one adjacent revenue class.
This ensures that even imperfect predictions still guide drivers toward profitable areas.

---

# Technologies Used

DeepDispatch was built using the following tools:

- Python  
- Pandas / NumPy  
- Scikit-Learn  
- XGBoost  
- PyTorch  
- Folium / OpenStreetMap for visualization  
- Joblib for model serialization  

These technologies enable scalable data processing, model training, and interactive visualization.

---

# Conclusion

DeepDispatch demonstrates how combining **spatial clustering, feature engineering, machine learning, and deep learning** can transform historical taxi data into actionable mobility insights.
By forecasting revenue potential and visualizing it through an interactive heatmap, the system enables **data-driven fleet repositioning**, reducing wasted driving time and improving urban transportation efficiency.
