# Pipeline Runs

This folder contains summary statistics from running the MolDef translation
pipeline on ClinVar GKS variation data releases.

Each subfolder corresponds to a specific ClinVar GKS release, named by the
release date (e.g. `2025_12_08/`).

## What's included

Each run folder contains a `stats.json` file with the following information:

- **Source file** — the ClinVar GKS variation file used as input
- **Run date and duration** — when the pipeline was run and how long it took
- **Total lines read** — number of records processed from the source file
- **VRS allele counts** — breakdown by allele type (LSE, RLE, other)
- **Translation results** — how many records were successfully translated
- **Failures** — how many records failed validation or translation

## How to reproduce

1. Download the source file from the
   [clinvar-gks repository](https://github.com/clingen-data-model/clinvar-gks)
2. Install and run the pipeline from
   [fhir-moldef](https://github.com/InformaticsGenomicMedicine/fhir-moldef)
3. The pipeline can be found under `src/fhir_moldef/pipelines`


## Citation
If project is used or referenced please use the following citation: 
> Bajjali S , Freimuth RR. InformaticsGenomicMedicine/moldef-examples: v0.1.0-alpha. Zenodo. https://doi.org/10.5281/zenodo.20209476

<!-- ## Releases

| Release Date | Source File | Total Translated | Total Failed |
|---|---|---|---|
| 2025-12-08 | clinvar_gks_variation_2025_12_08_v2_4_3.jsonl.gz | 4,128,083 | 597 |