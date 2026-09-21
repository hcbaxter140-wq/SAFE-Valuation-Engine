# S.A.F.E. (Sector-Adaptive Fundamental Engine)

An institutional-grade quantitative screening and valuation engine that integrates stochastic Monte Carlo DCF simulations, macroeconomic regime detection, and the Quarter-Kelly criterion for portfolio sizing.

> **Developer Note & Research Workflow:**
> I am an undergraduate student majoring in Business Finance with minors in Economics and Mathematics. My core focus is financial architecture, quantitative theory, and empirical investment research.
>
> To build this engine, I designed the quantitative architecture, economic nowcasting logic, mathematical thresholds, and risk bounds. To execute the Python syntax, API routing, and vectorized data manipulation, I utilized AI as a pair-programmer. I own the underlying economic models, valuation logic, and thesis defenses; modern tooling was leveraged to build the programmatic infrastructure.

---

## Institutional Documentation & Master Dictionary
The Python code is paired with an exhaustive mathematical guide detailing all underlying equations, step-function grading matrices, and investment thesis defenses:

**[View the Complete S.A.F.E. Master Wiki & Architecture Guide](https://app.notion.com/p/Quant-Documentation-3e0bd67b7411808089b9e6cd4feb4667?source=copy_link)**

---

## Core Engine Features

* **Triangular Monte Carlo DCF:** Rejects static single-point estimates by running 1,000 stochastic simulations per asset, utilizing asymmetric downside tail-risk to account for real-world supply-chain and macro shocks.
* **Macroeconomic Nowcasting:** Pulls live data from the Federal Reserve (FRED API) to track Core PCE momentum, Capacity Utilization, and High-Yield Credit Spreads ($Z$-Score Panic Triggers) to dynamically scale sector exposure.
* **Adaptive Step-Function Grading:** Converts raw financial metrics into 1–10 institutional grades with dynamic adjustments for sector structural realities (e.g., adjusting margin thresholds for Consumer Cyclicals vs. Technology).
* **Dual-Hurdle Allocation Filter:** Enforces economic value creation by checking $\text{ROIC} > \text{WACC}$ and a baseline hurdle rate, featuring automated waiver cascades (Hyper-growth, Historical Consistency) and value-trap penalties.
* **Quarter-Kelly Capital Allocation:** Algorithmically scales position sizes based on statistical edge and Sortino-adjusted downside protection, programmatically bound by an 8% single-asset cap and a 25% sector ceiling.
* **Empirical Factor Validation:** Executes 1-Sample $T$-Tests on portfolio Alpha against equal-weight benchmarks (RSP) to statistically reject the null hypothesis of random market noise.

---

## Empirical Fund Teardowns

The engine includes real-world stress tests run against constituent holdings across major thematic ETFs:

* `ARKK_Teardown.csv`: **Hyper-Growth & Valuation Bubbles.** Evaluates speculative tech assets, validating the engine's Burn-Rate mode and growth-cap safety rails by enforcing 0% capital lockouts on negative-FCF constituents.
* `XOP_XME_Teardown.csv`: **Cyclical Cash Flows & Value Traps.** Demonstrates how the engine differentiates between true economic value creators (e.g., EOG, COP) and low-multiple cyclical traps masking peak-cycle earnings.
* `SMH_Teardown.csv`: **CapEx Cycles & Momentum.** Tests 3-Year Free Cash Flow smoothing across capital-intensive hardware supply chains while tracking 200-day SMA trend extensions.
* `VFAIX_VGSIX.csv`: **Structural Debt Bypass.** Validates the engine’s capital structure exemptions, ensuring financial institutions and real estate entities are not penalized for operational leverage in DCF modeling.

---

## Environment & Setup

### Prerequisites
* Python 3.9+
* API Keys: [FRED API (St. Louis Fed)](https://fred.stlouisfed.org/docs/api/api_key.html) and [Finnhub API](https://finnhub.io/)

### Installation
```bash
pip install yfinance pandas numpy scipy matplotlib seaborn fredapi requests
