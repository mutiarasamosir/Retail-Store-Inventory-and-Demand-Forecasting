# Retail Store Inventory & Demand Forecasting

![Python](https://img.shields.io/badge/Python-3.11-blue) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange) ![Statsmodels](https://img.shields.io/badge/Statsmodels-0.14.0-green)

## Deskripsi Singkat
Notebook ini menganalisis data permintaan (demand) pada toko retail menggunakan dataset sintetis.  
Tujuannya:  
- Memprediksi demand harian.  
- Mengevaluasi dampak promosi (`Promotion`) dan epidemi (`Epidemic`).  
- Memberikan rekomendasi stok berbasis forecast.

Dataset bersifat **synthetic**, dibuat untuk latihan forecasting & analisis inventory.

## Dataset
- Dataset terdiri dari 16 kolom, termasuk:  
  `Date`, `Demand`, `Promotion`, `Epidemic`, `Category`, `Store ID`, dll.  
- Rentang data: 2022-01-01 → 2024-01-30  
- Jumlah total record: 76.000  
- Digunakan untuk:  
  - Latihan time series forecasting.  
  - Analisis dampak faktor eksternal (Promo, Epidemic) terhadap demand.

## Analisis & Langkah Notebook
Notebook ini terdiri dari beberapa tahap:

1. **Data Loading & Validation**  
   - Memastikan kolom penting ada, tipe data benar, dan tidak ada missing date.

2. **Exploratory Data Analysis (EDA)**  
   - Tren demand harian, rolling mean, bulanan, dan per weekday.  
   - Dampak promosi (`Promotion`) dan epidemi (`Epidemic`) terhadap demand.  
   - Heatmap interaksi bulan x weekday.

3. **Feature Engineering**  
   - Fitur berbasis waktu: `dayofweek`, `month`, `quarter`, `is_weekend`.  
   - Lag features: `lag_1`, `lag_7`, `lag_14`.  
   - Rolling mean: `roll_mean_7`, `roll_mean_30`.  
   - Heatmap korelasi fitur numerik.

4. **Train/Test Split**  
   - Split berbasis waktu (time-based) 80% train / 20% test.

5. **Baseline Forecasting**  
   - **Naive Forecast:** besok = hari ini  
   - **Moving Average (7 hari)**  
   - Evaluasi: MAE & RMSE  
   - Visualisasi distribusi demand dan forecast

6. **SARIMAX dengan Exogenous Features**  
   - Model SARIMAX(1,1,1)(1,1,1,7) dengan `Promotion` & `Epidemic`.  
   - Forecast vs actual & confidence interval.  
   - Interpretasi koefisien:  
     - **Promo** positif → meningkatkan demand  
     - **Epidemic** negatif → menurunkan demand  
   - Evaluasi: MAE & RMSE

## Hasil Utama
- 📊 **Baseline Moving Average 7 hari:**  
  - MAE = 34.16  
  - RMSE = 43.40
- 📈 **SARIMAX (dengan Promo & Epidemic):**  
  - MAE = 1181.76  
  - RMSE = 1305.37
- ✅ Promo terbukti meningkatkan demand, Epidemic menurunkan demand.
- 🖼️ Visualisasi tren & forecast tersedia di notebook.
- 
Lihat detail analisis & plot di ([Retail_Forecasting.ipynb](https://github.com/mutiarasamosir/Retail-Store-Inventory-and-Demand-Forecasting/blob/main/Retail%20Store%20Inventory%20and%20Demand%20Forecasting.ipynb))
