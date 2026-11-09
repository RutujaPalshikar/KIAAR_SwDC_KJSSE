# Satellite-Based Crop Health & Soil Moisture Monitoring

## Overview
This repository contains the end-to-end data pipeline and machine learning workflow developed during my internship under Software Development Cell under KJ Somaiya School of Engineering for K. J. Somaiya Institute of Applied Agricultural Research (KIAAR). The project focuses on automated crop health and soil moisture monitoring across diverse agricultural regions in India. By leveraging multi-source satellite imagery (including Sentinel-2 and Planet data) and geospatial processing platforms like Google Earth Engine, the project calculates key vegetation indices to assess agricultural conditions across distinct seasonal cycles.

## Features
* **Automated Geospatial Data Pipeline:** Fetches and processes high-resolution satellite imagery from Sentinel-2 and Planet data using Google Earth Engine and the Sentinel Hub API based on defined bounding boxes.
* **Vegetation Index Calculation:** Extracts and computes critical agricultural metrics including:
  * NDVI (Normalized Difference Vegetation Index)
  * SAVI (Soil Adjusted Vegetation Index)
  * NDMI (Normalized Difference Moisture Index)
  * EVI (Enhanced Vegetation Index)
  * REVI (Red-Edge Vegetation Index)
* **Data Pre-processing:** Cleans time-series data by removing NaNs and invalid values, and applies Z-score standardization (clipped to [-1, 1]) for model readiness.
* **Predictive Machine Learning Models:** Implements several architectures for crop stage classification and time-series forecasting:
  * **Decision Trees & XGBoost:** Classifies crop stages into 'Delayed', 'Immature', or 'Harvest-ready' using static and dynamic vegetation thresholds.
  * **LSTM (Long Short-Term Memory):** Utilizes historical NDVI sequences to forecast future vegetation health and yield potential.
* **Geospatial Visualization:** Generates 2D classification maps and heatmaps showing crop stages across different geographic indices, alongside confusion matrices for model evaluation.

## Technologies & Libraries
* **Language:** Python 3
* **Geospatial & Cloud Platforms:** Google Earth Engine (GEE), Sentinel Hub API
* **Spatial Data Processing:** `rasterio`, `geopandas`, `shapely`
* **Data Manipulation & Math:** `pandas`, `numpy`
* **Machine Learning:** `scikit-learn`, `xgboost`, `tensorflow`/`keras` (for LSTM)
* **Visualization:** `matplotlib`, `seaborn`

## Repository Structure
The repository consists of standalone Jupyter Notebooks dedicated to specific models and regions:

*   `KIAAR_crop_harvest_XGboost model desert validation.ipynb` - XGBoost validation for desert regions.
*   `KIAAR_crop_harvest_XGboost model fertile region validation.ipynb` - XGBoost model applied to fertile regions.
*   `KIAAR_crop_harvest_XGboost model.ipynb` - Base XGBoost model for crop harvest prediction.
*   `KIAAR_crop_harvest_decision_trees.ipynb` - Base Decision Tree model.
*   `KIAAR_crop_harvest_decision_trees_all_VI_s.ipynb` - Decision Trees utilizing all computed vegetation indices.
*   `KIAAR_crop_harvest_decision_trees_desert_validation.ipynb` - Decision Tree validation for desert regions.
*   `KIAAR_soil moisture_linear_regression_KIAAR region.ipynb` - Linear regression for soil moisture in the KIAAR region.
*   `KIAAR_soil moisture_linear_regression_K_taka(Western Ghats).ipynb` - Linear regression for soil moisture (Karnataka/Western).
*   `KIAAR_soil moisture_naive bayes_KIAAR region.ipynb` - Naive Bayes modeling for the KIAAR region.
*   `KIAAR_soil moisture_naive bayes_K_taka(Western Ghats).ipynb` - Naive Bayes modeling (Karnataka/Western).
*   `KIAAR_soil moisture_naive bayes_Thar region.ipynb` - Naive Bayes modeling for the Thar desert region.

## Installation & Setup

1. **Clone the repository:**
    ```bash
    git clone [[https://github.com/YOUR_USERNAME/KIAAR_SwDC_KJSSE.git](https://github.com/YOUR_USERNAME/KIAAR_SwDC_KJSSE.git)](https://github.com/RutujaPalshikar/KIAAR_SwDC_KJSSE)
    cd KIAAR_SwDC_KJSSE
    ```

2. **Install required dependencies:**
    Ensure you have Python installed, then install the necessary libraries to run the notebooks:
    ```bash
    pip install jupyter pandas numpy scikit-learn xgboost matplotlib seaborn
    ```

3. **Launch Jupyter Notebook:**
    Start the Jupyter environment to view and run the `.ipynb` files:
    ```bash
    jupyter notebook
    ```

## Project Workflow
1. **Data Loading:** Each notebook imports the pre-processed satellite imagery datasets.
2. **Model Training:** Models (XGBoost, Decision Trees, Linear Regression, Naive Bayes) are trained on specific regional subsets (e.g., Thar region, Fertile regions).
3. **Evaluation:** Models are validated against regional data to ensure accuracy in predicting crop harvest readiness and soil moisture levels.
