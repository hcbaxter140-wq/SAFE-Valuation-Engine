# S.A.F.E. (Sector-Adaptive Fundamental Engine)

A quantitative equity screening and valuation model. It integrates Monte Carlo DCF simulations, macroeconomic regime detection, LLM-based sentiment analysis, and the Quarter-Kelly criterion for position sizing.

> **Developer Note & Research Workflow:**
> I am an undergraduate student majoring in Business Finance with minors in Economics and Mathematics. My core focus is financial architecture, quantitative theory, and empirical investment research.
>
> To build this engine, I designed the quantitative architecture, economic nowcasting logic, mathematical thresholds, and risk bounds. To execute the Python syntax, API routing, and vectorized data manipulation, I utilized AI as a pair-programmer. I own the underlying economic models, valuation logic, and thesis defenses; modern tooling was leveraged to build the programmatic infrastructure.

---

## Documentation & Dictionary

The Python code is paired with a mathematical guide detailing the underlying equations, step-function grading matrices, and investment thesis defenses:

**[View My Personal S.A.F.E. Architecture Guide](https://app.notion.com/p/Quant-Documentation-3e0bd67b7411808089b9e6cd4feb4667?source=copy_link)**

---

## Core Features

* **Triangular Monte Carlo DCF:** Runs 1,000 stochastic simulations per asset to replace single-point estimates. Simulation bounds adjust dynamically based on Blume's Beta. Includes a Poisson Jump-Diffusion variable to account for asymmetric tail risks and macro shocks.
* **Accounting Waterfall Extraction:** Handles SEC reporting inconsistencies and missing API data. The code cascades through prioritized arrays of accounting string aliases to prevent `KeyError`s and `ZeroDivisionError`s during financial data extraction.
* **5-Pillar S.A.F.E. Rubric:** Scores equities from 1-10 across 15 fundamental metrics. Uses sector-specific baseline spreads to normalize comparisons (e.g., standardizing margin thresholds between high-volume retail and high-margin software).
* **LLM Sentiment Scoring:** Feeds a 7-day Finnhub news digest into the Gemini API for semantic analysis. Outputs a continuous score from -1.0 to 1.0 based on financial context rather than simple positive/negative word counts.
* **Macroeconomic Nowcasting:** Pulls live Federal Reserve data (FRED API) tracking Core PCE, Capacity Utilization, and High-Yield Credit Spreads. A credit spread Z-Score above 2.0 triggers a "Crash Mode" override, lowering terminal growth ceilings and raising WACC floors.
* **Dual-Hurdle Allocation Filter:** Requires ROIC > WACC for portfolio inclusion. Includes programmed waivers for hyper-growth and 3-year historical consistency to prevent disqualification from single-quarter accounting anomalies.
* **Blended Quarter-Kelly Allocation:** Sizes positions using a 60/20/20 weighted factor split (Fundamental Score / MC Win Rate / Sortino Ratio). Includes value-trap penalties, an 8% single-asset maximum, and a 25% sector cap.
* **Empirical Factor Validation:** Runs a rolling-window vectorized backtest (Bootstrap Alpha) and a 1-Sample T-Test on portfolio Alpha to reject the null hypothesis of random outperformance against the equal-weight S&P 500 (RSP).
