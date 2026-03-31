# Monte-Carlo-Option-Pricing
This project implements a Monte Carlo simulation framework to model the evolution and risk profile of a diversified equity portfolio. It retrieves historical market data, estimates statistical properties, simulates future price paths, and computes key risk metrics such as Value at Risk (VaR) and Conditional Value at Risk (CVaR).

The result is a practical demonstration of how Monte Carlo methods support portfolio forecasting, risk estimation, and scenario modelling—core concepts in quantitative finance and modern risk management.

📌 Features
Downloads historical stock data via Yahoo Finance
Calculates daily returns, mean returns, and covariance matrix
Generates random portfolio weights
Runs Monte Carlo simulations using:
Multivariate normal shocks
Cholesky decomposition for correlation structure
Plots simulated portfolio value paths
Computes:
Value at Risk (VaR)
Conditional Value at Risk (CVaR)

🧠 Methodology
1. Data Extraction

The model retrieves closing prices for a basket of Australian stocks:

CBA, BHP, TLS, NAB, WBC, STO

It computes:

Mean daily returns (μ)
Covariance matrix (Σ)
2. Portfolio Construction

Random portfolio weights are generated, then normalised to sum to 1.

3. Monte Carlo Simulation

Each simulation follows these steps:

Generate random shocks
Apply Cholesky decomposition to impose realistic asset correlations
Construct daily return paths
Compute cumulative portfolio values over a 100-day horizon
4. Risk Metrics

From the distribution of final portfolio values:

VaR = α-percentile loss (default α = 5%)
CVaR = average loss beyond the VaR threshold
📈 Visualisation

The script plots all Monte Carlo portfolio paths, providing insight into the dispersion of possible outcomes and downside risk.

🧮 Key Formulas

Correlated shocks:

L = Cholesky(Σ)
ε = L · Z

Daily returns:

R(t) = μ + ε

Portfolio path:

V(t) = V₀ × Π (1 + wᵀR(t))

VaR:

VaR = InitialValue − percentile(V, α)

CVaR:

CVaR = InitialValue − mean(V[V ≤ VaR])
🛠️ Tech Stack
Python
pandas
NumPy
matplotlib
yfinance
🚀 How to Run

Install dependencies:

pip install pandas numpy matplotlib yfinance

Run the script:

python monte_carlo_portfolio.py
📂 Project Structure
.
├── monte_carlo_portfolio.py
├── README.md
└── requirements.txt
📊 Example Output
Portfolio simulation plot
Printed VaR & CVaR values, e.g.:
VaR $123.45
CVaR $178.90
🔮 Future Improvements
Option to specify custom weights
Use geometric Brownian motion for price dynamics
Add data export functionality
Build a Streamlit dashboard
Allow user-defined tickers and simulation parameters
