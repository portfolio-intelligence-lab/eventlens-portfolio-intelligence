# EventLens

EventLens is a reproducible prototype of a source-agnostic, event-driven portfolio intelligence pipeline.

## Scope

The pipeline connects verified financial events to portfolio holdings, converts market data into GBP, estimates abnormal returns using a market model, and generates transparent monitoring alerts.

## Main components

- Demonstration portfolio of 15 international stocks
- Yahoo Finance market prices
- GBP currency conversion
- ACWI ETF benchmark proxy
- Official-company event snapshot
- SQLite data storage
- Market-model event study
- Abnormal returns, CAR and z-scores
- Rule-based thesis matching
- Manager alert and monitoring summary

## Reproducibility

The notebook uses a frozen event snapshot stored in `data/events_snapshot.csv`.

The current prototype is offline and reproducible. The event snapshot contains events collected from official company sources, together with source URLs and verification status.

In a production version, the event-ingestion layer could be connected to authorised live sources such as company investor-relations feeds, regulatory filings or licensed financial-data providers.

## Repository structure

- `EventLens_full_pipeline.ipynb` — complete reproducible pipeline
- `data/` — input data and generated CSV outputs
- `figures/` — generated charts
- `requirements.txt` — required Python packages

## How to run

Install the required packages:

```bash
pip install -r requirements.txt
```

Then open `EventLens_full_pipeline.ipynb` in Jupyter Notebook and run all cells from top to bottom.

## Methodological notes

The ACWI ETF is used as a transparent proxy for a global equity benchmark.

The event study estimates a market model over a historical estimation window and calculates event-day abnormal returns, cumulative abnormal returns and residual-based z-scores.

The portfolio is illustrative and equally weighted. The results are intended to demonstrate the pipeline rather than provide investment advice.

## Limitations

- Yahoo Finance is used as a convenient market-data source for the prototype.
- ACWI is an ETF proxy rather than the MSCI ACWI index itself.
- The event snapshot is fixed and offline rather than continuously updated.
- Thesis matching is rule-based and is not an autonomous AI agent.
- The current implementation does not provide investment advice.

## Future production architecture

In a production deployment, a source connector or AI-assisted ingestion agent could retrieve, normalise, deduplicate and verify new events from authorised external sources.

The analytical and alerting layers would remain source-agnostic, allowing the market-data and event-data providers to be replaced without changing the core portfolio-analysis logic.
