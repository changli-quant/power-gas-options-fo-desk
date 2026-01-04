# 03 Black-Scholes Role on Desk – Power & Gas European Option

This note explains how BS formula is used in a FO desk for European options on Power/Gas.

---

## 1. Pricing Vanilla European Options

- BS formula computes price of call/put under **lognormal GBM assumption**
- Inputs:
  - Forward price F, Strike K, Maturity T
  - Discount factor e^{-rT}
  - Volatility σ (from vol surface)
- Output:
  - Price
  - Greeks: Delta, Vega, Theta
- FO desk: BS price = quote to client; Greeks = hedge parameters

---

## 2. Vol Selection

- Use **vol surface** at option's moneyness
- Moneyness = F/K
- Interpolate if necessary
- Guarantees consistency with market

---

## 3. Hedge & Trader Interaction

- Trader **does not trust BS prediction of future price**
- Use BS Greeks to **hedge actual risk**:
  - Delta → adjust underlying position
  - Vega → adjust volatility exposure
  - Theta → account for time decay
- Quant provides **tools and analysis**; Trader executes hedge

---

## 4. Forward Dynamics / Monte Carlo (Optional)

- Vanilla option pricing: **MC not needed**
- Forward dynamics (OU, Samuelson) used for:
  - Portfolio P&L simulation
  - Scenario analysis
  - Exotic options
- MC generates paths → compute price/Greeks → support trader decision

---

## 5. FO Workflow – Summary

1. **Market Data** → forward curve, vanilla quotes, vol surface  
2. **Determine Inputs** → F, K, T, σ  
3. **BS Pricing** → price + Greeks  
4. **Trader Hedge / Quote** → Delta/Vega/Theta  
5. **Optional Forward Dynamics / MC** → risk/scenario analysis  
6. **P&L Attribution** → delta/vega/theta P&L  
7. **Daily Update** → repeat as market evolves
