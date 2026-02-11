
# FX Option Valuation — Summary of Steps & Numerical Results
This notebook demonstrates the valuation of an FX option using historical data, Monte Carlo simulation, and QuantLib. The process includes data acquisition, volatility estimation, forward rate computation, and option pricing.

## 1. Data Acquisition & Preparation
* **Timeframe:** Approximately 5 years of historical data prior to today.
* **FX Data Source:** Yahoo Finance (`EURUSD=X`) for EUR/USD spot rates.
* **Interest Rate Data Source:** FRED for 1-year risk-free rates:
  * USD: `DGS1`
  * EUR: `IRSTCI01EZM156N`
* **USD/EUR Spot Rates:** Converted by inverting EUR/USD.

## 2. Volatility Calculation
* Daily logarithmic returns were calculated from USD/EUR spot rates.
* **Historical Daily Volatility:** `0.0047`
* **Historical Annualized Volatility:** `0.0752`
  (Assuming 252 trading days)

## 3. Current Market Data & Parameters
| Parameter                 | Value              |
| ------------------------- | ------------------ |
| Latest USD/EUR Spot Rate  | `0.8400`           |
| USD 1-Year Risk-Free Rate | `0.0343`           |
| EUR 1-Year Risk-Free Rate | `0.0193`           |
| Time to Maturity (T)      | `5` years          |
| Option Strike Price       | `1.2000` (USD/EUR) |
| Notional Amount           | `1,000,000` USD    |
| Monte Carlo Simulations   | `10,000` paths     |
| Time Steps                | `1,260`            |

## 4. Forward FX Rate Calculations
* **Monte Carlo Estimated Forward FX Rate (USD/EUR):** `0.9055`
* **IRP (Interest Rate Parity) Forward FX Rate (USD/EUR):** `0.9055`
* **QuantLib Process Reconstructed Forward FX Rate (USD/EUR):** `0.7793`

## 5. FX Option Valuation (QuantLib Monte Carlo)
A European call option on USD/EUR was priced using a QuantLib Monte Carlo engine.
* **Monte Carlo Estimated FX Option NPV (per unit of EUR):** `0.0027`

## 6. Total FX Swaption Present Value
The total present value is calculated by multiplying the option NPV by the effective notional in EUR.
* **Effective Notional Amount (EUR):** `833,333.33`
* **Total Monte Carlo Estimated FX Swaption PV:** `2,245.4166` USD

## 7. Visualizations
The notebook includes visualizations to support the analysis:
* Historical USD/EUR spot rate trend
* Historical USD and EUR interest rate trends
* Sample Monte Carlo FX rate paths
* Distribution of final FX rates at maturity
<img width="1790" height="1145" alt="image" src="https://github.com/user-attachments/assets/6b04873d-21cb-4fc5-a2f3-cdbe7517e526" />

