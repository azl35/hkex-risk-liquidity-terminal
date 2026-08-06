# US Capital Markets Risk & Execution Terminal 

A capital markets product prototype combining a **Python ETL data engine** with a **Google Sheets front-office execution terminal**. Built to demonstrate real-time ingestion of US equity market benchmarks (`SPY`), automated detection of market liquidity shocks, and dynamic execution routing recommendations for Tier-1 trading desks.

---

## Project Overview
* **Target Focus:** Front-office desk tools, risk management, and capital markets analytics.
* **Asset Benchmark:** SPDR S&P 500 ETF Trust (`SPY` / US Equities).
* **Key Metrics:** 
  * 30-Day Annualized Realized Volatility (%)
  * Parametric 1-Day Value-at-Risk ($95\%$ & $99\%$ CI on a $100K portfolio)
  * Amihud Liquidity Shock / Price Impact Index
  * **Automated Exception Handling Engine:** Rules-based system flagging high-stress market days and outputting execution rerouting guidance

---

## System Architecture

1. **Python Engine (`us_capital_markets_risk_engine.ipynb`):**
   * Fetches daily OHLCV market data via `yfinance`.
   * Calculates log returns, rolling annualized volatility, and parametric VaR.
   * Calculates the **Amihud Liquidity Impact Index**:
  $$\text{Amihud Index} = \frac{|\text{Return}|}{\text{Dollar Volume}} \times 10^{11}$$
   * Executes rule-based logic: Flags **Critical Stress** when 30-Day Volatility breaches $18.0\%$ **AND** Amihud Price Impact breaches the $85\text{th}$ percentile.
   * Exports structured CSV output

2. **Front-Office Dashboard (`US_Risk_Execution_Terminal_AlvinaLin.xlsx`):**
   * Terminal-style UI featuring KPI metric cards.
   * Visual charts highlighting risk stress trends and liquidity spikes.

View the live Google Sheets Terminal Dashboard: https://docs.google.com/spreadsheets/d/1-ag4tLfzgUNxmcCOUPvf3SUuVDI5Co8qQEAbV1UApD0/edit?usp=sharing 

## Dashboard Preview:

<img width="1056" height="579" alt="image" src="https://github.com/user-attachments/assets/a2c079ba-e390-47af-b5d9-cafcb5b59dae" />

