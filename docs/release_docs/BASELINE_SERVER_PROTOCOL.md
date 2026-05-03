# Baseline Server Protocol for GFC-Forest-CD10k

Baseline experiments should be run on a GPU server. Do not report baseline results from the local dataset construction machine unless the full training logs and GPU configuration are available.

## Dataset

Use the fixed dataset root:

```text
GFC_Forest_256_10k/
```

Use fixed splits:

```text
splits/train.txt
splits/val.txt
splits/test.txt
```

Ignore label value: `255`.

## Candidate baselines

Minimum recommended baseline set:

1. FC-EF.
2. FC-Siam-Diff.
3. FC-Siam-Conc.
4. SNUNet.
5. BIT.
6. ChangeFormer.
7. A recent transformer/foundation-style change detection baseline, if available.
8. The local/proposed model, if this dataset paper is paired with a method.

## Training protocol

Use identical input resolution, augmentations, optimizer family, and model-selection rule wherever possible.

Recommended default:

```text
input size: 256 x 256
batch size: hardware dependent, report explicitly
optimizer: AdamW or Adam, report explicitly
learning rate: 1e-4 to 3e-4, tune only on validation split
epochs: 100 or fixed convergence budget
early stopping: optional, validation F1/IoU based
checkpoint: best validation F1 or best validation IoU-change
loss: cross entropy or BCE/Dice variant with ignore-mask support
```

## Metrics

Report all metrics on the test split, ignoring label `255`:

```text
Precision
Recall
F1-score
IoU-change
mIoU
Overall Accuracy
```

Also report stratified metrics:

```text
by source region
by continent/macro-region
by valid_ratio bin
by change_ratio bin
positive-only and negative-only sample subsets
```

## Required artifacts

For each model save:

```text
config.yaml
training_log.csv
best_checkpoint metadata
validation curve CSV
test_predictions summary
metric table CSV
region-wise metric table CSV
valid-ratio-bin metric table CSV
```

## Reproducibility

Run at least 3 seeds for the final comparison table if compute allows. If only one seed is possible, explicitly state this limitation and publish the seed/config.
