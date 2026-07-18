# EU Freight Rate Risk Monitor - Pricing Edition

This is the pricing edition of my EU Freight Rate Risk Monitor: the same analysis,
presented for pricing, tender and bid decisions. Canonical study repo:
[freight-rate-risk-monitor](https://github.com/khareparag/freight-rate-risk-monitor)
(analysis synced July 2026). Category-manager edition:
[freight-tender-timing](https://github.com/khareparag/freight-tender-timing).
Streaming extension: [freight-rate-stream](https://github.com/khareparag/freight-rate-stream).

Every quote is a position on the next twelve months of rates. Most desks take that
position on experience and last quarter's numbers. This study measures the ground under
it: air and road freight rates across six EU markets, 2003 to 2024, every finding
test-backed.

## Two modes, two pricing problems
Air runs about 1.6x road's volatility (coefficient of variation 0.155 against 0.095),
and the gap is not a pandemic artifact - it holds at 1.35x with 2020-2022 removed and
1.41x pre-COVID. In a typical year air moves inside a 6.7% band, road 2.8%. Validity
windows, indexation clauses and surcharge logic sized for one do not fit the other.

## Seasonality is tradable
Air climbs about 3.2% into a hard Q2 peak. Across 85 backtested market-years,
trough-season locks (Q4 to Q1) beat peak-season locks in 75% of years, average edge
1.8% - Germany 8 of 9. That edge is yours to spend either way: price sharper at the
trough to take the award, or hold margin at the peak with the index behind you. Out of
sample, the Q2 climb repeated in 10 of 12 market-years in 2024 and 2025.

## Repricing on signal, not on schedule
Since July 2026 the bands run live. A streaming extension of the study scores every rate
movement as it arrives and fires a repricing alert when a lane breaks its band. Replayed
over 2019-2022, the 2020 air shock triggers exactly where the study's charts show it;
replayed over the quiet 2015-2018 window, the alarm stays close to silent.
The story: https://rfq.ch/projects/freight-rate-stream/

## Know where the rule breaks
In Poland road, not air, is the volatile mode. In France the timing rule fails (44% hit
rate on the freight-only series). Per-lane validation comes first; no price hangs on an
unvalidated pattern.

## The working tool
A self-built, five-tab monitor with every test attached.
Live monitor: https://khareparag.github.io/freight-rate-risk-monitor/
Full write-up for pricing teams: https://rfq.ch/projects/pricing-volatility/

## Reproduce it
```
pip install pandas scipy matplotlib
python code/analysis_fr.py        # six-state pipeline, writes results_6.json
python code/analysis_upgrades.py  # backtest, robustness, out-of-sample
```
results/ holds the machine-readable outputs every number above is checked against.

## Author
Parag Khare. Twelve-plus years of pricing and tendering on the seller side, plus
buyer-side tender platform configuration for 68+ enterprise shippers. I price against
the evaluation the buyer actually runs.

- Site: https://rfq.ch/
- LinkedIn: https://www.linkedin.com/in/khareparag/
- Email: pk@rfq.ch
