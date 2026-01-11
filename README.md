# Hypothesis Testing

## Research Objective
Evaluate whether a dynamic equity exposure strategy based on volatility targeting and volatility mispricing regimes reduces **maximum drawdown** of the Nifty 50 compared to a static buy-and-hold strategy.

---

## H₀ (Null Hypothesis)
Maximum drawdown of the Nifty 50 does not differ between a dynamic equity exposure strategy based on volatility targeting & volatility mispricing regimes and a static buy-and-hold exposure.  

$H_0:\ \max(DD_{\text{dynamic}}) = \max(DD_{\text{buy\&hold}})$  

---

## H₁ (Alternative Hypothesis)
Maximum drawdown of the Nifty 50 is lower under a dynamic equity exposure strategy based on volatility targeting & volatility mispricing regimes compared to a static buy-and-hold exposure.  

$H_1:\ \max(DD_{\text{dynamic}}) < \max(DD_{\text{buy\&hold}})$

---

## Methodology

- Constructed a baseline **buy-and-hold** portfolio on the Nifty 50 index.
- Designed a **dynamic equity exposure strategy** where allocation is adjusted based on:
  - Forecasted volatility levels
  - Volatility mispricing regimes (realized vs forecast volatility)
- Exposure was scaled down during high-volatility regimes and scaled up during low-volatility regimes.
- Portfolio performance was evaluated using **maximum drawdown** as the primary risk metric.
- All strategies were tested over the same sample period to ensure comparability.

---

## Volatility Forecasting Models

The following models were implemented and compared:

1. **EWMA Model**
   - Exponential weighting
   - Captures time-varying volatility with fast reaction to shocks

2. **GARCH(1,1), Mean = 0**
   - Standard symmetric volatility model
   - Assumes zero conditional mean in returns

3. **GARCH(1,1), Mean = Constant**
   - Accounts for non-zero average returns
   - Separates mean dynamics from volatility clustering

---

## Assumptions

- The analysis uses the Nifty 50 index-level time series rather than a reconstructed constituent portfolio. This mitigates survivorship bias at the security-selection level, as the index reflects historical constituent additions and removals by the index provider.
- Transaction costs, taxes, and liquidity constraints are ignored.
- Volatility forecasts are assumed to be available without delay.
- Model parameters are estimated using rolling windows to avoid look-ahead bias.
- Leverage constraints are not explicitly modeled; exposure is capped implicitly.
- The Nifty 50 index is assumed to be investable without tracking error.

---

## Model Limitations

- EWMA may overreact to short-term shocks during crisis periods.
- GARCH models assume symmetric volatility response and may understate tail risk.
- Structural breaks and extreme regime shifts may reduce forecast accuracy.
- Results are sensitive to window length, decay factors, and rebalancing frequency.
- Maximum drawdown is path-dependent and may vary with start/end dates.

---

## Results

1. Max Drawdown – Buy & Hold: **−38.44%**  
2. *Max Drawdown – EWMA:* **−18.30%**  
3. *Max Drawdown – GARCH(1,1), Mean = 0:* **−16.57%**  
4. *Max Drawdown – GARCH(1,1), Mean = Constant:* **−15.70%**  

---

## Conclusion

Reject $H_0$ and accept $H_1$.

Dynamic equity exposure strategies based on volatility targeting and volatility mispricing regimes significantly reduce maximum drawdown of the Nifty 50 compared to a static buy-and-hold approach. The results are robust across multiple volatility forecasting models, with GARCH-based strategies delivering the strongest drawdown reduction.

---

## Reproducibility & Robustness

- All assumptions, model specifications, and parameter choices are explicitly documented.
- Results are reproducible using the same data, windowing scheme, and rebalancing rules.
