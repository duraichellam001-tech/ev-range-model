# ev-range-model
Energy consumption &amp; range estimation model for EVs

# INITIAL MODEL DEVELOPMENT AND COMPARIOSN
Model Comparison Summary — UDDS Drive Cycle

Three models were evaluated for predicting energy consumption over the UDDS cycle:

A physics-based model using vehicle parameters and first-principle equations (reference baseline),

A tabular ML surrogate (XGBoost) trained on drive-cycle summary statistics (avg/max speed, accel, idle ratio),

A sequence ML surrogate (LSTM) trained on transient dynamics from HWY + US06 cycles.

The XGBoost model predicted Wh/km within ± 3 % of the physics baseline, demonstrating that steady-state energy estimation can be achieved from a limited set of cycle descriptors.
The LSTM model, trained on unseen cycles, reproduced transient power profiles and achieved < 2 % deviation in integrated Wh/km.
This validates that data-driven surrogates can complement or replace 1D physics simulations in early-stage range and fuel-economy estimation workflows, reducing simulation turnaround time by > 90 % once trained.

XGB model dataset --> Different features extracted from different augmented drive cycles.
XGB used for steady state prediction --> Predicts Wh/km ( single scalar ) from Given features about the drive cycle

LSTM dataset --> Time series time vs velocity fed to the model
LSTM used for transient prediction of P_batt which is then post processed to Wh/km

*** Augmented version of UDDS is added to trainig set of both LSTM and XGB due to less availability of datasets ***
