# Cryptocurrency Portfolio Risk Estimation using MCMC

### Project Overview
This project focuses on estimating the volatility of a cryptocurrency portfolio using **Metropolis-Hastings Markov Chain Monte Carlo (MCMC)**. Instead of relying on simple point estimates of risk, this Bayesian framework provides an uncertainty-aware distribution of volatility, which is critical for making informed investment decisions in highly volatile markets.

### Objectives
* **Data Acquisition:** Download 30 days of real historical price data for 5 major cryptocurrencies (BTC, ETH, ADA, SOL, LINK) using the `yfinance` API.
* **Volatility Estimation:** Model daily log-returns as Gaussian distributions and use MCMC to sample the posterior distribution of volatility ($\sigma$).
* **Portfolio Risk Analysis:** Calculate the risk of an equal-weight portfolio and propagate MCMC uncertainty to determine the 95% credible intervals for portfolio volatility.
* **Validation:** Verify MCMC performance using trace plots and acceptance rate monitoring.

### Technical Stack
* **Language:** Python 3.10+
* **Data Handling:** `NumPy`, `Pandas`
* **Financial Data:** `yfinance`
* **Statistical Tools:** `SciPy`
* **Visualization:** `Matplotlib`

### Methodology
1.  **Log-Returns:** Daily log-returns are calculated as $r_t = \ln(P_t / P_{t-1})$ to ensure additivity and approximate normality.
2.  **Bayesian Modeling:** A Half-Normal prior is placed on the volatility parameter $\sigma$.
3.  **MCMC Sampling:** The Metropolis-Hastings algorithm is used to generate posterior samples.
4.  **Portfolio Aggregation:** Individual asset volatilities are combined into an equal-weight portfolio, maintaining the full distribution of uncertainty for the total risk estimate.

### Key Results
* **Uncertainty Quantification:** The model provides a full distribution of possible volatility values rather than a single number.
* **MCMC Metrics:** Acceptance rates were maintained in the optimal **20–40% range**, confirming well-tuned proposal distributions.
* **Visualization:** The project includes trace plots for convergence checks and density plots for risk estimation.

### How to Run
1.  Ensure you have the required libraries installed:
    ```bash
    pip install numpy pandas matplotlib yfinance scipy
    ```
2.  Open the Jupyter notebook `Moksh_Jain_Assignment_7.ipynb`.
3.  Run all cells to fetch the latest market data and generate the risk estimates.

### Conclusion
The project demonstrates that MCMC is a powerful tool for financial risk management. By quantifying *how confident* an investor should be in a risk estimate, it provides a superior alternative to traditional frequentist methods.
