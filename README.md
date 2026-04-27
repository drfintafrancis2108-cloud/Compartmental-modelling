#  Infectious Disease Modelling Framework (SI, SIS, SIR, SEIR)

This repository contains a collection of **compartmental infectious disease models implemented in R**, including:

* SI model (basic transmission)
* SIS model (reinfection dynamics)
* SIR model (permanent immunity)
* SEIR model (incubation period)
* Intervention extensions (treatment, conceptual framework)

The models are implemented using **ordinary differential equations (ODEs)** and solved using the `deSolve` package in R.

---

# Mathematical Framework

All models are based on compartmental epidemiology where individuals transition between states over continuous time.

## SI Model

\frac{dS}{dt} = -\beta \frac{SI}{N}, \quad \frac{dI}{dt} = \beta \frac{SI}{N}

---

## SIS Model

\frac{dS}{dt} = -\beta \frac{SI}{N} + \gamma I, \quad \frac{dI}{dt} = \beta \frac{SI}{N} - \gamma I

---

## SIR Model

\frac{dS}{dt} = -\beta \frac{SI}{N}, \quad \frac{dI}{dt} = \beta \frac{SI}{N} - \gamma I, \quad \frac{dR}{dt} = \gamma I

---

## SEIR Model

\frac{dS}{dt} = -\beta \frac{SI}{N}, \quad \frac{dE}{dt} = \beta \frac{SI}{N} - \sigma E, \quad \frac{dI}{dt} = \sigma E - \gamma I, \quad \frac{dR}{dt} = \gamma I

---

# Intervention Extension (Treatment Concept)

Treatment increases recovery rate:

\gamma \rightarrow \gamma + \tau

Where:

* τ = treatment rate (e.g., antibiotics or fast recovery intervention)

---

# Repository Structure

```
infectious-disease-models/
│
├── SI_model.R
├── SIS_model.R
├── SIR_model.R
├── SEIR_model.R
│
├── interventions/
│   ├── treatment_SIR.R
│   ├── treatment_SEIR.R
│
├── simulations/
│   ├── compare_SIS_SIR_SEIR.R
│
├── figures/
│   ├── infection_curves.png
│
└── README.md
```

---

# Requirements

Install required R package:

```r
install.packages("deSolve")
```

---

# How to Run Models

Example (SIR model):

```r
source("SIR_model.R")
out <- ode(y = state, times = times, func = sir_model, parms = parameters)
out <- as.data.frame(out)
```

---

# Example Outputs

Each model produces time-series outputs for:

* Susceptible (S)
* Infected (I)
* Recovered (R) (if applicable)
* Exposed (E) (for SEIR)

---

# Model Comparison

The repository allows comparison of epidemic dynamics:

| Model | Behavior                         |
| ----- | -------------------------------- |
| SI    | monotonic infection growth/decay |
| SIS   | endemic equilibrium possible     |
| SIR   | epidemic peak then decline       |
| SEIR  | delayed epidemic peak            |

---

# Key Insights

* Model structure strongly affects epidemic outcomes
* SEIR introduces realistic incubation delays
* SIS allows persistent infection
* SIR introduces immunity and epidemic waves

---

# Applications

These models can be extended to:

* Malaria transmission modelling (vector-borne SEIR-SEI)
* Intervention analysis (treatment, vaccination, ITN)
* Public health policy simulation
* Outbreak forecasting
* R₀ estimation studies

---

# Future Work

Planned extensions:

* Mosquito–human malaria transmission model
* Seasonal forcing (rainfall-dependent transmission)
* Intervention optimization (treatment + ITN + spraying)
* Parameter estimation from real epidemiological data

---

#  Author Notes

This repository is intended for:

* epidemiology simulation studies
* academic research and teaching
* computational disease modelling exploration

---

