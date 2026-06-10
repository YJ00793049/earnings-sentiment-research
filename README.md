# Earnings Press-Release Sentiment & Stock Returns

Independent research project testing whether the linguistic tone of S&P 500
earnings press releases predicts abnormal stock returns around the announcement,
beyond the earnings surprise itself.

## Summary
- **Data:** 250 earnings press releases (Item 2.02 8-K exhibits) from S&P 500
  firms, 2022–2024, collected from SEC EDGAR.
- **Sentiment:** Scored with FinBERT (ProsusAI/finbert).
- **Returns:** Market-adjusted abnormal returns (vs. SPY) in the [-1,+1],
  [0,+1], and [0,+5] windows, from Yahoo Finance.
- **Control:** Earnings surprise (%) from Yahoo Finance earnings dates.
- **Method:** OLS with Newey-West (HAC) standard errors.

## Main result
More positive press-release tone predicts higher abnormal returns in the two
days around the announcement, and the relationship survives controlling for the
earnings beat-or-miss. The effect concentrates in the first two trading days and
fades within a week.

## Pipeline
1. Pull S&P 500 tickers and 8-K filings from SEC EDGAR
2. Filter to Item 2.02 (earnings) filings
3. Extract press-release text from Exhibit 99.x
4. Score sentiment with FinBERT
5. Compute event-study abnormal returns
6. Hypothesis test (sentiment → returns)
7. Add earnings-surprise control
8. Build the master results table

## Data sources
All free and public: SEC EDGAR, Yahoo Finance (`yfinance`), Wikipedia (S&P 500
constituents).

## Reproducibility
Run the notebook top to bottom. All data is fetched from public sources at runtime.
