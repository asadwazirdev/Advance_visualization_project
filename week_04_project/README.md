# NYC Taxi Data Analysis

Data preprocessing, NumPy and advanced visualization on the NYC Taxi Trip Duration dataset.

## What this project does
1. Data loading
2. Data cleaning (missing values, duplicates, invalid trips)
3. Feature engineering (time features, Haversine distance, speed, categories)
4. Feature scaling (Min-Max, Standardization)
5. Feature encoding (Label, One-hot)
6. NumPy implementation (slicing, aggregation, math operations)
7. Interactive Plotly charts (geo map, density map, animations, sunburst) and a GIF
8. Processed dataset and an auto-generated final report

## Dataset
Download `train.csv` from Kaggle: https://www.kaggle.com/datasets/yasserh/nyc-taxi-trip-duration

Rename it to `NYC.csv` and put it in the same folder as the notebook. The file is large, so it is not included in this repository.

## Setup
```bash
pip install pandas numpy scikit-learn plotly kaleido imageio pillow matplotlib nbformat
```
To save the GIF with Plotly, run `plotly_get_chrome` once. If Chrome is missing, the notebook falls back to matplotlib.

## Run
Open `nyc_taxi_preprocessing_01.ipynb` and run all cells. Outputs are saved in the `outputs/` folder, and the report is written to `NYC_Taxi_Final_Report.md`.

## Files
- `nyc_taxi_preprocessing_01.ipynb` - main notebook
- `NYC_Taxi_Final_Report.md` - generated report with insights
- `outputs/` - charts, animations and GIF
