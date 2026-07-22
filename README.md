# Quant Project Template

A modular Python template for quantitative finance, systematic investment research, and strategy backtesting.

This repository provides a standardized structure for developing, testing, evaluating, and reporting quantitative investment strategies. The core idea is to separate the **strategy logic** from the **simulation engine** and the **performance reporting layer**.

Each strategy is implemented as a Python class responsible for deciding portfolio positions at a given point in time using only information available up to that date. The simulator then evaluates those positions over the next period, records realised returns, weights, turnover, transaction costs, and other diagnostics, and rolls forward across the full sample.

After each simulation, the framework generates a QuantStats-style tear sheet to evaluate performance, risk, drawdowns, benchmark comparison, and rolling diagnostics.

---

## Objective

The objective of this project is to provide a clean and extensible research framework for systematic investment strategies.

The template is designed to support:

- quantitative research workflows;
- systematic strategy simulation;
- rolling backtests;
- strategy comparison under a common protocol;
- portfolio-weight tracking;
- performance and risk diagnostics;
- reproducible research reports;
- QuantStats-style tear sheet generation.

The Markowitz minimum-variance portfolio included in the project should be interpreted only as a simple reference example of how to implement a strategy class and connect it to the simulator. It is not the main contribution of the repository.

The main contribution is the **simulation and reporting architecture**.

---

## Research Workflow

The framework follows the standard research cycle below:

1. Load and validate market data.
2. Implement a strategy as a Python class.
3. At each decision date, the strategy chooses a position using only past and current information.
4. The simulator applies this position to the next period.
5. Realised returns, portfolio weights, turnover, costs, and diagnostics are stored.
6. The process rolls forward until the end of the sample.
7. A QuantStats-style tear sheet is generated for post-simulation analysis.

Conceptually:

```text
Data → Strategy Class → Simulator → Returns/Weights/Diagnostics → Tear Sheet
