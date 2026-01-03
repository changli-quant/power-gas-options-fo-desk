# 01 Market Conventions – Power & Gas Desk

This note summarizes the key market conventions that drive pricing, calibration, and hedging decisions on a Power/Gas front-office desk.

---

## 1. Spot, Forward, and Futures

- **Spot (S)**: Current price for immediate delivery. Highly volatile, especially electricity.
- **Forward (F)**: Agreed price today for delivery at a future date (usually monthly/quarterly). Used as underlying for vanilla option pricing.
- **Futures**: Exchange-traded, standardized contracts. Similar prices to forwards but with daily marking-to-market.

**FO takeaway:** Forward price is usually the underlying for European vanilla options.

---

## 2. Commodity vs Equity

- **Seasonality**: Predictable patterns (daily, monthly, yearly). Structural, not noise. Modeled in forward curve as deterministic component.
- **Mean reversion**: Spot prices tend to revert to long-term levels → OU-type dynamics for risk analysis.
- **Non-storability (power)**: Extreme spikes in spot price. Affects forward curve construction and risk modeling.

---

## 3. Liquidity & Standardization

- Most liquidity: standard strikes/maturities & vanilla options.
- Exotics (barrier, spread, knock-in/out) exist but illiquid → hedged with vanilla options.
- Market conventions determine:
  1. Observable data → calibratable points
  2. Parameters → OU σ, κ, θ_t
  3. Risks trader actually hedges → Delta, Vega, Theta

---

## 4. Forward Curve & Dynamics

- **Forward curve** = snapshot of delivery prices today (static)
- **Forward dynamics** = model of how forward evolves (OU, Gabilon, Samuelson)
- Vanilla option pricing: take forward at valuation date → plug into BS
- Portfolio/risk simulation: use dynamics to generate future paths

---

## 5. Day Count & Discounting

- Use ACT/365 and zero-coupon discount curve for present value
- Necessary for BS price and Greeks
