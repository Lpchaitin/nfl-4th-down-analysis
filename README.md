# NFL 4th Down Decision Model

## Article
[The NFL's 4th Down Problem Isn't What You Think](https://docs.google.com/document/d/1DQQqfEyn4NBig2NrpASjEkl9HZpnhtpCmDx7z5I63BE/edit?usp=sharing)

## Overview
This project analyzes 39,367 4th down plays across 10 NFL seasons (2016–2025) to evaluate coaching decision quality. Using play-by-play data from nfl_data_py and an XGBoost classifier, we model the optimal 4th down decision for every situation and compare it against what coaches actually did — quantifying who makes the best and worst decisions and what it costs them in win probability.

## Key Findings
- NFL go-for-it rates have nearly **doubled from 13% in 2016 to 23% in 2025**, driven by the analytics revolution
- **Field position is the dominant factor** in coaching decisions, with win probability and score differential playing a surprisingly minor role
- Contrary to popular belief, coaches are **more often too aggressive than too conservative** — 1,575 too-aggressive plays vs 879 too-conservative plays across the dataset
- A clear **generational divide** exists: almost every coach above league average aggressiveness was hired after 2020
- **Aggressiveness ≠ decision quality** — Kellen Moore ranks last in WPA despite being one of the most aggressive coaches in the dataset, while Andy Reid and Zac Taylor generate strong positive WPA without being the most aggressive

## Methodology
- **Data source:** nfl_data_py / nflverse (play-by-play, 2016–2025)
- **Model:** XGBoost classifier predicting optimal decision (go, punt, field goal)
- **Features:** field position, yards to go, score differential, win probability, game time, quarter, goal-to-go
- **Evaluation:** 91% accuracy on held-out test set; coach decisions compared against model recommendations
- **Disagreement analysis:** plays classified as too aggressive, too conservative, or aligned with model

## Repo Structure
nfl-4th-down-analysis/
├── data/
│   ├── raw/              # Raw play-by-play parquet files (not tracked)
│   └── processed/        # Filtered 4th down dataset (not tracked)
├── notebooks/
│   ├── 01_data_pull.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_modeling.ipynb
│   └── 04_coach_analysis.ipynb
├── outputs/
│   ├── figures/          # All saved visualizations
│   └── models/           # Saved model files (not tracked)
├── src/
├── requirements.txt
└── README.md

## How to Run
1. Clone the repo
2. Install dependencies: `pip install -r requirements.txt`
3. Run notebooks in order: `01 → 02 → 03 → 04`
4. Data will be downloaded automatically in notebook 01

## Visualizations
- Go-for-it rate by season (2016–2025)
- Go-for-it rate by field position
- Go-for-it rate by yards to go
- Most vs least aggressive coaches
- Coach aggressiveness trends over time
- Direction of disagreements by coach
- Feature importance
- Win probability added by coach

## Data Source
Play-by-play data pulled via [nfl_data_py](https://github.com/nflverse/nfl_data_py) — credit to the nflverse contributors.