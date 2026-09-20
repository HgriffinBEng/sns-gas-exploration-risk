# Risking a Southern North Sea gas exploration well

A hypothetical single-well gas exploration prospect, valued with a Monte Carlo simulation, a sensitivity analysis and a simple decision tree. Every input is an illustrative round number chosen for this exercise. Nothing here comes from any real well, field or operator.

## Questions it answers

1. What is the well worth if it finds gas, and how wide is the range?
2. Which uncertainties actually move that value?
3. Is drilling worth it once the chance of a dry hole is included?

## Method

- **Inputs:** gas volume in place (lognormal, fitted to a P90 of 10 BCF and a P10 of 40 BCF), recovery factor, gas price, well cost and extra days lost to problems, each with its own distribution.
- **Model:** reserves, margin per BCF, a 20% annual decline over 10 years, discounted at 10% mid-year.
- **Monte Carlo:** 100,000 runs, all five inputs varied at once, fixed random seed.
- **Sensitivity:** each input moved from its 10th to its 90th percentile while the others sit at their medians, shown as a tornado chart.
- **Chance of success:** the product of four geological elements (39.6%), combined with the Monte Carlo into an expected monetary value.

## Findings

- If the well finds gas, the median NPV is about £40m, with a P90 of about £2m and a P10 of about £125m. About 8% of outcomes lose money.
- Gas volume moves NPV by about £106m across its range and gas price by about £53m. Recovery factor, extra days lost and well cost each move it by £3m to £10m.
- A very small discovery (2 BCF or less) appeared once in 100,000 draws, so a dry hole has to be modelled as a separate outcome and cannot be a low draw from the volume range.
- The expected value of drilling is about £4m. It breaks even at a 34.8% chance of success against a case of 39.6%, so the margin is thin.

## Run it

Open `sns-gas-exploration-risk.ipynb` in Jupyter and choose Kernel, then Restart & Run All. It needs Python with numpy, pandas, matplotlib and Jupyter, which Anaconda includes.

## Limitations

- Inputs are sampled independently, although volume and recovery factor would normally be linked.
- Single well, gross basis, no tax, and a simple exponential decline.
- A dry hole is assumed to cost the full well cost.
- Chance of success is treated as a known number.
- The method is the point, not the specific values.
