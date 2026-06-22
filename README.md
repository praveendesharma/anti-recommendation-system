# Anti-Recommendation System: Expanding User Tastes Through Beneficial Discomfort

A multi-objective recommender system designed to combat filter bubbles by deliberately suggesting content outside users' comfort zones — while still ensuring they'll enjoy it.

## Overview

Traditional recommender systems optimize for immediate satisfaction, reinforcing existing preferences and narrowing user taste over time. This project introduces an **Anti-Recommendation System** that balances three competing objectives:

1. **Predicted enjoyment** — will the user actually like it?
2. **Genre diversity** — is it different from their usual choices?
3. **Content challenge** — will it expand their horizons?

The scoring function is:

```
AntiRecScore(u, i) = α · predicted_rating + β · diversity_score + γ · challenge_score
```

Optimal weights found: α=0.5, β=0.3, γ=0.2

## Key Results

- **40–60% increase** in recommendation diversity vs. standard collaborative filtering
- Only **10–15% drop** in predicted rating quality
- Introduced **2–4 new genres** on average per user (vs. 0–1 for standard recommenders)
- "Specialist" users (narrow taste profiles) benefit most from anti-recommendations

## Novel Evaluation Metrics

Standard RMSE/MAE don't capture diversity or exploration. We introduce:

- **Diversity Gain** — Shannon entropy of recommended genres minus history entropy
- **Challenge Acceptance Rate (CAR@K)** — fraction of challenging recommendations users would actually enjoy
- **Comfort Zone Escape (CZE@K)** — average distance of recommendations from user's taste centroid
- **Exploration Catalyst Score** — new genres explored in subsequent ratings after receiving anti-recommendations

## Dataset

[MovieLens 1M](https://grouplens.org/datasets/movielens/1m/) — 1 million ratings from 6,040 users on 3,706 movies.

## Models

- Baselines: Global average, user average, movie average
- Collaborative filtering (user-based and item-based)
- Matrix factorization (SVD)
- Anti-recommender: Matrix factorization + multi-objective scoring with diversity and challenge components

## Tech Stack

Python, NumPy, Pandas, Scikit-learn, Surprise (SVD)

## Course

CSE 158R — Web Mining and Recommender Systems, UC San Diego
