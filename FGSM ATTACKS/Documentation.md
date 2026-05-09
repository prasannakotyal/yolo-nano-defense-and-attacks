# FGSM Attack Notebook

`fgsm_attack.ipynb` implements untargeted FGSM for `yolo26n-obb.pt` on DOTAv1.

## Method

For each image, the notebook computes the native Ultralytics OBB loss against the DOTAv1 labels and takes one gradient-ascent step on the input image:

`x_adv = clamp(x + epsilon * sign(grad_x loss), 0, 1)`

The attack uses RGB tensors for the model forward pass and writes PNG files for standard Ultralytics validation.

## Outputs

The notebook writes:

- `/kaggle/working/yolo26_obb_fgsm/metrics.csv`
- `/kaggle/working/yolo26_obb_fgsm/plots/map.png`
- `/kaggle/working/yolo26_obb_fgsm/plots/precision_recall.png`
- `/kaggle/working/yolo26_obb_fgsm/plots/f1.png`

The mAP column named `map50_95` is mAP averaged from IoU 0.50 to 0.95, not mAP95.
