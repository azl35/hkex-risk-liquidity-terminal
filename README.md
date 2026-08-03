# HKEX Risk & Liquidity Terminal (Proof-of-Concept)

A capital markets desk tool PoC combining a **Python ETL data engine** with a **Google Sheets front-office risk dashboard**. Built to demonstrate real-time visualization of rolling volatility, intraday liquidity shocks, and Value-at-Risk (VaR) metrics for HKEX equities (`2800.HK`).

---

## Project Overview
* **Target Focus:** Front-office desk tools, risk management, and capital markets analytics.
* **Asset Class Analyzed:** Tracker Fund of Hong Kong (`2800.HK` / HKEX).
* **Key Metrics:** 
  * 30-Day Annualized Realized Volatility (%)
  * Parametric 1-Day Value-at-Risk ($95\%$ & $99\%$ CI on a $100K portfolio)
  * Amihud Liquidity Shock / Price Impact Index

---

## System Architecture

1. **Python Engine (`hkex_risk_liquidity_engine.py`):**
   * Fetches daily OHLCV market data via `yfinance`.
   * Calculates log returns, rolling annualized volatility, and parametric VaR.
   * Computes the Amihud Liquidity Impact Ratio:
     $$\text{Amihud Index} = \frac{|\text{Return}|}{\text{Dollar Volume}}$$
   * Exports structured datasets for spreadsheet ingestion.

2. **Front-Office Dashboard (`Lab49_HKEX_Risk_Terminal_AlvinaLin.xlsx`):**
   * Terminal-style UI featuring KPI metric cards.
   * Combo & Area visual charts highlighting volatility stress windows and liquidity dry-ups.

Dashboard Preview:
<img width="1051" height="578" alt="image" src="https://github.com/user-attachments/assets/09acea44-3d18-4aa4-8aa6-9b2a2b012cc9" />

