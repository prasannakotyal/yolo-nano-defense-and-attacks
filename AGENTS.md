# Project Agent Instructions

These instructions apply to this repository.

## Experiment Contract

- Use DOTAv1 for all YOLO26n-OBB attack and defense experiments.
- Use exactly the 15 DOTAv1 classes. Do not add the DOTA 1.5 `container crane` class.
- Use the official `yolo26n-obb.pt` model only with a 15-class OBB head unless a new checkpoint is explicitly documented as DOTAv1-compatible.
- Do not compare 15-class and 16-class checkpoints.
- Generate fresh metrics and plots from CSV outputs. Do not reuse old plots from mismatched class heads or proxy-loss experiments.
- For gradient attacks, use the native Ultralytics OBB loss or clearly document any alternative objective.
