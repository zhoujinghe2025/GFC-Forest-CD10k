# GFC-Forest-CD10k Candidate v1.0

GFC-Forest-CD10k is a candidate benchmark dataset for binary forest change detection from 2018 to 2020. Each sample contains a pre-change RGB image (`A`), a post-change RGB image (`B`), and a pixel-level label mask (`label`). Label values are `0` for unchanged valid forest pixels, `1` for forest-loss/change pixels, and `255` for ignored pixels outside the valid supervision mask.

## Dataset snapshot

| Item | Value |
|---|---:|
| Image triplets | 10,000 |
| Patch size | 256 x 256 |
| Positive samples | 7,000 |
| Negative samples | 3,000 |
| Train / val / test | 8,001 / 1,009 / 990 |
| Source regions | 24 |
| Mean valid_ratio | 0.111555 |
| Median valid_ratio | 0.080170 |
| Mean change ratio among valid pixels | 0.264751 |

## Directory structure

```text
GFC_Forest_256_10k/
  A/                 # pre-change RGB patches
  B/                 # post-change RGB patches
  label/             # label masks, values 0/1/255
  splits/
    train.txt
    val.txt
    test.txt
  metadata.csv
```

## Construction rules

- Source products: Google Earth Engine exports derived from Global Forest Change and Landsat annual composites.
- Time interval: 2018 to 2020.
- Patch size: 256 x 256 pixels.
- Candidate stride: 64 pixels.
- Valid supervision threshold: `valid_ratio >= 0.05`.
- Positive sample rule: `change_ratio >= 0.05` among valid pixels.
- Negative sample rule: `change_ratio <= 0.03` among valid pixels.
- Target class composition: 70% positive and 30% negative samples.
- Ignore label: `255`.

## Reliability checks

The local reliability report found:

- Matched triplets: 10,000.
- Bad shape count: 0.
- Bad label value count: 0.
- Split leakage: 0.
- Exact triplet duplicate groups: 0.
- Exact A+B image duplicate groups: 0.

See `dataset_reliability_outputs/gfc_forest_256_10k/dataset_reliability_report.md` for the full report.

## Recommended evaluation metrics

Report at least the following metrics on the fixed test split:

- Precision, Recall, F1-score.
- IoU for the change class.
- Mean IoU.
- Overall Accuracy.
- Region-wise F1/IoU.
- Valid-ratio-bin F1/IoU.

All metrics should ignore pixels with label value `255`.

## Current limitation

This candidate release is generated from automatic GFC-derived labels. Manual audit files have been prepared, but human verification results must be completed before claiming final dataset label quality.


## License

The dataset is released for non-commercial research use under CC BY-NC 4.0. Construction and evaluation code should be released under the MIT License. Users should cite this dataset and the original GFC/Landsat data products.
