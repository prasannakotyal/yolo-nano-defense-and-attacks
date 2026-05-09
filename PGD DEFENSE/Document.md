# PGD Defense Notebooks

The defense workflow is split into training and evaluation.

## Training

`pgd-defense.ipynb` builds a 15-class DOTAv1 defense dataset containing clean images and native-loss PGD adversarial images at epsilon `0.04`, then fine-tunes `yolo26n-obb.pt`.

The notebook detects whether Kaggle has one or two GPUs and chooses `device=0` or `device=[0, 1]` accordingly.

## Evaluation

`plot_generation_code.ipynb` expects a 15-class defended `best.pt` uploaded as a Kaggle dataset. Update `DEFENDED_MODEL_PATH` in the notebook, then run it to compare baseline and defended models under native-loss PGD.

Old 16-class defense weights are not compatible with this DOTAv1 setup and were removed.
