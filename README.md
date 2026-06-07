# FNO Super-Resolution — Équation de la Chaleur 2D

Projet final — Scientific Machine Learning, Mines Paris PSL / SPEIT 2026

## Description

Ce projet applique un **Fourier Neural Operator (FNO)** au problème de super-résolution d'images, en l'interprétant comme un opérateur inverse de diffusion thermique 2D. On apprend à reconstruire une image haute résolution à partir de sa version basse résolution (facteur ×4), et on compare les performances du FNO à un CNN baseline classique.

Dataset utilisé : **Oxford Flowers-102** (8 189 photos naturelles, paires HR/LR générées par downsampling bicubic ×4).

## Dépendances

```bash
pip install torch numpy scipy matplotlib datasets pillow
```

Testé avec Python 3.10 et PyTorch 2.x.

## Comment exécuter

Ouvrir et exécuter toutes les cellules du notebook dans l'ordre :

```bash
jupyter notebook FNO_SuperResolution.ipynb
```

Aucune intervention manuelle n'est nécessaire. Les figures sont sauvegardées automatiquement dans `results/`.

## Structure du projet

```
project/
├── FNO_SuperResolution.ipynb   # notebook principal
├── README.md
└── results/                    # généré à l'exécution
    ├── dataset_samples.png
    ├── training_curves.png
    ├── qualitative_comparison.png
    ├── metrics.csv
    ├── zero_shot_sr.png
    └── ablation_modes.png
```

## Contenu du notebook

| Section | Contenu |
|---------|---------|
| 1 · Configuration | hyperparamètres centralisés |
| 2 · Dataset | chargement Oxford Flowers-102 via torchvision |
| 3 · Architecture | FNO-2D + CNN baseline |
| 4 · Entraînement | boucle train/test, métriques relL2 / PSNR |
| 5 · Résultats | courbes de convergence + comparaison visuelle |
| 6 · Zero-Shot SR | FNO ×4 évalué à ×8 sans ré-entraînement |
| 7 · Ablation | impact du nombre de modes Fourier kmax ∈ {4, 8, 12, 16} |

## Reproduire les résultats

Les hyperparamètres principaux sont dans la cellule 1 du notebook. Les valeurs par défaut reproduisent les résultats du rapport (`MODES=12`, `WIDTH=32`, `EPOCHS=50`, `SCALE=4`).

La graine aléatoire est fixée (`seed=42`) pour garantir la reproductibilité.

## Référence

Z. Li et al. — *Fourier Neural Operator for Parametric Partial Differential Equations*, ICLR 2021.
