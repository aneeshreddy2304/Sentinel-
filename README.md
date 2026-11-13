<p align="center"><img src="docs/assets/banner.svg" alt="Sentinel — From traffic features to an explainable security workflow." width="100%"></p>

<p align="center"><img src="docs/assets/badges/python.svg" alt="python" height="28"> <img src="docs/assets/badges/flask.svg" alt="flask" height="28"> <img src="docs/assets/badges/scikit-learn.svg" alt="scikit-learn" height="28"> <img src="docs/assets/badges/sqlite.svg" alt="sqlite" height="28"></p>

<p align="center"><strong>An educational intrusion-classification project combining notebook experiments with a Flask prediction interface.</strong></p>

## Overview

An educational intrusion-classification project combining notebook experiments with a Flask prediction interface.

### Why it matters

Sentinel connects the full shape of an applied ML security project: feature preparation, classifier experiments, saved artifacts, and a web-facing prediction flow.

## Key features

- UNSW-NB15-style feature exploration
- Multiple scikit-learn classifier experiments
- Feature-selection and resampling workflows
- Flask interface for model-backed predictions

## Architecture

```mermaid
flowchart LR
  A[Network feature data] --> B[Notebook experiments]
  B --> C[Saved classifier]
  D[Flask form] --> E[Prediction service]
  C --> E
  E --> F[Classification result]
```

## Technology stack

**python** · **flask** · **scikit learn** · **sqlite**

## Getting started

Provide a permitted dataset and compatible saved model, install the imported Python packages, and use only synthetic accounts in a local environment. Keep credential remediation in the separate security PR.
