# 00 FO Desk Workflow – General Option Pricing Perspective

This note summarizes the **general workflow of a front-office options desk**.
It is intended as a conceptual framework for any underlying (Equity, Commodity, FX, Rates) and any vanilla or exotic option.

---

## 1. Market Data & Observables

FO desk starts with the **market data universe**:

- Underlying prices:
  - Spot price S₀
  - Forward/futures prices F(t,T)
- Vanilla option quotes:
  - Market price or implied volatility
  - Standard strikes and maturities (high liquidity)
- Yield/discount curves for present value
- Conventions:
  - Day count
  - Settlement rules
  - Delivery periods (for commodities)

**Key point:**  
Only **observable market data** can be used for calibration. All model parameters should tie back to these.

---

## 2. Implied Parameters & Calibration

- **Implied volatility:** Derived from market price using chosen pricing model
- **Other model parameters:** e.g., mean-reversion κ, long-term level θ, vol of vol, jump intensity
- Calibration ensures **model prices match market prices** for liquid instruments
- Output:
  - Model parameters ready for pricing and Greeks
  - Basis for risk and P&L attribution

**FO use:**  
- Trader relies on calibrated model to quote new instruments
- Ensures consistency between desk price and market

---

## 3. Pricing & Greeks

- **Pricing model:**  
  - Vanilla: BS, Heston, OU, etc.
  - Exotic: Monte Carlo, PDE, trees, closed-form if available
- **Greeks calculation:**  
  - Delta, Gamma, Vega, Theta, Rho, etc.
  - Provide hedge ratios
- **Workflow:**  
  1. Plug inputs (F/K, T, σ, r, etc.) into pricing function
  2. Compute price
  3. Compute Greeks

**FO purpose:**  
- Price → trader quote to client or internal desk
- Greeks → determine hedge positions

---

## 4. Hedge & Risk Management

- Trader hedges **market risks** (delta, vega, theta) in real time
- Quant provides:
  - Sensitivity calculations
  - Scenario analysis (Monte Carlo paths)
  - P&L attribution: how much P&L comes from spot move, volatility change, time decay
- Hedge adjustment is **dynamic**; recomputed as market moves

---

## 5. Exotic Options / Illiquid Products

- Exotics often **illiquid** → hedged with standard vanillas
- FO logic:
  - Price and hedge exotics using **vanilla building blocks**
  - Monte Carlo or PDE to generate Greeks for path-dependent risks
- Desk workflow remains the same: **market → model → quote → hedge → P&L**

---

## 6. Daily / Continuous Loop

Typical FO desk operates in a **continuous loop**:
- Market moves → recompute forward curve, vol surface
- Any new trade → price and quote immediately
- Daily close → full P&L attribution

---

## 7. Key Takeaways for a FO Quant

1. **Model ≠ prediction**  
   - Model provides **market-consistent prices and Greeks**
2. **Calibration is essential**  
   - Every parameter must have market backing
3. **Greeks guide trader action**  
   - Hedge ratios, risk limits, P&L attribution
4. **Workflow is modular**  
   - Market data, model, calibration, pricing, hedge, P&L

> In interviews, this general workflow shows you **understand the desk perspective**: how a quant bridges market data, models, and trader decisions.
