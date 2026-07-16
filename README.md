# Dupire Local Volatility Calibration & Exotic Option Pricing

> Status: Work in progress

This project aims to implement a local volatility calibration framework from an implied volatility surface using Dupire’s formula.

The objective is to understand how market option prices can be used to construct a local volatility surface, and how this calibrated model can then be used for Monte Carlo pricing of vanilla and path-dependent options.

## Objective

The project focuses on:

- implementing Black-Scholes pricing for European options;
- building an implied volatility surface across strikes and maturities;
- converting implied volatilities into option prices;
- applying Dupire’s formula to derive a local volatility surface;
- simulating asset paths under local volatility;
- pricing vanilla and barrier options using Monte Carlo;
- analyzing numerical stability and model limitations.

## Motivation

Black-Scholes assumes a constant volatility, but market option prices imply different volatilities depending on strike and maturity.

The local volatility model addresses this limitation by introducing a volatility function depending on time and the underlying price:

```text
sigma_local = sigma_local(t, S_t)
```
This project is designed as a practical introduction to volatility surface calibration and equity derivatives pricing.
