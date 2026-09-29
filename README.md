# Genre-Based User Clustering for Movie Recommendation

## Overview

This project was developed for the **Introduction to Data Science** course.

The main objective is to analyze user rating behavior and group users based on their movie genre preferences using **K-Means clustering**. Instead of representing users with thousands of individual movie ratings, the project constructs a compact **User × Genre preference matrix** using mean-centered ratings.

The clustering result is then used as the basis for a simple **cluster-based movie recommendation module**.

---

## Dataset

The project uses the **MovieLens Small Dataset**.

Main files used:

- `movies.csv` — movie IDs, titles, and genres.
- `ratings.csv` — user ratings for movies.

Dataset summary:

- **610 users**
- **9,742 movies**
- **100,836 ratings**
- **19 genres**
- Rating scale: **0.5 – 5.0**

---

## Methodology

The main pipeline is:

```text
MovieLens ratings + movies
        ↓
Genre One-Hot Encoding
        ↓
Mean-Centered Ratings
        ↓
User × Genre Matrix
        ↓
StandardScaler
        ↓
K-Means Clustering
        ↓
User Preference Clusters
        ↓
Cluster-Based Recommendation
```

### 1. User Preference Representation

For each user and genre, the project calculates a centered preference score:

```text
Centered Preference = Mean Rating for Genre - User's Overall Mean Rating
```

This reduces differences in individual rating scales and allows the clustering process to focus more on relative genre preferences.

The resulting feature matrix contains:

```text
610 users × 19 genre features
```

### 2. K-Means Clustering

K-Means is applied to the standardized User × Genre matrix.

The number of clusters is selected using multiple criteria:

- SSE / Elbow Method
- Silhouette Score
- Cluster-size analysis
- Stability across multiple random seeds

The final selected configuration is:

```text
K = 5
```

Final cluster sizes:

| Cluster | Number of Users |
|--------:|----------------:|
| 0 | 107 |
| 1 | 279 |
| 2 | 63 |
| 3 | 25 |
| 4 | 136 |

The clusters represent different patterns of movie genre preference.

### 3. Cluster-Based Recommendation

After clustering, recommendations are generated using ratings from other users in the same cluster.

For each candidate movie, the system considers:

- Average rating within the cluster
- Number of ratings within the cluster
- Movies already watched by the target user

Candidate movies are ranked using:

```text
score = avg_rating × log(1 + rating_count)
```

The recommendation module is a **downstream application of the clustering result**, while K-Means user clustering remains the main machine learning task of the project.

---

## Repository Structure

```text
.
├── Midterm_Present (3).pptx
├── README.md
├── Report DS.pdf
├── finalDS.ipynb
├── midterm.ipynb
├── movies.csv
├── project summary document.docx
└── ratings.csv
```

### File Description

| File | Description |
|------|-------------|
| `finalDS.ipynb` | Final notebook containing preprocessing, EDA, user-genre feature construction, K-Means clustering, cluster analysis, and recommendation implementation. |
| `midterm.ipynb` | Notebook used for the midterm stage, mainly focusing on dataset exploration and visualization. |
| `movies.csv` | Movie information including movie ID, title, and genres. |
| `ratings.csv` | User-movie rating data used for analysis and modeling. |
| `Midterm_Present (3).pptx` | Presentation slides used for the midterm presentation. |
| `Report DS.pdf` | Final project report describing the methodology, experiments, results, evaluation, and discussion. |
| `project summary document.docx` | Summary document providing an overview of the project and its main components. |
| `README.md` | Overview and documentation of the repository. |

---

## Main Results

The final model uses **K = 5** user clusters.

The clustering analysis shows that user preference groups are not strongly separated, but the selected configuration provides:

- Usable cluster sizes
- Reasonable stability across random seeds
- Interpretable genre-preference profiles
- A practical basis for cluster-based recommendation

The recommendation demonstration shows how the learned user segments can be used to generate Top-N movie recommendations from users with similar preference patterns.

---

## Limitations

Current limitations include:

- User preference changes over time are not modeled.
- Genre distribution is imbalanced.
- User-generated tags are not included in the feature representation.
- New-user profiles are approximated using selected favorite genres.
- Recommendation quality has not yet been evaluated using dedicated ranking metrics such as Precision@K, Recall@K, or NDCG.

---

## Future Work

Possible extensions include:

- Time-aware user preference modeling
- Genre weighting or imbalance handling
- Integration of user-generated tags
- Improved cold-start strategies
- Quantitative evaluation of recommendation quality

---

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Scikit-learn
- Jupyter Notebook

---

## Authors

**Group 8**  
Introduction to Data Science Project
