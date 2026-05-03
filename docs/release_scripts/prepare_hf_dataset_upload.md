# Hugging Face Dataset Upload Preparation

This is a preparation note, not an executed upload.

Recommended repository name:

```text
zhoujinghe2025/GFC-Forest-CD10k
```

Recommended contents:

```text
GFC_Forest_256_10k/
README.md
DATASHEET_GFC_Forest_CD10k.md
CITATION.cff
DATASET_VERSION.json
GFC_Forest_256_10k_sha256_manifest.txt
```

Potential upload command after `huggingface-cli` or `hf` authentication:

```bash
hf repo create zhoujinghe2025/GFC-Forest-CD10k --type dataset
hf upload zhoujinghe2025/GFC-Forest-CD10k GFC_Forest_256_10k GFC_Forest_256_10k --repo-type dataset
hf upload zhoujinghe2025/GFC-Forest-CD10k gfc_publication_package_10k/release_docs . --repo-type dataset
hf upload zhoujinghe2025/GFC-Forest-CD10k gfc_publication_package_10k/GFC_Forest_256_10k_sha256_manifest.txt GFC_Forest_256_10k_sha256_manifest.txt --repo-type dataset
```

Before public release, decide license and complete the human audit statement.
