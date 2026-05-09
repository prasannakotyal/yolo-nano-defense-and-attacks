# Quantized PGD Attack Notebook

`quantized_attacks.ipynb` implements a save-to-disk aware PGD attack for `yolo26n-obb.pt` on DOTAv1.

## Method

The attack maximizes native OBB loss like PGD, but after every projected step the adversarial image is rounded to valid 8-bit image levels:

`round(clamp(x_adv, 0, 1) * 255) / 255`

This makes the attack evaluate the perturbation that actually survives PNG serialization.

## Outputs

The notebook writes metrics and plots under `/kaggle/working/yolo26_obb_quantized_pgd/`.
