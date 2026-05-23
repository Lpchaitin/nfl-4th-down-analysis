# NFL 4th Down Decision Analysis

## Article
[A 4th Down Breakdown (2016-2025)](https://docs.google.com/document/d/1DQQqfEyn4NBig2NrpASjEkl9HZpnhtpCmDx7z5I63BE/edit?usp=sharing)

## Overview
This project analyzes 39,367 4th down plays across 10 NFL seasons (2016-2025) to evaluate coaching decision quality, play design effectiveness, and defensive strategy on 4th down. Using play-by-play data from nflverse and an XGBoost classifier, we model the optimal 4th down decision for every situation, then go deeper into formations, personnel packages, and defensive alignments to understand not just whether coaches should go for it, but how they should execute and what defenses should do to stop them.

## Key Findings
- NFL go-for-it rates have nearly **doubled from 13% in 2016 to 23% in 2025**
- **Field position dominates decision making** over win probability and score differential
- Coaches are **more often too aggressive than too conservative**, 1,575 too-aggressive plays vs 879 too-conservative
- A clear **generational divide** exists: almost every coach above league average aggressiveness was hired after 2020
- **Shotgun converts at only 47%** despite being used on 62% of go-for-it plays, while Under Center converts at 70%
- **Heavy personnel packages dramatically outperform spread packages**: 12 personnel with no WRs converts at 75% vs 44% for 4-wide sets
- **Zone coverage stops 4th down conversions at 58%** vs 49% for man coverage
- **Seattle and New England are the best 4th down defenses**; Las Vegas Raiders are the worst at 36% stop rate
- **Andy Reid is the best go-for-it coach** by conversion rate, EPA, and WPA across every metric

## Methodology
- **Data source:** nfl_data_py / nflverse (play-by-play, 2016-2025)
- **Model:** XGBoost classifier predicting optimal decision (go, punt, field goal)
- **Features:** field position, yards to go, score differential, win probability, game time, quarter, goal-to-go
- **Evaluation:** 91% accuracy on held-out test set
- **Formation analysis:** offensive formation, personnel packages, defenders in box, coverage type

## Repo Structure

nfl-4th-down-analysis/
├── data/
│   ├── raw/              # Raw play-by-play parquet files (not tracked)
│   └── processed/        # Filtered 4th down dataset (not tracked)
├── notebooks/
│   ├── 01_data_pull.ipynb
│   ├── 02_eda.ipynb
│   ├── 03_modeling.ipynb
│   ├── 04_coach_analysis.ipynb
│   ├── 05_go_for_it_analysis.ipynb
│   ├── 06_formation_analysis.ipynb
│   └── 07_defensive_analysis.ipynb
├── outputs/
│   └── figures/          # All saved visualizations
├── src/
├── requirements.txt
└── README.md

## How to Run
1. Clone the repo
2. Install dependencies: `pip install -r requirements.txt`
3. Run notebooks in order: `01 → 07`
4. Data downloads automatically in notebook 01

## Visualizations
- Go-for-it rate by season (2016-2025)
- Go-for-it rate by field position
- Go-for-it rate by yards to go
- Most vs least aggressive coaches
- Coach aggressiveness trends over time
- Direction of disagreements by coach
- Feature importance
- Win probability added by coach
- Conversion rate by yards to go and play type
- Play type usage by yards to go
- Coach conversion rates
- Average EPA per go-for-it play by coach
- Formation conversion rate and EPA
- Personnel package conversion rate and EPA
- Defenders in box conversion rate
- Stop rate by coverage type
- Man vs zone stop rate
- Team stop rate

## Data Source
Play-by-play data pulled via [nfl_data_py](https://github.com/nflverse/nfl_data_py) — credit to the nflverse contributors.