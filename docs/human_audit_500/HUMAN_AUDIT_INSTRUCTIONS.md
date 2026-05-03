# Human Audit Instructions for GFC-Forest-CD10k

The 500-sample audit table is prepared in:

```text
human_audit_500/gfc10k_human_audit_500_samples.csv
```

Contact sheets are provided for quick visual review of the first 100 samples. Full audit should use the file paths in the CSV.

## Label meaning

- `0`: unchanged valid forest pixel.
- `1`: forest change/loss pixel.
- `255`: ignore / not evaluated.

## Recommended annotation fields

Use the following quality labels:

```text
correct
acceptable_minor_noise
uncertain
wrong_label
bad_image_pair
bad_registration
```

Use the following error types where relevant:

```text
missing_change
false_change
low_valid_area
cloud_or_shadow
seasonal_or_phenology_difference
registration_shift
ambiguous_visual_evidence
other
```

## Minimum reporting for manuscript

Report:

- Number of audited samples.
- Acceptable-label rate.
- Wrong-label rate.
- Uncertain rate.
- Error-type distribution.
- Inter-annotator agreement if two annotators are used.

Do not claim manual verification until these fields are filled and summarized.
