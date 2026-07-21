Earnings Press-Release Sentiment & Stock Returns

Independent research project testing whether the linguistic tone of S&P 500 earnings press releases predicts abnormal stock returns around the announcement, beyond the earnings surprise itself.

Summary

Data: 6,013 earnings press releases (Item 2.02 8-K exhibits) from S&P 500 firms, 2022-2024, collected from SEC EDGAR. Final regression sample: 5,679 events after surprise matching.
Sentiment: Scored with FinBERT (ProsusAI/finbert). Sample mean = 0.192, range -0.606 to +0.922.
Returns: Market-model-adjusted abnormal returns in the [-1,+1], [0,+1], and [0,+5] windows.
Control: Earnings surprise (%) from Yahoo Finance, matched within 5 days.
Method: OLS with two-way clustered standard errors (firm x quarter). Holm-Bonferroni correction applied across all six hypotheses.

Main Results

All six regressions significant at p < 0.0001. Primary specification [0,+1] with surprise control: beta = 0.0195, t = 5.61. Correlation between sentiment and earnings surprise = 0.029, confirming tone carries information distinct from the headline beat-or-miss. Placebo test on random non-earnings dates produces near-zero coefficients (p > 0.49), confirming the effect is specific to announcement windows.

Pipeline (13 steps)

1. Pull S&P 500 tickers and 8-K filings from SEC EDGAR
2. Filter to Item 2.02 earnings filings with after-hours event date correction
3. Extract press release text from Exhibit 99.1
4. Score sentiment with FinBERT
5. Compute market-model-adjusted abnormal returns
6. Match earnings surprise from Yahoo Finance
7. Run OLS regressions with two-way clustered SEs
8. Apply Holm-Bonferroni correction
9. Run placebo test
10. Cross-check with Loughran-McDonald dictionary
11. Heterogeneity analysis by firm size tercile
12. Interaction model (sentiment x firm size)
13. Event-time CAR figure

Data Sources

All free and public: SEC EDGAR, Yahoo Finance (yfinance), Wikipedia (S&P 500 constituents).

Reproducibility

Run the notebook top to bottom. All data is fetched from public sources at runtime. Fixed random seed = 42.
