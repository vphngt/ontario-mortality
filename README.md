# **Ontario Mortality Projection & Insurance/Annuity Pricing**

**An end-to-end actuarial analysis that builds Ontario mortality tables, projects improvement with Lee-Carter, and quantifies how much "frozen" mortality misprices life annuities and term insurance.**

---

## Data Source
* **[Canadian Human Mortality Database (CHMD), Ontario](http://www.bdlc.umontreal.ca/chmd/prov/ont/ont.htm)**: 1x1 deaths and exposure-to-risk by single age and year, 1921-2022 (2023 preliminary data excluded).


## Technologies Used
* **Python** (pandas, NumPy, SciPy, statsmodels, Matplotlib)
* **Jupyter Notebook**


## Key Features
* **Experience Study**: Computed central death rates, q(x), and life expectancy by sex, graduated old-age rates with a Gompertz fit extended to age 110.
* **Lee-Carter Model**: Fitted by SVD with the second-stage adjustment (fitted deaths = actual deaths), and forecast k(t) as a random walk with drift (ARIMA(0,1,0)), checked against statsmodels.
* **Out-of-Sample Backtest**: Trained through 2005, tested on 2006-2019 against a frozen-2005 benchmark, comparing 1921 vs 1950 training starts.
* **Pricing**: Generational vs frozen basis for a whole-life annuity-due at 65 and a 20-year term at 45.
* **Longevity Risk**: Simulated 1,000 k(t) paths to give a range on annuity values.
* **COVID-19 Excess Mortality**: Actual 2020-2022 deaths vs model-expected deaths.


## Results
* At ages 65-95, Lee-Carter cut backtest error by **about 50% for women and 30% for men** vs frozen mortality.
* Frozen mortality **under-reserves a 65-year-old annuity by about 3-5%** and **over-prices 20-year term cover by 21-30%**.
* Frozen annuity values sit **below the entire 5%-95% simulated range** for both sexes.
* Deaths ran **about 6-7% above expectation in 2020-21 and about 12% in 2022**.
* Training from 1950 rather than 1921 improved fit, both models under-predicted 2006-2019 improvement.
