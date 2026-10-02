# Bacterial Growth: Exponential Curve Fitting

This project uses the `pop_linearization.ipynb` notebook to explore bacterial growth over time using blank-corrected OD600 measurements. OD600 measures sample turbidity and is used as an indicator of growth, rather than a direct count of bacteria.

## Notebook Workflow

1. Load the Excel dataset and convert it to CSV.
2. Find the header row and select rows E, F, G, and H.
3. Reshape the data with `melt()` so time and OD600 become separate columns.
4. Select samples labelled “Positive control”.
5. Fit an exponential curve using `scipy.optimize.curve_fit`.
6. Plot the full experiment and fit a second curve using the first 10 hours.

The model used is:

```text
OD(t) = a × exp(b × t) + c
```

- `t`: time in hours.
- `a`: scaling factor.
- `b`: growth rate parameter.
- `c`: vertical offset.


## Quick Start

Install the required packages in your Python environment:

```bash
python -m pip install -r requirements.txt
```

Open `pop_linearization.ipynb` in VS Code or Jupyter, select the Python environment with these packages, and run the cells from top to bottom. Ensure the input Excel file is in the expected location before running.

## Reading the Graphs

- Blue points represent measured OD600 values.
- The red curve represents the fitted model.
- The horizontal axis shows time in hours.
- The vertical axis shows blank-corrected OD600.

The full experiment includes an initial period with little growth, faster growth, and a later slowdown. A single exponential curve does not represent all these stages well. The first-10-hours analysis focuses on earlier growth, although this interval also includes the initial slow period.
