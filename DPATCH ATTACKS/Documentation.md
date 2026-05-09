# DPatch Attack Notebook

`dpatch_attack.ipynb` trains a universal adversarial patch for `yolo26n-obb.pt` on DOTAv1.

## Method

The patch is optimized directly against the native Ultralytics OBB loss on patched images. The optimizer minimizes `-loss + TV_WEIGHT * total_variation`, which is equivalent to maximizing detector loss while discouraging high-frequency patch noise.

The patch is placed at random valid positions during training and evaluation. The notebook records mAP50 over training iterations so the patch effect is measurable instead of assumed.

## Outputs

The notebook writes:

- `/kaggle/working/yolo26_obb_dpatch/metrics.csv`
- `/kaggle/working/yolo26_obb_dpatch/dpatch.png`
- `/kaggle/working/yolo26_obb_dpatch/plots/dpatch_map50.png`
