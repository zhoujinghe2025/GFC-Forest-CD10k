# Top-Tier Dataset Paper Release Checklist

## Already completed locally

- [x] Constructed GFC-Forest-CD10k candidate dataset.
- [x] Fixed train/val/test splits.
- [x] Generated metadata.csv.
- [x] Ran local integrity checks.
- [x] Confirmed zero split leakage.
- [x] Confirmed zero exact duplicate triplets.
- [x] Generated source-region coverage table.
- [x] Generated valid_ratio and change_ratio summaries.
- [x] Generated publication-style figures.
- [x] Prepared 500-sample human audit table and contact sheets.
- [x] Prepared baseline server protocol.
- [x] Prepared README and datasheet drafts.

## Still required before submission

- [ ] Complete human audit labels for the 500 sampled cases.
- [ ] Summarize human audit error rates and common failure modes.
- [ ] Run 6-8 baseline models on a GPU server.
- [ ] Report test metrics and region-wise metrics.
- [ ] Add valid_ratio-bin and change_ratio-bin model performance.
- [ ] Create a dataset comparison table against LEVIR-CD, WHU-CD, CDD, SYSU-CD, SECOND, LIM-CD, OpenMapCD and forest-change datasets.
- [ ] Freeze version as v1.0.
- [ ] Publish checksums and download scripts.
- [ ] Upload data to a durable host such as Hugging Face Datasets, Zenodo, or Figshare.
- [ ] Keep GitHub for code, metadata, configs, and documentation.
- [ ] Add license and citation file.
- [ ] Prepare manuscript figures and tables in final journal format.
