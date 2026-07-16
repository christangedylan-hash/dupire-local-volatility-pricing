# Dupire Local Volatility Calibration & Exotic Option Pricing

> Status: Work in progress

This project aims to implement a local volatility calibration framework from an implied volatility surface using Dupire’s formula.

The goal is to understand how market option prices can be used to construct a local volatility surface, and how this calibrated model can then be used for Monte Carlo pricing of vanilla and path-dependent options.

## Project Overview

Black-Scholes assumes a constant volatility parameter. However, in real markets, implied volatility varies across strikes and maturities, creating a volatility smile or volatility surface.

The local volatility model extends Black-Scholes by allowing volatility to depend on both time and the underlying asset price:

```text
sigma_local = sigma_local(t, S_t)
```

This project studies how to move from an implied volatility surface to a local volatility surface using Dupire’s formula, then uses the calibrated model for option pricing.

## Objectives

The project focuses on:

- implementing Black-Scholes pricing for European call and put options;
- computing Greeks such as Delta, Gamma and Vega;
- recovering implied volatility through numerical inversion;
- building an implied volatility surface across strikes and maturities;
- converting implied volatilities into option prices;
- applying Dupire’s formula to derive a local volatility surface;
- simulating asset paths under local volatility;
- pricing vanilla and barrier options using Monte Carlo simulation;
- analyzing numerical stability and model limitations.

## Methodology

The project follows a progressive approach.

First, Black-Scholes pricing is implemented and used as a benchmark model. Then, an implied volatility surface is constructed from synthetic option data. This surface is converted into call prices, which are used to compute the derivatives required in Dupire’s formula.

Once the local volatility surface is obtained, Monte Carlo simulations are performed under the local volatility dynamics:

```text
dS_t = (r - q) S_t dt + sigma_local(t, S_t) S_t dW_t
```

The resulting model is then used to price European and path-dependent options, with comparisons against Black-Scholes prices.

## Planned Repository Structure

```text
notebooks/
  01_black_scholes_and_implied_volatility.ipynb
  02_implied_volatility_surface.ipynb
  03_dupire_local_volatility_calibration.ipynb
  04_local_volatility_monte_carlo_pricing.ipynb

src/
  black_scholes.py
  implied_volatility.py
  volatility_surface.py
  local_volatility.py
  monte_carlo.py

references/
  README.md

README.md
```

## Roadmap

### Step 1 — Black-Scholes Pricing

- Implement European call and put pricing.
- Compute Greeks such as Delta, Gamma and Vega.
- Validate the implementation on simple numerical examples.

### Step 2 — Implied Volatility

- Implement numerical inversion of the Black-Scholes formula.
- Recover implied volatility from option prices.
- Study how implied volatility depends on strike and maturity.

### Step 3 — Implied Volatility Surface

- Build a synthetic implied volatility surface.
- Interpolate the surface across strikes and maturities.
- Convert implied volatilities into call prices.

### Step 4 — Dupire Local Volatility Calibration

- Approximate the derivatives of call prices with respect to strike and maturity.
- Implement Dupire’s formula.
- Construct the local volatility surface.
- Study the numerical stability of the calibration.

### Step 5 — Monte Carlo Pricing under Local Volatility

- Simulate asset paths under local volatility dynamics.
- Price European options.
- Price simple path-dependent options such as barrier options.
- Compare local volatility prices with Black-Scholes benchmark prices.

### Step 6 — Numerical Analysis and Limitations

- Analyze the sensitivity of the local volatility surface to interpolation choices.
- Discuss numerical noise from finite differences.
- Compare constant volatility and local volatility assumptions.
- Identify the limitations of the local volatility model.

## References

- Bruno Dupire, *Pricing with a Smile*.
- Jim Gatheral, *The Volatility Surface*.
- Julien Guyon and Pierre Henry-Labordère, *The Smile Calibration Problem Solved*.
- Lorenzo Bergomi, *Stochastic Volatility Modeling*.

## Tech Stack

- Python
- NumPy
- pandas
- scipy
- matplotlib
- Monte Carlo simulation
- Numerical differentiation
- Option pricing

## Current Status

The project is currently in progress.

The first development phase focuses on reviewing Black-Scholes pricing, Greeks, implied volatility and basic Monte Carlo simulation before moving to Dupire local volatility calibration.

## Disclaimer

This project is for academic and educational purposes only. It does not constitute financial advice or a production-ready pricing library.
