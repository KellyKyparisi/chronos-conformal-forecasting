# chronos-conformal-forecasting
Improving uncertainty calibration in pretrained time-series models using Conformal Prediction (Chronos-T5, M4 Daily).

# Conformal Prediction for Reliable Time-Series Forecasting

## 📌 Project Overview
This repository contains my MSc thesis on improving uncertainty
quantification in pretrained time-series forecasting models using
Conformal Prediction.

The project focuses on Chronos-T5 Small, a pretrained Transformer-based
foundation model for time-series forecasting. While Chronos produces
accurate point and quantile forecasts, its prediction intervals are often
miscalibrated, meaning their stated confidence levels do not match
empirical coverage. This work applies Conformalized Quantile Regression
(CQR) as a lightweight, distribution-free post-processing step to restore
statistically valid uncertainty estimates without retraining the model.

## 🎯 Research Objective
To evaluate whether conformal calibration can correct the miscalibration
of Chronos’ probabilistic forecasts and produce reliable prediction
intervals in a zero-shot forecasting setting.

## 🧠 Methodology
- Model: Chronos-T5 Small (46M parameters), zero-shot inference
- Dataset: M4 Daily benchmark (4,227 time series)
- Forecast horizon: 14 days
- Quantiles: 0.05, 0.50, 0.95
- Calibration method: Conformalized Quantile Regression (CQR)
- Series-level split: 80% calibration / 20% test (no series overlap)

Calibration is performed per forecast horizon using nonconformity scores
derived from quantile residuals, ensuring valid finite-sample coverage.

## 📊 Key Results
| Metric | Uncalibrated | Calibrated (CQR) |
|------|--------------|------------------|
| Prediction Interval Coverage (PICP) | 0.744 | **0.863** |
| Interval Calibration Error (ICE) | 0.155 | **0.036** |
| Sharpness (Interval Width) | 449.41 | 555.46 |
| Winkler Interval Score | 1052.92 | **964.48** |
| Pinball Loss (τ = 0.5) | 78.49 | 78.49 |

Conformal calibration substantially improves empirical coverage and
reduces calibration error, while preserving median forecast accuracy and
only modestly widening prediction intervals.

## Tech Stack
- Python 3.10
- PyTorch
- Chronos Forecasting (Amazon Science)
- Forecasting Evaluation Framework (FEV)
- NumPy, pandas, matplotlib
  
## For Recruiters
This project demonstrates:
- Applied machine learning for time-series forecasting
- Uncertainty quantification beyond point accuracy
- Model-agnostic calibration methods
- Research-grade evaluation and reproducibility

## 📄 Thesis
**Conformal Prediction for Reliable Uncertainty Quantification in Chronos
Time-Series Forecasting**  
BSc Computer Science  
University of Crete

