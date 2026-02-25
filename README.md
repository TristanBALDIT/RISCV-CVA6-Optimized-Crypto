[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18772550.svg)](https://doi.org/10.5281/zenodo.18772550)

# RISCV-CVA6-Optimized-Crypto

**RISCV-CVA6-Optimized-Crypto** is a project designed to optimize the performance of some symmetric-key cryptographic 
algorithms (AES,ChaCha20 and ASCON) on the [**RISC-V OPENHW GROUP CV32A6 SOFTCORE**](https://github.com/openhwgroup/cva6) architecture by developing a 
small coprocessor implemented with the **CVXIF interface**. The performance are measured via a [custom benchmark](Benchmark%20codes/README.md) 
running the baremetal ciphers algorithms on the **ZYBO Z7-20** board.

This benchmark allows the simultaneous performance comparison of different symmetric ciphers, based on the number of 
instructions and cycles they require.

The **ZYBO Z7-20** toolchain used to implement and test the modified CVA6 softcore is based on the 
[**THALES CVA6 SOFTCORE CONTEST**](https://github.com/ThalesGroup/cva6-softcore-contest/blob/cv32a6_contest_24_25) one and my own version of the CVA6 softcore, implementing my custom coprocessor : 
[cva6_crypto](https://github.com/TristanBALDIT/cva6_crypto) and the top module for the board.

## Project Structure

- `Benchmarks codes/` — Folder containing the C codes used as benchmark
  - `aes/` — AES benchmark codes
  - `chacha/` — ChaCha20 benchmark codes
  - `ascon/` — Ascon benchmark codes
  - `opcodes test/` — baremetal C test for the opcodes of the CVXIF coprocessor
  -  `main.c` — Main benchmark program
  - `loader.c` — Helper functions to load random test data into the algorithms
  

- `Benchmarks results & graphs/` — Contains all the data and graphs from my benchmark runs
  - `graphs/` — Folder containing exported graphs

  - `scripts/` — Contains all the Python scripts
    - `data.py` — Raw data from the pre-optimization measurement
    - `main.py` — Script to generate most of the graphs from `data.py`
    - `variance.py` — Script to generate the cycle variance related plots

  - `benchmark.xlsx` — Excel file containing both pre- and post-optimization data

- `cva6_crypto/` — Modified version of the cva6 softcore containing the CVXIF coprocessor

## CVA6 Softcore and modifications

This project is fully based on the **CVA6 softcore** : a RISCV, 6-stage, single-issue, in-order CPU project developed
by the [OpenHardware Group](https://openhwfoundation.org). This family of six-stage RISC-V cores supports a wide range of ISA extensions, 
including those required to boot Linux, making it far more capable than many lightweight cores. 
Moreover, CVA6 implements key RISC-V hardware standards, notably the **Core-V eXtension Interface** ([CV-X-IF](https://github.com/openhwgroup/core-v-xif))
allowing the asy development of tighly coupled coprocessors.

The `cva6_crypto/` contains a personal fork of the CVA6 main repo were is implemented as small coprocessor 
on the CVXIF interface, used to execute custom arithmetics operations optimising the execution of ChaCha20 and Ascon 
symmetric ciphers.

## Benchmark codes

All the benchmark codes are accessible in the [associated directory](Benchmark%20codes)
which also includes a complete tutorial on [how to get started with the **ZYBO Z7-20** toolchain](/Benchmark%20codes/README.md).

## Benchmark codes

The `Benchmarks results & graphs/` contains data from both pre- and post-optimisation benchmarks (`benchmark.xlsx`) as well 
as python scripts generating graphs from the pre-optimisation data only in `Benchmarks results & graphs/scripts/`. Finally, the graphs generated are 
stored in the `Benchmarks results & graphs/results/ folder`.
