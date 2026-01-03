# 02 Option Quotes and Vol – Power & Gas Desk

This note explains how market option quotes and implied volatilities are used in a front-office desk.

---

## 1. Market Quotes

- Market provides vanilla European option quotes at **standard strikes/maturities**.
- Quote example: `"42–45 vol"` → 42–45% annualized implied volatility.
- Quote can be **price** or **implied volatility**.
- FO workflow: convert price → implied vol (calibration), or read vol → compute price.

---

## 2. Moneyness

- **Definition**: Moneyness = F/K (forward moneyness preferred)
- Interpret:
  - <1 → OTM, =1 → ATM, >1 → ITM
- Used to locate vol on **vol surface**.

---

## 3. Vol Surface

- 2D surface: moneyness (X-axis) × maturity (Y-axis) → implied vol (Z-axis)
- Purpose:
  1. Ensure pricing consistent with market
  2. Provide input for BS Greeks calculation
- Determining vol:
  - Locate moneyness + maturity point
  - Interpolate if needed
- Used in BS formula → price + Greeks → trader quote/hedge

---

## 4. Implied Vol vs Historical Vol

- Historical vol: past realized volatility
- Implied vol: deduced from market price using BS
- FO care about **implied vol** → matches market pricing

---

## 5. Calibration

- **Calibration** = reverse-engineering parameters from market quotes
  - Example: given market price → solve BS formula for σ → implied vol
  - Ensures your model produces prices consistent with market
- Calibration is **daily task** on FO desk, foundation for P&L and hedge
