# CVA6 Crypto Benchmark — Results

This folder contains measured benchmark outputs and generated graphs produced with our [benchmark toolchain.](../Benchmark%20codes/README.md) It is intended to store raw measurements, aggregated summaries and visualizations that help compare the performance of the CVA6 core with and without the CVXIF crypto coprocessor and different optimization variants.

## Directory Structure

- `graphs/` — Folder containing exported graphs

- `scripts/` — Contains all the Python scripts
    - `data.py` — Raw data from the pre-optimization measurement
    - `main.py` — Script to generate most of the graphs from `data.py`
    - `variance.py` — Script to generate the cycle variance related plots

- `benchmark.xlsx` — Excel file containing both pre- and post-optimization data