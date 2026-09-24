# Quantum-Simulation-on-IQM-Resonance

Trotterized quantum simulation of the Fermi-Hubbard model, implemented on the [IQM Resonance](https://resonance.meetiqm.com/) platform and evaluated across ideal, noisy, and real hardware environments.

## Overview

This project implements a Trotterized quantum circuit for the Fermi-Hubbard model and studies how well it performs in practice. Using custom fermionic gate constructions (RXX, RYY, and fSWAP), we built a layered circuit that captures:

- **Onsite potentials**
- **Short-range hopping**
- **Fermionic exchange dynamics**

The circuit is run in three settings to compare performance:

1. **Ideal** – noiseless classical simulation
2. **Noisy** – simulation with depolarizing channels
3. **Real hardware** – execution on an IQM quantum device via IQM Resonance

## Repository Structure

```
.
├── data/         # Raw and processed results
├── figures/      # Plots and figures
├── notebooks/    # Colab notebooks for running and analyzing experiments
├── reports/      # Written report and supporting documents
├── src/          # Circuit construction and simulation code
└── README.md
```

## Getting Started

### Prerequisites

- Python 3.9+
- An [IQM Resonance](https://resonance.meetiqm.com/) account and API token (required for hardware runs only)

## Method

The Fermi-Hubbard time evolution is decomposed into Trotter steps. Each step is built from layers of:

- Onsite terms for the potential
- RXX and RYY gates for nearest-neighbor hopping
- fSWAP gates to handle fermionic exchange and preserve correct particle statistics

Performance is measured by comparing occupation patterns and occupation fidelity across the three environments, including variation across random seeds for the noisy simulations.

## Results

- **Ideal simulation:** The circuit reproduced the expected occupation patterns, confirming the design and gate structure.
- **Depolarizing noise:** Occupation fidelity dropped clearly, with more variation across random seeds, showing sensitivity to gate-level decoherence.
- **IQM hardware:** Deviations were larger than the depolarizing noise model predicted, reflecting real-system noise and hardware-specific limitations.

Reducing Trotter error requires deeper circuits, which accumulates more noise. On current NISQ hardware, performance is constrained by this trade-off between Trotter error and cumulative noise.

Figures and raw data are in `figures/` and `data/`.

## Conclusion

The circuit models the target physics accurately under ideal conditions, but cumulative noise and Trotter error limit it on today's hardware. These findings point to the need for stronger error-mitigation techniques and more noise-resilient algorithms to make near-term quantum simulation reliable and scalable.

## Authors

- Mawa Clarke
- Zachary Justin Metellus