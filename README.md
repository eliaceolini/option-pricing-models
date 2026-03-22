# Option Pricing Models with Monte Carlo

This project implements and compares three advanced option pricing frameworks widely used in quantitative finance:

- Heston Stochastic Volatility Model
- Merton Jump-Diffusion Model
- Local Volatility Model (Dupire)

The goal is to analyze their ability to reproduce implied volatility surfaces and to assess their impact on pricing both vanilla and exotic derivatives.

---

## 🔍 Objectives

- Calibrate each model to a synthetic implied volatility surface
- Compare pricing accuracy on European options
- Evaluate model performance on path-dependent exotic options:
  - Asian options
  - Barrier options (Down-and-Out)
  - Cliquet options

---

## ⚙️ Methodology

### Volatility Surface Construction
A realistic implied volatility surface is generated analytically as a function of maturity and log-moneyness, reproducing:
- Negative skew
- Volatility smile
- Term structure effects

### Model Calibration
Model parameters are calibrated by minimizing pricing errors vs Black-Scholes benchmark prices:

- **Heston** → Nelder-Mead optimization  
- **Merton** → Differential Evolution (global optimization)

### Pricing
- Monte Carlo simulations are used for all models
- Time discretization at daily frequency
- Pricing performed for both vanilla and exotic options

---

## 📊 Results

### Calibration Performance (RMSE)

| Model     | RMSE (Total) |
|----------|-------------|
| Heston   | 0.27        |
| Merton   | 0.31        |
| Local Vol| 0.07        |

- Local Vol provides the best fit by construction
- Heston captures skew via stochastic volatility
- Merton captures jump risk but introduces pricing bias

### Exotic Options Insights

- **Asian Options**: stable across models (path averaging effect)
- **Barrier Options**: highly sensitive to volatility dynamics
- **Cliquet Options**: strongest dispersion due to return distribution differences

---

## 🧠 Key Insights

- Model choice has limited impact on vanilla options but becomes critical for path-dependent derivatives
- Stochastic volatility improves realism but increases numerical complexity
- Jump processes capture tail risk but may distort drift dynamics
- Local volatility ensures perfect calibration but lacks forward consistency

---

## 🧪 Technologies

- Python
- NumPy
- SciPy
- Matplotlib

---

## 📁 Project Structure
- notebooks/ → main analysis and simulations
- report/ → full project report (PDF)

---

## 🚀 Possible Extensions

- Variance reduction techniques (Antithetic, Control Variates)
- Calibration to real market data
- GPU acceleration for Monte Carlo simulations

---

## Author

Elia Ceolini
