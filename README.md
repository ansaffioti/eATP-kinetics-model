This repository contains the computational models, data fitting pipelines, and simulation scripts used to analyze extracellular ATP ($eATP$) kinetics and release fluxes ($J_{efflux}$) in trophoblast cells (**BeWo**) challenged with *Plasmodium falciparum*-infected red blood cells (**iRBCs**).

## Overview

The dynamics of $[eATP]$ are governed by the balance between cell release mechanisms ($J_{efflux}$) and extracellular hydrolysis mediated by EctoATPases:

$$\frac{d[eATP]}{dt} = J_{efflux}(t) - [eATP] \cdot (k_{BeWo-h} + k_{RBC-h})$$

We evaluated three candidate models for $J_{efflux}(t)$ and compared them using the Akaike Information Criterion (AIC):
* **Model 1 (Constant flux):** $J_{efflux}(t) = k_{s\_b}$
* **Model 2 (Linear progressive flux):** $J_{efflux}(t) = k_{s\_m} \cdot t$
* **Model 3 (Combined basal + linear flux):** $J_{efflux}(t) = k_{s\_b} + k_{s\_m} \cdot t$
* **Model 4 (Exponential increase in flux with saturation):** $J_{efflux}(t) = k_{s\_A} + (1-exp(-k_{s\_exp} \cdot t))$

---

## Repository Structure

```text
eATP-kinetics-model/
│
├── data/                         # Raw and preprocessed experimental data
│   ├── Activities/               # EctoATPase activity slopes (BeWo, RBCs)
│   └── Off_line/                 # Time-series [eATP] experimental measurements
│
├── notebooks/
│   └── eATP_model_fitting.ipynb  # Main Jupyter notebook containing fitting & simulations
│
├── Processed/                    # Generated output files
│   ├── Off_line/                 # Fitted parameters (CSV) and Akaike tables
│   └── Simulations/              # Exported simulation trajectories (CSV)
│
├── requirements.txt              # Python package dependencies
├── LICENSE                       # MIT License
└── README.md                     # Repository documentation
