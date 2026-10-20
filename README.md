# XGBoost inverse model: reactor conditions from polymer microstructure

Predicts four reactor conditions of ethylene/1-octene copolymerization (P, [Al]/[Ti], C8 preload and reaction time) from three microstructural descriptors extracted from GPC curves (`LogM_Mean`, `WF_Max`, `SCB_Mean`), using KNN-based data augmentation and an XGBoost regressor.

The notebook has three blocks:

1. **Libraries and data loading**: imports, settings and input files.
2. **Data preprocessing and modeling**: train/test split, KNN augmentation, training, evaluation, model saving, bootstrap prediction intervals and GPC preprocessing. Everything is saved to `results/`.
3. **Figures**: independent of Block 2 in memory. It reads the saved model and data from `results/` and writes the figures to `figures/`, one folder per figure type.

**How to run:** place this notebook in the same folder as `xgbnew.xlsx` and `Dados_tratados_2.xlsx`.
First run: Block 1 → Block 2 → Block 3. To regenerate only the figures: Block 1 → Block 3.

```
project_folder/
├── xgbnew.xlsx, Dados_tratados_2.xlsx
├── results/
│   ├── models/        xgboost_scenario_1.pkl, xgboost_scenario_2.pkl
│   ├── data/          train/test split, augmented training sets, processed GPC data
│   ├── uncertainty/   prediction_intervals.csv, interval_metrics.csv
│   └── model_metrics.csv
└── figures/
    ├── 01_model_fit/
    ├── 02_target_distributions/
    ├── 03_augmented_data/
    ├── 04_targets_vs_microstructure/
    ├── 05_gpc_mwd/
    ├── 06_gpc_scb/
    └── 07_prediction_intervals/
```

Tested with Python 3.12, pandas 3.0, scikit-learn 1.8, xgboost 3.4, matplotlib 3.10 and seaborn 0.13.


