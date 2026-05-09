# PGD Attack Notebook

`pgd_attack.ipynb` implements random-start untargeted PGD for `yolo26n-obb.pt` on DOTAv1.

## Method

For each image, the notebook maximizes the native Ultralytics OBB loss under an L-infinity constraint. The default configuration uses 10 PGD steps with `alpha = epsilon * 0.25`.

The notebook keeps the perturbation inside the epsilon ball after each step and validates the generated adversarial image directory with Ultralytics OBB validation.

## Outputs

The notebook writes metrics and plots under `/kaggle/working/yolo26_obb_pgd/`.
