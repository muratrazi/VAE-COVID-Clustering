# VAE-COVID-Clustering
# COVID-19 Time Series Clustering with Variational Autoencoders (VAE) 

This repository contains a complete pipeline for analyzing and clustering the COVID-19 mortality waves of 174 countries using a deep generative model (Variational Autoencoder - VAE) and K-Means clustering.

## 📌 Project Overview
Traditional time-series comparison methods like Dynamic Time Warping (DTW) are computationally expensive and highly sensitive to noise. This project takes a deep learning approach:
1. **Representation Learning:** A PyTorch VAE is trained to compress 3 years of daily COVID-19 death data (smoothed and normalized) into an 8-dimensional latent space.
2. **Clustering:** K-Means algorithm is applied to these extracted latent features (the "DNA" of the pandemic waves) to group 174 countries into 8 distinct clusters based on their pandemic patterns.

## 🚀 Key Features
- **Live Data Fetching:** Directly fetches the most up-to-date raw dataset from the Our World in Data (OWID) GitHub repository.
- **Robust Preprocessing:** Handles missing values, OWID duplicates, and applies 7-day rolling averages with Min-Max normalization.
- **Deep Learning Model:** End-to-end PyTorch implementation of a Variational Autoencoder.
- **Automated Output Generation:** - Exports an Excel file (`VAE_8_Clusters_Comparison.xlsx`) structuring countries under their assigned clusters.
  - Generates high-resolution plots (`VAE_Representative_Signals.png`) of the mean dynamic waves of each cluster.
  - Renders an interactive global choropleth map using precise ISO-3 codes via Plotly.

## 🛠️ Requirements
To run this script locally or on Google Colab, you will need the following libraries:
\`\`\`bash
pip install pandas numpy torch scikit-learn plotly matplotlib openpyxl
\`\`\`

## 📊 Outputs
Running the `main.py` (or notebook cell) will automatically generate the following:
1. **`VAE_8_Clusters_Comparison.xlsx`**: An Excel sheet containing the clustered countries structured in columns.
2. **`VAE_Representative_Signals.png`**: High-resolution plot showcasing the mean dynamic waves against the background signals of the countries in each cluster.
3. **Interactive Map**: A Plotly map rendered directly in your browser or IDE.

## 📝 Usage for Anomaly Detection or Prediction
The trained VAE acts as a powerful feature extractor. By passing a new country's normalized time-series data through the `model.enc_net()`, you can instantly locate its 8-dimensional coordinates in the latent space and predict its cluster using the trained K-Means model without having to recalculate pairwise distances like DTW requires.

## 📜 License
This project is open-source and available under the MIT License.
