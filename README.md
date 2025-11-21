# Wind Turbine Power Prediction Project

**Author:** Tibo Stans  
**Course:** Machine Learning 2025 - VUB  
**Final Score:** 9.10 MAE (91.6% improvement from baseline)

---

## Hi there! 👋

Welcome to my Machine Learning project for the 2025 VUB course. This repository contains my complete work on predicting wind turbine power output based on weather and operational data.

It's been quite a journey from a simple linear regression baseline (which was... not great, at 108.82 MAE) to a highly optimized ensemble model that achieved a score of **9.10 MAE**. I'm pretty proud of the result, especially since it's only 0.47 kW away from the top leaderboard score!

## Project Structure

I've organized the project to be as clean and reproducible as possible. Here's where everything lives:

```
final_project/
├── code/                              # The core logic (Jupyter Notebooks)
│   ├── 01_exploratory_data_analysis_and_baseline.ipynb     # Start here! EDA + Feature Engineering + First XGBoost
│   ├── 02_hyperparameter_optimization.ipynb   # Tuning the best model with Optuna
│   ├── 03_ensemble_methods.ipynb # Combining XGBoost, LightGBM, and CatBoost
│   └── 04_neural_network_approach.ipynb # A deep learning experiment (for comparison)
├── data/                              # The dataset
│   ├── training_data.csv              # Input data for training
│   └── test_data.csv                  # Data for generating submissions
├── models/                            # Where trained models are saved
│   └── (pkl and pt files will appear here after running notebooks)
├── results/                           # Submission files and plots
│   └── (CSVs and PNGs will be generated here)
├── report/                            # The formal academic report
│   └── report.tex                     # LaTeX source
└── README.md                          # You are here!
```

## How to Run This Code

I've set everything up so you can run it step-by-step.

### 1. Get Ready
First, make sure you have Python installed (I used 3.10). You'll need a few libraries:

```bash
pip install pandas numpy scikit-learn xgboost lightgbm catboost optuna torch matplotlib seaborn
```

### 2. Follow the Story
The notebooks are numbered for a reason—they tell the story of how I built the solution.

1.  **Notebook 01 (`01_exploratory_data_analysis_and_baseline.ipynb`)**:
    *   I start by exploring the data and cleaning it up.
    *   I create about 40 new features (this was the biggest game-changer!).
    *   I train a baseline XGBoost model.
    *   *Result:* ~9.30 MAE.

2.  **Notebook 02 (`02_hyperparameter_optimization.ipynb`)**:
    *   I take that XGBoost model and use Optuna to find the perfect hyperparameters.
    *   It runs for 50 trials to squeeze out every bit of performance.
    *   *Result:* ~9.15 MAE.

3.  **Notebook 03 (`03_ensemble_methods.ipynb`)**:
    *   I bring in LightGBM and CatBoost to add diversity.
    *   I combine them using a weighted ensemble.
    *   *Result:* **9.10 MAE** (My best score!).

4.  **Notebook 04 (`04_neural_network_approach.ipynb`)**:
    *   I tried a Neural Network (PyTorch MLP) just to see if it could beat the trees.
    *   Spoiler: It didn't (tabular data loves trees!), but it was a cool experiment.

## Key Takeaways & Lessons Learned

If I had to summarize what I learned from this project:

*   **Feature Engineering is King:** No amount of hyperparameter tuning could match the boost I got from adding physics-based features like `wind_power_theoretical` (using the $P = \frac{1}{2}\rho A v^3$ formula).
*   **Know Your Data:** Realizing that the turbine has distinct states (like "shutdown" or "rated power") helped me understand why simple models failed.
*   **Ensembles Help (a little):** Blending models gave me that final 0.05 improvement, but the solid foundation was built in step 1.
*   **Neural Networks aren't Magic:** For this kind of structured data with 200k rows, Gradient Boosting is just faster and more accurate.

## Future Ideas

If I had more time, I'd love to try:
*   **State-Specific Models:** Training separate models for when the turbine is starting up vs. when it's running at full power.
*   **Sequence Models:** Using LSTMs to capture the time-series nature of the wind data better.
*   **More External Data:** Maybe adding local weather station data could help with the outliers.

## The Report

For the full academic breakdown, check out `report/report.tex`. It has all the math, graphs, and formal analysis.

---
*Thanks for checking out my project!*
