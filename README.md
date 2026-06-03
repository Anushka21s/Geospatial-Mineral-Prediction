# ⛏️ Geospatial Mineral Occurrence Prediction using Machine Learning

> A machine learning–powered dashboard that predicts the probability of mineral deposits (Gold, Copper, Iron, Lithium, Manganese, Bauxite) across Indian geological survey regions using geochemical, geospatial, and geological parameters.

🔗 **Live App:** [mineralpredictor-gmxmd9valv9ct95ubokgmh.streamlit.app](https://mineralpredictor-gmxmd9valv9ct95ubokgmh.streamlit.app)

---

## 📌 Problem Statement

Identifying mineral-rich zones traditionally requires extensive manual field surveys — a process that is time-consuming and expensive. This project addresses that challenge by training a **Random Forest classifier** on synthetic geological survey data (modelled after real India mineral occurrence datasets) to predict which mineral is most likely present at any given location, based on its geochemical and geological signature.

---

## 🎯 Key Features

- 🔮 **Predict a Location** — Enter latitude, longitude, and deposit type to get mineral probability scores for all 6 mineral classes
- 🗺️ **Interactive Map** — Folium-powered map of 2,000 survey sites across India, colour-coded by mineral type with clickable popups
- 📊 **Dataset Explorer** — Browse raw data, geochemical boxplots, spatial scatter plots, and correlation heatmaps
- 🤖 **Model Evaluation** — Confusion matrix, per-class precision/recall/F1, and RF vs XGBoost comparison
- 📈 **Feature Importance** — Visual breakdown of which geochemical and geospatial features drive predictions
- 📍 **State-wise Analysis** — State × mineral heatmap and dominant mineral distribution across 15 Indian states

---

## 🧠 Machine Learning Pipeline

```
Raw geological survey data
        ↓
Feature engineering & preprocessing
(One-hot encoding · StandardScaler · Train/Test split)
        ↓
Random Forest Classifier (300 trees)   +   XGBoost (comparison)
        ↓
Mineral probability output (6 classes)
        ↓
Streamlit dashboard + Folium map
```

### Model Performance

| Metric | Score |
|---|---|
| RF Accuracy | ~89.9% |
| RF F1 Score (weighted) | ~88.5% |
| 5-fold Cross-validation | ~89.1% |
| XGBoost Accuracy | ~91.9% |

---

## 🪨 Minerals Predicted

| Mineral | Key Geochemical Signal | Primary States |
|---|---|---|
| 🟡 Gold | Very high Au ppb · Vein deposits | Karnataka, Andhra Pradesh, Rajasthan |
| 🟤 Copper | Very high Cu ppm · Porphyry/Skarn | Rajasthan, Jharkhand, MP |
| 🔴 Iron | Very high Fe% · Sedimentary | Odisha, Jharkhand, Chhattisgarh |
| 🔵 Lithium | Very high Li ppm · High elevation | Rajasthan, Karnataka, Andhra Pradesh |
| 🟣 Manganese | Very high Mn% · Low elevation | Odisha, Maharashtra, MP |
| 🟢 Bauxite | Very high Al% · Laterite deposits | Odisha, Jharkhand, Gujarat |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend / UI | Streamlit |
| ML Model | scikit-learn (Random Forest), XGBoost |
| Geospatial Mapping | Folium, GeoPandas, Shapely |
| Data Processing | Pandas, NumPy |
| Visualisation | Matplotlib, Seaborn |
| Deployment | Streamlit Community Cloud |

---

## 📁 Project Structure

```
mineral_predictor/
├── app.py                # Streamlit dashboard (6 pages)
├── data_generator.py     # Synthetic geological dataset generator
├── model.py              # ML training pipeline + grid prediction
├── map_renderer.py       # Folium map builder
└── requirements.txt      # Python dependencies
```

---

## 🚀 Run Locally

**1. Clone the repository**
```bash
git clone https://github.com/your-username/mineral-predictor.git
cd mineral-predictor
```

**2. Create and activate a conda environment**
```bash
conda create -n mineral_env python=3.10 -y
conda activate mineral_env
```

**3. Install dependencies**
```bash
conda install -c conda-forge numpy pandas scikit-learn matplotlib seaborn geopandas shapely folium -y
conda install -c conda-forge streamlit -y
pip install xgboost mapclassify
```

**4. Run the app**
```bash
streamlit run app.py
```

The app will open automatically at `http://localhost:8501`

---

## 📊 Dataset

The dataset is **synthetically generated** to mirror the structure of the real [India Mineral Ores dataset (Kaggle)](https://www.kaggle.com/), preserving authentic geochemical signatures for each mineral type based on real geological knowledge:

- **2,000 survey sites** across 15 Indian states
- **47 features** after one-hot encoding of categorical variables
- **6 target classes** (mineral types)
- Features include: latitude, longitude, elevation, Au/Cu/Fe/Li/Mn/Al concentrations, soil pH, fault proximity, deposit type, development status, production size

---

## 💡 How the Prediction Works

Each mineral has a distinct geochemical fingerprint in the real world:
- **Iron ore** sites show Fe% > 55 — the model learns this threshold
- **Gold** sites show Au concentrations in the thousands of ppb near fault lines
- **Bauxite** sites have Al% > 28 on laterite plateaus

The Random Forest learns these patterns across all 47 features and applies them to predict the most probable mineral at any new location — effectively acting as a **decision-support system** for geological prospecting.

---

## 👤 Author

**Satis** — Connect on [LinkedIn](#) | [GitHub](#)

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
