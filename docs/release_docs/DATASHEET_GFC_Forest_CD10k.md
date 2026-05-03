# Datasheet for GFC-Forest-CD10k Candidate v1.0

## Motivation

The dataset is intended to support reproducible forest change detection experiments using fixed image pairs, ignore-aware pixel labels, and train/validation/test splits. It targets a gap between generic building/land-cover change benchmarks and forest-specific change detection benchmarks.

## Composition

The candidate dataset contains 10,000 image triplets. Each triplet has a pre-change RGB patch, a post-change RGB patch, and a label mask. Labels are binary for valid pixels with an ignore value for non-supervised pixels.

Class composition is intentionally controlled: 7,000 positive samples and 3,000 negative samples. Samples are drawn from 24 source regions spanning tropical, boreal, temperate, montane, and subtropical forest contexts.

## Collection and generation process

The source GeoTIFFs were exported from Google Earth Engine. The label generation uses Global Forest Change forest/loss signals and valid data masks. Annual RGB composites were generated from Landsat observations for the start and end years. Candidate patches were filtered by valid supervision area and change density.

## Preprocessing and filtering

- Patch size: 256 x 256.
- Stride: 64.
- Valid-pixel threshold: `valid_ratio >= 0.05`.
- Positive threshold: `change_ratio >= 0.05`.
- Negative threshold: `change_ratio <= 0.03`.
- Ignore label: `255`.

## Recommended uses

- Binary forest change detection.
- Benchmarking of CNN, Siamese, transformer, and hybrid change detection models.
- Robustness analysis under sparse valid-label supervision.
- Region-wise generalization analysis.

## Out-of-scope uses

- Direct forest carbon accounting.
- Legal or operational deforestation enforcement without independent validation.
- Fine-grained forest disturbance type classification.
- Pixel-perfect manually annotated land-cover mapping.

## Quality assurance

Local reliability checks confirmed 10,000 matched triplets, zero bad shape files, zero invalid label values, zero split leakage, and zero exact duplicate image triplets. A 500-sample human audit table and contact sheets have been generated but are not yet manually filled.

## Ethical and environmental considerations

The dataset covers forest change processes that may be associated with land use, logging, agriculture, fire, or other disturbances. The dataset should be used for scientific analysis and model benchmarking, not for attributing legal responsibility without independent evidence.

## Maintenance

Before public release, freeze this version as `GFC-Forest-CD10k v1.0`, publish checksums, and avoid changing train/val/test splits. Future versions should use semantic versioning and provide changelogs.


## License and access

The dataset is intended for non-commercial research use and should be released under CC BY-NC 4.0. Code and scripts should be released under MIT. Commercial use requires separate permission and compliance with upstream data providers' terms.
