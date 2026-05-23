<h1 align="center">
F1 Pattern Recognition: Driver Behavior Analysis using <br> Machine Learning and Clustering Algorithms
</h1>

---

## 📝 Abstract

<div align="justify">
This project identifies and analyzes distinct behavioral patterns in Formula 1 driver performance across 75 years of racing data (1950-2024). Using a combination of unsupervised learning techniques (K-Means, DBSCAN, Hierarchical Clustering) and dimensionality reduction (PCA), we classify drivers into three distinct behavioral archetypes: Consistent Climbers, Midfield Stabilizers, and Volatile Drivers.
</div> <br> <div>
The analysis engineers 7 behavioral features from position change metrics, normalizes them using StandardScaler, and applies statistical significance testing (permutation tests, chi-square tests) to validate clustering results. Supervised learning models (Random Forest, Linear Regression) are trained using 5-fold cross-validation to predict driver performance characteristics, achieving a 37.9% improvement over naive baselines.
</div> <br>

<div align="justify">
The project leverages 26,759 historical race records from the Kaggle F1 dataset, validates results on 2024 season data, and generates 12 publication-ready visualizations and 9 data export files documenting cluster assignments, transition matrices, and model performance metrics.
</div>

---

## 📁 Repository Structure

```bash
ApexFlow/
├── notebooks/
│   └── f1_analysis.ipynb               # Main analysis notebook
├── data/
│   ├── archive.zip                     # Historical F1 data (1950-2023)
│   ├── archive (1).zip                 # 2024 season data
│   ├── results.csv                     # Race results (26,759 records)
│   ├── qualifying.csv                  # Qualifying data (10,494 records)
│   ├── drivers.csv                     # Driver metadata
│   ├── races.csv                       # Race information
│   └── [other extracted datasets]
├── outputs/
│   ├── behavioral_space.png            # PCA cluster visualization
│   ├── pca_behavioral_space.png        # 2D behavioral space
│   ├── k_selection.png                 # Elbow curve for K-Means
│   ├── dbscan_eps_selection.png        # K-distance elbow plot
│   ├── dbscan_outliers_pca.png         # Outlier detection results
│   ├── cluster_over_time.png           # Era-based cluster composition
│   ├── era_cluster_composition.png     # Stacked area chart
│   ├── hierarchical_clustering.png     # Dendrogram (Ward linkage)
│   ├── driver_longitudinal.png         # Driver trajectory visualization
│   ├── permutation_test.png            # Significance test results
│   ├── transition_heatmap.png          # Season-to-season transitions
│   ├── supervised_comparison.png       # Model comparison results
│   ├── cluster_summary.csv             # Mean features per cluster
│   ├── driver_clusters.csv             # Driver cluster assignments
│   ├── driver_clusters_2024.csv        # 2024 validation results
│   ├── driver_season_clusters.csv      # Historical assignments
│   ├── driver_trajectories.csv         # Transition data
│   ├── cluster_transitions.csv         # Transition matrix
│   ├── transition_asymmetry.csv        # Chi-square test results
│   ├── era_cluster_proportions.csv     # Era-based proportions
│   └── supervised_model_comparison.csv # 5-fold CV metrics
├── requirements.txt                    # Python dependencies
├── .gitignore                          # Git configuration
└── README.md                           # This file
```

---

## 🎯 Key Features

- **Unsupervised Clustering** — K-Means (k=3), DBSCAN (auto eps), and Hierarchical (Ward linkage) to identify behavioral patterns
- **Dimensionality Reduction** — PCA with 2 principal components for 2D behavioral space visualization
- **Feature Engineering** — 7 behavioral metrics: avg_gain, gain_pct, volatility, p10_gain, p90_gain, gain_per_qual_rank, teammate_delta_avg
- **Statistical Validation** — Permutation significance test (p = 0.000) and chi-square contingency tests on driver transitions
- **Supervised Learning** — Random Forest regressor with 5-fold CV achieving MAE = 2.567 ± 0.045 (37.9% improvement)
- **Temporal Analysis** — Era-based clustering analysis (Pre-1994, 1994-2009, 2010+) and driver longitudinal trajectory tracking
- **External Validation** — 2024 season performance validation against historical models
- **Publication-Ready Outputs** — 12 visualizations and 9 CSV exports documenting all results

---

## 🛠️ Technologies Used

| Category | Technology |
|----------|-----------|
| **Language** | Python 3.10+ |
| **ML Libraries** | scikit-learn 1.2+, pandas 1.5+, numpy 1.23+ |
| **Visualization** | matplotlib 3.6+, seaborn 0.12+ |
| **Statistics** | scipy 1.9+ |
| **Notebook** | Jupyter 1.0+, IPython 8.0+ |
| **Development** | VS Code, Git, GitHub |

---

## 📊 Features Engineered

| Feature | Description |
|---------|-------------|
| `avg_gain` | Mean position change across races |
| `gain_pct` | % of races with positive position gains |
| `volatility` | Std deviation of position changes |
| `p10_gain` | 10th percentile position change |
| `p90_gain` | 90th percentile position change |
| `gain_per_qual_rank` | Position gain normalized by qualifying rank |
| `teammate_delta_avg` | Average finish position vs teammate |

---

## ⚙️ Local Setup Instructions

### 1. Prerequisites
- Python 3.10 or higher
- pip package manager
- Git

### 2. Clone Repository
```bash
git clone https://github.com/Bharadwaj-1953/ApexFlow.git
cd ApexFlow
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Run Notebook
```bash
jupyter notebook notebooks/f1_analysis.ipynb
```

The notebook will execute all 54 cells, performing the complete analysis pipeline and generating all visualizations and exports to the `outputs/` directory.

---

## 🧪 Testing & Results

### Clustering Results
- **K-Means Optimal k**: 3 (determined via elbow method)
- **Permutation Test**: p = 0.000 (highly significant)
- **Adjusted Rand Index (Hierarchical vs K-Means)**: 0.3868

### Driver Archetypes Identified

**Consistent Climbers** (Green #2ecc71)
- High avg_gain and gain_pct, low volatility
- Reliable position improvements from grid
- Examples: Lewis Hamilton, Senna era drivers

**Midfield Stabilizers** (Blue #3498db)
- Near-zero avg_gain, moderate volatility
- Consistent midfield performance
- Limited upward mobility

**Volatile Drivers** (Red #e74c3c)
- High volatility, high p90_gain
- Unpredictable performance, high-risk style
- Inconsistent lap-to-lap pace

### Supervised Learning Performance

| Model | MAE | Improvement |
|-------|-----|-------------|
| Linear Regression | 3.256 | 22.4% |
| Random Forest (5-fold CV) | 2.567 ± 0.045 | 37.9% |

*Baseline (Naive): 4.194*

---

## 📊 Data Statistics

- **Historical Race Records**: 26,759 (1950-2024)
- **Qualifying Records**: 10,494
- **Driver-Seasons Analyzed**: 604
- **2024 Validation Drivers**: 24
- **Features Engineered**: 7
- **Output Files Generated**: 21 (12 PNG + 9 CSV)



## 🌐 Contact

- **Email**: manne.bharadwaj.1953@gmail.com
- **LinkedIn**: [Bharadwaj Manne](https://www.linkedin.com/in/bharadwaj-manne-711476249/)
- **GitHub**: [Bharadwaj-1953](https://github.com/Bharadwaj-1953)

---
