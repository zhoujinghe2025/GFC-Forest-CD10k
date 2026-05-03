# GFC-Forest-CD10k Local Publication Package

## Dataset snapshot
- Candidate version: `GFC_Forest_256_10k_candidate_v1`
- Samples: 10000 image triplets
- Positive / negative: 7000 / 3000
- Fixed split: train=8001, val=1009, test=990
- Source regions: 24
- Mean valid_ratio: 0.111555; median valid_ratio: 0.080170
- Mean change ratio among valid pixels: 0.264751

## Reliability summary
- Matched triplets: 10000
- Bad shape count: 0
- Bad label value count: 0
- Split leakage: 0
- Exact duplicate triplets: 0
- Exact duplicate A+B images: 0

## Generated evidence files
- `gfc10k_dataset_summary.csv`
- `gfc10k_source_region_coverage.csv`
- `gfc10k_valid_ratio_bins.csv`
- `gfc10k_change_ratio_bins.csv`
- `gfc10k_split_class_distribution.csv`
- `human_audit_500/gfc10k_human_audit_500_samples.csv`
- `human_audit_500/gfc10k_audit_contact_sheet_*.png`
- `figures/*.svg` and `figures/*.png`

## Recommended manuscript positioning
This dataset should be described as a GFC-derived, multi-regional forest change detection benchmark with fixed ignore-mask-aware supervision. The current local evidence supports dataset integrity and candidate-scale benchmarking, but top-tier publication still requires manual audit results and server-side baseline experiments.

## Remaining before top-tier submission
1. Complete the 500-sample human audit and report quality/error rates.
2. Run 6-8 baseline models on a GPU server with identical training and evaluation protocol.
3. Add region-wise and valid_ratio-bin performance tables.
4. Release checksums, download scripts, README, datasheet, and model evaluation code.
