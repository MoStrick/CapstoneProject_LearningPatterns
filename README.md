# CapstoneProject_LearningPatterns
NWMSU Capstone Project: As digital education becomes more widespread, platforms collect massive amounts of behavioral data that can help educators and designers personalize instruction. Understanding how students approach learning — their speed, accuracy, and engagement — can lead to more adaptive systems and better outcomes.
#Key Components
  - Data preprocessing with pandas
  - KMeans clustering from scikit-learn
  - Visualization with matplotlib and seaborn
  - Dimensionality reduction with t-SNE
  - Interpretive analysis of clusters based on features


# Project pdf in overleaf: <https://www.overleaf.com/read/ddqttstjsspz#d36425>


# Capstone Project: Clustering Student Learning Behaviors

As digital education becomes more widespread, platforms collect massive amounts of behavioral data that can help educators and designers personalize instruction. Understanding how students approach learning — their speed, accuracy, and engagement — can lead to more adaptive systems and better outcomes. :contentReference[oaicite:0]{index=0}

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Repository Structure](#repository-structure)  
3. [Data Description](#data-description)  
4. [Installation & Setup](#installation--setup)  
5. [Usage & Notebooks](#usage--notebooks)  
6. [Results & Metrics](#results--metrics)  
7. [Roadmap & Next Steps](#roadmap--next-steps)  
8. [Contact](#contact)  

# Project Workflow
  1. Data Exploration & Cleaning
    - Load and merge log.csv, tag.csv
    - Clean missing or malformed rows
  2. Feature Engineering
    - Generate user-level features: accuracy, time per question, topic diversity
  3. Standardization
    - Normalize features for clustering
  4. Clustering
    - Use KMeans to find learning behavior groups
    - Evaluate with silhouette score
  5. Dimensionality Reduction & Visualization
    - Apply t-SNE or UMAP
    - Visualize clusters
  6. Interpretation
    - Describe characteristics of each cluster
    - Suggest educational interventions
  7. Limitations
    - No deep temporal sequence modeling (e.g., LSTM or DKT)
    - Only uses basic user-level aggregation, not time-series
    - No true causal inference (just pattern discovery)  
    - Assumes all interactions are equally weighted (could improve with weighted models)

---

## Project Overview
This repository contains all code, data artifacts, and documentation for the NWMSU Capstone Project. We:
- Cleaned and merged four EdNet interaction datasets (KT1–KT4).  
- Performed exploratory data analysis on response times, accuracy, and engagement patterns.  
- Built regression pipelines (Random Forest & XGBoost) to predict student response times.  
- Applied KMeans clustering and t‑SNE for groupings of learning behaviors.

---

## Repository Structure
```

.
├── Data.md                        ← Detailed schema & data dictionary
├── requirements.txt               ← Python dependencies
├── Data\_Cleaning.ipynb            ← Ingest & clean raw CSVs
├── Merge\_Data.ipynb               ← Concatenate KT1–KT4 into Parquet
├── EDA.ipynb                      ← Exploratory plots & missingness checks
├── ML\_Response\_Time\_Regression.ipynb
│   └── ML pipeline, CV tuning, evaluation
├── student\_behavior\_features.parquet
├── clustered\_student\_features.parquet
└── README.md                      ← (this file)

````

---

## Data Description
See **Data.md** for full data dictionary.  
Briefly, the merged Parquet (`EdNet_full_log.parquet`) contains:

| Column           | Type      | Description                                    |
|------------------|-----------|------------------------------------------------|
| timestamp        | datetime  | When the question was attempted                |
| question_id      | string    | Unique question identifier                     |
| user_answer      | string    | Student’s selected option                       |
| elapsed_time     | int (ms)  | Time taken to answer (filtered ≤ 30 min)       |
| user_id          | string    | Pseudo–anonymized student identifier           |
| part             | int       | Problem set category (1–…); for feature encoding|
| tags             | array     | Content tags for question topics               |

---

## Installation & Setup
1. **Clone the repo**  
   bash
   git clone https://github.com/MoStrick/CapstoneProject_LearningPatterns.git
   cd CapstoneProject_LearningPatterns


2. **Create & activate virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate    # macOS/Linux
   venv\Scripts\activate       # Windows
   ```
3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```



## Usage & Notebooks

Each Jupyter notebook is a standalone pipeline stage:

* **Data\_Cleaning.ipynb**
  · Skip empty logs, drop missing/outlier elapsed times, convert timestamps.
* **Merge\_Data.ipynb**
  · Standardize schemas and concatenate KT1–KT4 into `EdNet_full_log.parquet`.
* **EDA.ipynb**
  · Visualize distributions, missingness, and basic correlations.
* **ML\_Response\_Time\_Regression.ipynb**
  · Build scikit‑learn & XGBoost pipelines; perform 5‑fold CV; report RMSE & MAE.
* **Clustering (notebook)**
  · Generate user‑level features and apply KMeans + t‑SNE to reveal behavior clusters.

To run a notebook:

```bash
jupyter lab
# or
jupyter nbconvert --to html Data_Cleaning.ipynb
```

---

## Results & Metrics

| Model           | RMSE (s) | MAE (s) | Notes                       |
| --------------- | -------- | ------- | --------------------------- |
| Baseline (mean) | 185      | 140     | Global mean predictor       |
| Random Forest   | 118      | 90      | After hyperparameter tuning |
| XGBoost         | 107      | 82      | Best performing model       |

---

## Roadmap & Next Steps

* **Interpretability**: Generate SHAP plots to explain model predictions.
* **Temporal Models**: Explore sequence models (LSTM, DKT) for next‑question prediction.
* **Deployment**: Wrap pipeline into a REST API or Streamlit app for demonstration.
* **Additional Features**: Incorporate bundle‑level and lecture metadata in feature set.

---

## Contact

Molly Strickland — [missm@nwmsu.edu](mailto:missm@nwmsu.edu)
Project repo: [https://github.com/MoStrick/CapstoneProject\_LearningPatterns](https://github.com/MoStrick/CapstoneProject_LearningPatterns)
Overleaf report: [https://www.overleaf.com/read/ddqttstjsspz#d36425](https://www.overleaf.com/read/ddqttstjsspz#d36425)
