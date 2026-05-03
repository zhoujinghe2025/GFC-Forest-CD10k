# Manuscript Methods Draft: GFC-Forest-CD10k

## Dataset construction

We constructed GFC-Forest-CD10k, a multi-regional benchmark for binary forest change detection between 2018 and 2020. Source scenes were exported from Google Earth Engine using Landsat annual RGB composites and Global Forest Change forest-loss information. Each exported GeoTIFF contains seven bands: pre-change RGB, post-change RGB, and a label band.

The label mask uses three values: unchanged valid forest pixels are encoded as 0, forest-loss/change pixels during the target interval are encoded as 1, and pixels outside the valid supervision mask are encoded as 255 and ignored during training and evaluation. Candidate patches were extracted using a 256 x 256 window and a stride of 64 pixels.

To reduce label sparsity and stabilize model evaluation, we retained only patches with `valid_ratio >= 0.05`. Positive samples were defined as patches with `change_ratio >= 0.05` among valid pixels, whereas negative samples were defined as patches with `change_ratio <= 0.03`. The final candidate v1.0 dataset contains 10,000 image triplets with a controlled positive/negative composition of 7,000/3,000.

## Dataset splitting and integrity checks

We use a fixed train/validation/test split with 8,001, 1,009, and 990 image triplets, respectively. File-level and hash-level reliability checks confirmed 10,000 matched triplets, zero invalid label values, zero split leakage, and zero exact duplicate image triplets. All reported model metrics should ignore pixels labeled 255.

## Human verification plan

Because labels are generated automatically from GFC-derived rules rather than manual dense annotation, we prepared a stratified 500-sample human audit subset. The audit subset is stratified by class, split, source region, and valid-ratio bins. Two independent annotators should inspect pre-change images, post-change images, and label overlays. The final manuscript should report agreement rates, acceptable-label rates, and common failure categories.

## Benchmark protocol

Baseline models should be trained on the fixed training split, selected on validation F1 or IoU-change, and evaluated once on the test split. We recommend reporting Precision, Recall, F1-score, IoU-change, mIoU, and Overall Accuracy, together with region-wise and valid-ratio-bin analyses.
