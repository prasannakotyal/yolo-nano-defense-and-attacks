# Robust Aerial Detection: Adversarial Attacks on YOLO26n-OBB

This repository contains Kaggle notebooks for evaluating white-box adversarial attacks against the official Ultralytics `yolo26n-obb.pt` model on DOTAv1.

## Fixed Experimental Contract

- Model: `yolo26n-obb.pt`
- Task: Ultralytics OBB detection
- Dataset: DOTAv1, 15 classes
- Kaggle dataset: https://www.kaggle.com/datasets/chandlertimm/dota-data
- Expected Kaggle mount: `/kaggle/input/dota-data`
- Image size: `1024`
- Metrics: precision, recall, mAP50, mAP50-95, and F1

The notebooks fail loudly if the loaded model head is not 15-class DOTAv1. DOTA 1.5 and `container crane` are intentionally not used because the official YOLO26n-OBB checkpoint is trained on DOTAv1.

## Notebooks

- `FGSM ATTACKS/fgsm_attack.ipynb`: one-step untargeted FGSM using native Ultralytics OBB loss.
- `PGD ATTACKS/pgd_attack.ipynb`: random-start iterative PGD using native Ultralytics OBB loss.
- `QUANTIZED ATTACKS/quantized_attacks.ipynb`: iterative PGD with uint8 quantization after every projected step.
- `DPATCH ATTACKS/dpatch_attack.ipynb`: universal patch training by maximizing native OBB loss.
- `PGD DEFENSE/pgd-defense.ipynb`: 15-class PGD adversarial fine-tuning.
- `PGD DEFENSE/plot_generation_code.ipynb`: baseline-vs-defended PGD evaluation plots.

Each notebook writes fresh metrics and plots under `/kaggle/working/...`. Old plots and old 16-class weights were removed to avoid mixing incompatible results.
