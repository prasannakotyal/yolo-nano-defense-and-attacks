# Adversarial Robustness of YOLO26n-OBB on DOTAv1

This repository contains Kaggle notebooks for studying adversarial attacks and adversarial fine-tuning on the Ultralytics `yolo26n-obb.pt` oriented object detector. The experiments focus on aerial object detection with oriented bounding boxes on DOTAv1.

## Overview

The project evaluates whether first-order and patch-based adversarial attacks can degrade the detection performance of a lightweight OBB model. The notebooks generate adversarial images, run standard Ultralytics OBB validation, and save metrics and plots for analysis.

The main attack settings are:

- FGSM: one-step untargeted gradient attack.
- PGD: random-start iterative projected gradient attack.
- Quantized PGD: iterative PGD with 8-bit image quantization after every projected step.
- DPatch: universal adversarial patch optimization.
- PGD defense: adversarial fine-tuning with clean and PGD-attacked DOTAv1 images.

## Model and Dataset

- Model: `yolo26n-obb.pt`
- Framework: Ultralytics YOLO OBB
- Dataset: DOTAv1
- Classes: 15 DOTAv1 categories
- Input size: `1024`
- Metrics: precision, recall, mAP50, mAP50-95, and F1

The Kaggle notebooks use this dataset:

https://www.kaggle.com/datasets/chandlertimm/dota-data

Expected Kaggle mount path:

```text
/kaggle/input/dota-data
```

The experiment code asserts that the loaded model has a 15-class OBB head before running evaluation or attacks.

## Repository Structure

```text
.
├── FGSM ATTACKS/
│   ├── fgsm_attack.ipynb
│   └── Documentation.md
├── PGD ATTACKS/
│   ├── pgd_attack.ipynb
│   └── Documentation.md
├── QUANTIZED ATTACKS/
│   ├── quantized_attacks.ipynb
│   └── Documentation.md
├── DPATCH ATTACKS/
│   ├── dpatch_attack.ipynb
│   └── Documentation.md
├── PGD DEFENSE/
│   ├── pgd-defense.ipynb
│   ├── plot_generation_code.ipynb
│   └── Document.md
└── ModelDocumentation.md
```

## Running on Kaggle

1. Create a Kaggle notebook.
2. Attach the DOTAv1 dataset from `chandlertimm/dota-data`.
3. Enable GPU acceleration.
4. Upload or copy the relevant notebook from this repository.
5. Run the notebook top to bottom.

Each notebook installs its Python dependencies at the top:

```text
ultralytics==8.4.48
opencv-python-headless
pyyaml
matplotlib
pandas
tqdm
```

## Outputs

Each notebook writes experiment outputs under `/kaggle/working/`.

Typical outputs include:

- `metrics.csv`: raw clean and attacked validation metrics.
- `plots/map.png`: mAP50 and mAP50-95 curves.
- `plots/precision_recall.png`: precision and recall curves.
- `plots/f1.png`: F1 curve.
- generated adversarial image directories for each epsilon.

The DPatch notebook additionally saves the learned patch image and a patch-training metric curve.

## Reproducibility Notes

The notebooks use a deterministic random seed and the DOTAv1 class list. Attack generation uses the native Ultralytics OBB loss so that gradients are aligned with the detector's actual training objective.

For paper-ready experiments, run each notebook on the same dataset split and report the raw `metrics.csv` values together with the generated plots.
