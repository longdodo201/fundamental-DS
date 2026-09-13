# MovieLens Exploratory Data Analysis

## Overview

This project performs **Exploratory Data Analysis (EDA)** on the MovieLens dataset.

The main goal is to understand:

* User rating behavior
* Movie popularity
* Genre distribution
* User interaction with different genres
* User activity
* Movie distribution by release year

For the midterm stage, this project focuses on **data understanding, data preparation, visualization, and insights**.

The recommendation part will be developed later in the final stage.

---

## Dataset

The project uses two main files from the MovieLens dataset:

### `movies.csv`

Contains movie information:

* `movieId`
* `title`
* `genres`

### `ratings.csv`

Contains user rating information:

* `userId`
* `movieId`
* `rating`
* `timestamp`

The two datasets are connected by:

```text
movieId
```

### Dataset Summary

* **610 users**
* **9,742 movies**
* **100,836 ratings**
* Average rating: approximately **3.5 / 5**

---

## Project Workflow

```text
MovieLens Raw Data
        ↓
Data Understanding
        ↓
Data Quality Check
        ↓
Data Preparation
        ↓
Exploratory Data Analysis
        ↓
Visualization
        ↓
Key Insights
```

---

## Data Preparation

The main preparation steps include:

### 1. Data Quality Check

The dataset is checked for:

* Missing values
* Duplicate rows
* Duplicate user-movie ratings
* Invalid rating values

The MovieLens dataset is already relatively clean, so no major missing-value problems were found.

### 2. Merge Datasets

`movies.csv` and `ratings.csv` are merged using:

```python
movieId
```

The merged dataset contains:

```text
userId
movieId
rating
timestamp
title
genres
```

### 3. Extract Release Year

The release year is extracted from the movie title.

Example:

```text
Toy Story (1995)
```

becomes:

```text
Title: Toy Story (1995)
Year: 1995
```

### 4. Process Genres

A movie can belong to multiple genres.

Example:

```text
Adventure|Animation|Children|Comedy|Fantasy
```

The genres are separated so that each genre can be analyzed individually.

---

## Exploratory Data Analysis

The EDA focuses on four main areas.

### Rating Analysis

We study the distribution of user ratings.

Main observation:

* Most ratings are between **3 and 5**
* Very low ratings appear less often
* The average rating is around **3.5**

---

### Movie Analysis

We analyze movies using:

* Number of ratings
* Average rating

An important idea is:

```text
Popularity ≠ Average Rating
```

A movie can receive many ratings but not have the highest average score.

Movies with very few ratings may also have very high average scores, so rating count should be considered together with average rating.

---

### Genre Analysis

Genre analysis includes:

* Number of movies by genre
* Number of ratings by genre
* Average rating by genre

An important observation is:

```text
Genre availability ≠ User interaction
```

A genre can receive many ratings partly because the dataset contains many movies from that genre.

Therefore, a high number of ratings does not automatically mean that users prefer that genre the most.

---

### User Analysis

We analyze:

* Number of ratings per user
* Most active users

The dataset shows that user activity is not equal.

Some users provide many ratings, while many users provide fewer ratings.

This is important for future recommendation analysis because active users provide more information about their preferences.

---

### Movie Distribution by Year

Movie release years are also analyzed.

The dataset includes movies from many different periods.

More movies appear in recent decades than in very early years.

This visualization represents the **coverage of the MovieLens dataset**, not the real number of movies produced worldwide each year.

---

## Key Insights

The main findings from the midterm analysis are:

1. Most ratings are concentrated in the middle-to-high range.
2. Movie popularity and average rating are different concepts.
3. Some genres contain significantly more movies than others.
4. Genre availability and user interaction are related but not identical.
5. Average rating should be considered together with rating count.
6. User activity is different across users.
7. The dataset contains movies from a wide range of release years.

---

## Technologies

This project uses:

* Python
* Pandas
* NumPy
* Matplotlib
* Jupyter Notebook / Google Colab

---

## Project Structure

```text
MovieLens-EDA/
│
├── data/
│   ├── movies.csv
│   └── ratings.csv
│
├── midterm.ipynb
│
├── presentation/
│   └── MovieLens_Midterm_Final.pdf
│
└── README.md
```

---

## How to Run

### 1. Clone the repository

```bash
git clone <your-repository-url>
```

### 2. Open the project

You can run the notebook using:

* Jupyter Notebook
* JupyterLab
* Google Colab
* VS Code

### 3. Install required libraries

```bash
pip install pandas numpy matplotlib
```

### 4. Run the notebook

Open:

```text
midterm.ipynb
```

and run the cells from top to bottom.

---

## Future Work

For the final stage, the project can be extended from EDA to a simple movie recommendation approach.

Possible next steps include:

```text
User Rating History
        ↓
User Preference Analysis
        ↓
User Clustering
        ↓
Similar Users / Similar Preferences
        ↓
Movie Recommendation
```

Possible methods include:

* User preference vectors
* K-Means clustering
* cluster based recomendation

The EDA from the midterm provides the foundation for these later steps.

---

## Authors

USTH – Introduction to Data Science Project

Midterm Topic:

**Exploratory Data Analysis of MovieLens Ratings**
