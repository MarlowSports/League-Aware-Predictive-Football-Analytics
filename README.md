# League-Aware-Predictive-Football-Analytics

Project Overview

This project implements a scalable, automated pipeline for predicting football match outcomes using historical performance data, opponent context, and time-aware trend modeling. The system generates match-level expected goals for home and away teams across multiple leagues, leveraging opponent-normalized features and moving-form trend analysis.

Key Features

Opponent-Normalized Metrics

Historical team statistics are scaled relative to each past opponent’s performance and projected against the upcoming opponent, creating strength-adjusted, context-aware features.

Time-Aware Trend Modeling

Employs ranked linear regression (analogous to Excel’s LINEST) to extrapolate expected goals from the last N matches, capturing moving-form dynamics while accounting for recency.

League-Aware Hierarchical Modeling

Implements a nested Group Loop in KNIME: first by league, then by team, ensuring models are trained on contextually homogeneous datasets.

Teams with fewer than 5 historical matches are excluded to maintain predictive reliability.

Integrated Match-Level Predictions

Combines predicted home and away performance to produce expected goals and goal difference for upcoming fixtures.

Fully automated for bulk execution of hundreds of matches.

Modular and Scalable

Designed for easy integration of new leagues, seasons, or additional statistical features.

Workflow is fully reproducible and adaptable for betting analytics, fantasy sports, or advanced statistical modeling.

Data Sources

Historical match results and team-level statistics from Football-Data.co.uk

Futures fixtures for prediction, including home/away team identifiers and league context

Pipeline Architecture

1. Data Preprocessing & Feature Engineering

Rank past matches chronologically per team

Construct team-centric datasets (home vs. away separation)

Calculate opponent-adjusted, context-aware statistics

2. Predictive Modeling

Linear regression per team (ranked by date)

Predict next-match expected goals using MaxRank + 1

Floor negative predictions to 0 for realism

3. Integration & Match-Level Outputs

Merge home and away predictions for each fixture

Compute derived metrics such as predicted goal difference

Optional Enhancements

Integration with Google Sheets or other data sources for live predictions

Extension to additional leagues or advanced statistical features (xG, possession trends, shots on target)

Probabilistic outcome modeling using Poisson regression or Monte Carlo simulations
