# CVA6 Crypto Benchmark — Results

This folder contains measured benchmark outputs and generated graphs produced with our [benchmark toolchain.](../Benchmark%20codes/README.md) It is intended to store raw measurements, aggregated summaries and visualizations that help compare the performance of the CVA6 core with and without the CVXIF crypto coprocessor and different optimization variants.

## Directory Structure

- `graphs/` — Folder containing exported graphs

- `scripts/` — Contains all the Python scripts
    - `data.py` — Raw data from the pre-optimization measurement
    - `main.py` — Script to generate most of the graphs from `data.py`
    - `variance.py` — Script to generate the cycle variance related plots

- `benchmark.xlsx` — Excel file containing both pre- and post-optimization data


## Graphs Generation 

The python scripts allows the generation of numerous different graphs from the 
pre-optimisation benchmark measurements, saved in `graphs/` .

The `main.py` script generates most of them. It is fully configurable, 
allowing you to choose which ones to display :

```
##############################################################################################
#                                       DISPLAY CHOICES                                     #
##############################################################################################

plot_bubbles = False

plot_cycles_per_blocks = True
log_cycles_per_blocks = False

plot_instructions_per_blocks = True
log_instructions_per_blocks = False

plot_cycles_per_bit_per_blocks = True
plot_instructions_per_bit_per_blocks = True

plot_delta = True
plot_cycles_per_iteration = True

plot_cycles_per_ad = True
plot_instructions_per_ad = True
```
The `variance.py` generates 3 plots linked to cycles variance of the measurements from 
the pre-optimisation.  

## Data & Results

The `data.py` hold formatted for plotting data from my pre-optimisation benchmark.
The resulting graphs are stored in the `graphs/`.

Here 2 figures examples:  
<br>
<br>
<div align="center">
  <img src="./graphs/cycles_per_blocks.png" alt="Alt Text" width="900">
</div>