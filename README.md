# FNO Super-Resolution — 2D Darcy Flow

Final Project — Scientific Machine Learning, Mines Paris PSL / SPEIT 2026

## Objective

Learn the super-resolution operator for the 2D Darcy equation:

$$-\nabla \cdot (a(x,y)\,\nabla u) = f \quad \text{on } [0,1]^2$$

The model takes `[a(x,y), u_LR]` as input (permeability field + low-resolution solution) and predicts the high-resolution solution `u_HR`.

Three models compared: **CNN (SRCNN)**, **FNO-8**, **FNO-16**.

## Usage

```bash
jupyter notebook FNO_Darcy_super_resolution4_64.ipynb
```

Run all cells in order. The dataset is generated automatically or reloaded from `data4_64/` if it already exists.  
After training, reload models using the **"Run this cell after kernel restart"** cell.

## Configuration

| Parameter | Value |
|-----------|-------|
| HR_SIZE | 64 |
| LR_SIZE | 4 — scale ×16 |
| N_TRAIN | 800 |
| N_TEST | 200 |
| EPOCHS | 200 |
| BATCH_SIZE | 16 |
| Optimizer | Adam + StepLR (÷2 every 50 epochs) |

## Results — test set (in-distribution)

| Model | Params | Relative L2 | PSNR (dB) |
|-------|--------|-------------|-----------|
| FNO-16 | 2 105 889 | **0.0188** | **45.6** |
| FNO-8 | 533 025 | 0.0229 | 43.9 |
| CNN | 131 649 | 0.0375 | 39.6 |

## Results — Zero-shot (out-of-distribution generalization)

Models trained on 4→64 (×16), tested on unseen resolutions:

| Config | CNN RL2 | FNO-8 RL2 | FNO-16 RL2 |
|--------|---------|-----------|------------|
| ZS-1 : 4→128 (×32) | 0.207 | 0.038 | **0.031** |
| ZS-2 : 8→64 (×8) | 0.144 | 0.124 | 0.127 |
| ZS-3 : 8→128 (×16) | 0.178 | 0.133 | **0.133** |

ZS-1 highlights the key FNO advantage: ×7 better generalization than CNN on an unseen resolution.

## Project Structure

```
project/
├── FNO_Darcy_super_resolution4_64.ipynb   # main notebook
├── FNO_Darcy_super_resolution4_68.ipynb   # variant 8->64
├── README.md
├── data4_64/                              # saved models and dataset
│   ├── coeff_train.npy / sol_train.npy
│   ├── coeff_test.npy  / sol_test.npy
│   ├── cnn.pt / fno8.pt / fno16.pt
│   └── cnn_losses.npy / fno8_losses.npy / fno16_losses.npy
└── results4_64/                           # figures and metrics
    ├── loss_comparison.png
    ├── metrics_comparison.png
    ├── metrics.csv
    ├── qualitative_clean.png
    ├── error_maps.png
    ├── zero_shot_comparison.png
    ├── zero_shot_metrics.csv
    └── zero_shot_qualitative.png
```

## Reference

Z. Li et al. — *Fourier Neural Operator for Parametric Partial Differential Equations*, ICLR 2021.
