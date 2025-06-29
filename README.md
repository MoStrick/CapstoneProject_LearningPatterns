# CapstoneProject_LearningPatterns
NWMSU Capstone Project: As digital education becomes more widespread, platforms collect massive amounts of behavioral data that can help educators and designers personalize instruction. Understanding how students approach learning — their speed, accuracy, and engagement — can lead to more adaptive systems and better outcomes.
#Key Components
  - Data preprocessing with pandas
  - KMeans clustering from scikit-learn
  - Visualization with matplotlib and seaborn
  - Dimensionality reduction with t-SNE
  - Interpretive analysis of clusters based on features


# Project pdf in overleaf: <https://www.overleaf.com/read/ddqttstjsspz#d36425>

# Project Workflow
  1. Data Exploration & Cleaning
    Load and merge log.csv, tag.csv
    Clean missing or malformed rows
  2. Feature Engineering
    Generate user-level features: accuracy, time per question, topic diversity
  3. Standardization
    Normalize features for clustering
  4. Clustering
    Use KMeans to find learning behavior groups
    Evaluate with silhouette score
  5. Dimensionality Reduction & Visualization
    Apply t-SNE or UMAP
    Visualize clusters
  6. Interpretation
    Describe characteristics of each cluster
    Suggest educational interventions
  7. Limitations
    No deep temporal sequence modeling (e.g., LSTM or DKT)
    Only uses basic user-level aggregation, not time-series
    No true causal inference (just pattern discovery)  
    Assumes all interactions are equally weighted (could improve with weighted models)


