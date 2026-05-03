# Server Run Plan for GFC-Forest-CD10k Baselines

## Transfer to server

Transfer the following directory to the GPU server:

```bash
GFC_Forest_256_10k/
gfc_publication_package_10k/baseline_protocol/
```

Recommended server-side structure:

```text
/workspace/gfc_forest_cd10k/
  data/GFC_Forest_256_10k/
  code/change_detection_baselines/
  runs/
```

## Required evaluation behavior

Every dataloader and metric function must ignore label value `255`. Report both pixel-level metrics and sample/region-stratified metrics.

## Suggested command pattern

The exact commands depend on the selected baseline repository. Use one config per model and keep all logs.

```bash
python train.py \
  --dataset-root /workspace/gfc_forest_cd10k/data/GFC_Forest_256_10k \
  --train-list splits/train.txt \
  --val-list splits/val.txt \
  --test-list splits/test.txt \
  --ignore-index 255 \
  --model MODEL_NAME \
  --epochs 100 \
  --batch-size BATCH_SIZE \
  --lr 1e-4 \
  --seed 0 \
  --output runs/MODEL_NAME_seed0
```

## Required outputs per model

```text
runs/MODEL_NAME_seed0/config.yaml
runs/MODEL_NAME_seed0/train_log.csv
runs/MODEL_NAME_seed0/val_curve.csv
runs/MODEL_NAME_seed0/test_metrics.csv
runs/MODEL_NAME_seed0/regionwise_metrics.csv
runs/MODEL_NAME_seed0/valid_ratio_bin_metrics.csv
runs/MODEL_NAME_seed0/best_checkpoint.txt
```

## Minimum acceptable experiment table

At least six models should be reported. If compute is limited, run one seed for all models and three seeds for the strongest two models. If compute is sufficient, run three seeds for all models.
