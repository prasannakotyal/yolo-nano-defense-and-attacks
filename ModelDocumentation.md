# Target Model: YOLO26n-OBB

The target model is the official Ultralytics `yolo26n-obb.pt` checkpoint.

## Class Contract

`yolo26n-obb.pt` is a DOTAv1 OBB model with a 15-class detection head. The experiments therefore use only DOTAv1 classes:

0. plane
1. ship
2. storage tank
3. baseball diamond
4. tennis court
5. basketball court
6. ground track field
7. harbor
8. bridge
9. large vehicle
10. small vehicle
11. helicopter
12. roundabout
13. soccer ball field
14. swimming pool

DOTA 1.5's extra `container crane` class is not used.

## Loading Check

The notebooks assert that `model.model.model[-1].nc == 15` before running attacks or evaluation. This prevents accidentally comparing checkpoints with different heads.
