# Moneyball 2.0 — AI Football Scouting System

## Project Overview

Moneyball 2.0 is a data-driven football scouting project that uses machine learning and player analytics to identify promising and potentially undervalued central midfielders.

The project applies K-Means clustering and a custom Scouting Value Score to support budget-oriented transfer decisions.

## Objectives

- Analyze football player attributes and estimated values.
- Identify different profiles of central midfielders using K-Means.
- Develop a multi-criteria player ranking system.
- Identify young players with strong development potential.
- Compare the proposed ranking approach with a Potential-only baseline.

## Dataset

Source: FIFA 23 Complete Player Dataset  
Kaggle: https://www.kaggle.com/datasets/stefanoleone992/fifa-23-complete-player-dataset

After filtering FIFA 23 records and removing duplicate player IDs:

- Unique players: 20,621
- Central midfielders analyzed: 2,429
- Players with complete scoring features: 2,422

The original dataset is not included in this repository because of its large size.

## Technologies

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- K-Means Clustering
- PCA
- Google Colab

## Methodology

### 1. Data Preparation
The dataset was filtered to FIFA 23, duplicate player records were removed, and relevant player attributes were selected.

### 2. Feature Engineering
Additional features were created, including:

- Potential Gap = Potential − Overall
- Value in Millions
- Primary Position

### 3. Clustering
K-Means was applied to 2,429 central midfielders using six attributes:

- Pace
- Shooting
- Passing
- Dribbling
- Defending
- Physic

The analysis produced three player clusters.

### 4. Scouting Value Score
A custom weighted ranking system was developed:

- Performance Score: 25%
- Potential Score: 30%
- Development Score: 20%
- Affordability Score: 15%
- Age Score: 10%

### 5. Candidate Selection
The final budget-oriented candidate pool used the following filters:

- Age ≤ 23
- Overall ≥ 65
- Potential ≥ 80
- Estimated value ≤ €5 million

## Results

The clustering analysis identified three groups of central midfielders:

| Cluster | Players | Average Age | Average Overall | Average Potential |
|---|---:|---:|---:|---:|
| 0 | 628 | 27.31 | 74.02 | 76.23 |
| 1 | 597 | 20.46 | 55.79 | 67.23 |
| 2 | 1,204 | 24.87 | 64.74 | 69.83 |

The final candidate pool contained 48 players.

Leading candidates included:

- Andrey Santos
- M. Perrone
- A. Scott
- M. Kjaergaard
- L. Ugochukwu

## Baseline Evaluation

The Scouting Score was compared with a baseline that ranks players by Potential alone, using the same pool of 48 candidates.

| Metric | Baseline | Scouting Score |
|---|---:|---:|
| Average Overall | 68.33 | 68.80 |
| Average Potential | 83.47 | 82.07 |
| Average Age | 18.93 | 19.47 |
| Total Estimated Value | €47.4M | €48.1M |

The Scouting Score selected players with a slightly higher average Overall, while the baseline had a higher average Potential and lower total estimated value.

The proposed model therefore provides an alternative ranking strategy, but the evaluation does not establish that it is economically superior to the baseline.

## Limitations

- FIFA 23 estimated player values are historical game-based estimates, not current transfer prices.
- FIFA Potential is not observed future performance.
- Match-level statistics and playing time were not included.
- Injury history and contract conditions were unavailable.
- The first listed position was used as the primary position.
- K-Means clustering is sensitive to feature selection and the chosen number of clusters.
- The Scouting Value Score is a heuristic ranking system, not a supervised prediction model.

## Conclusion

Moneyball 2.0 demonstrates how machine learning and multi-criteria ranking can support preliminary football scouting.

The system identifies promising young midfielders and provides a structured shortlist for further investigation. It should be used as a decision-support tool alongside real-world scouting and performance analysis.

## Reproducibility

The analysis was developed in Google Colab. Install the required libraries from `requirements.txt`, download the dataset from Kaggle, and run the notebook from top to bottom.
