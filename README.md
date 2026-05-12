# moldef-examples

This repository contains example FHIR MolecularDefinition Allele resources generated from ClinVar-GKS data.

The source data comes from the [`clingen-data-model/clinvar-gks`](https://github.com/clingen-data-model/clinvar-gks) project, which transforms ClinVar release data into GA4GH Genomic Knowledge Standards formats, including VRS outputs. The translated examples in this repository focus on VRS Allele records from ClinVar and convert them back into FHIR Allele profile instances using the [`fhir-moldef`](https://github.com/InformaticsGenomicMedicine/fhir-moldef) translation pipeline.

<!--
## Purpose

The goal of this repository is to provide sample translated data showing how GA4GH VRS Allele representations from ClinVar-GKS can be represented as FHIR MolecularDefinition Allele resources.

These examples are intended to support:

- testing of VRS-to-FHIR translation workflows
- review of FHIR MolecularDefinition Allele profile outputs
- interoperability work between GA4GH VRS and HL7 FHIR genomic standards
- development of downstream tooling that consumes FHIR MolecularDefinition resources

## Data Source

The input data is derived from ClinVar-GKS outputs.

ClinVar-GKS converts ClinVar release data into standardized GA4GH Genomic Knowledge Standards formats, including VRS, Cat-VRS, and VA-Spec datasets. The ClinVar-GKS repository describes its output datasets as JSONL files and includes variation records representing ClinVar variations in GA4GH formats.

## Translation Pipeline

The translation was performed using the FHIR-MolDef pipeline.

FHIR-MolDef provides support for creating FHIR `MolecularDefinition` resources and currently supports Sequence, Allele, and Variant profiles. It also supports bidirectional translation between GA4GH VRS Alleles and the FHIR Allele Profile.

In this repository, the translation flow is:

```text
ClinVar-GKS VRS Allele
        ↓
FHIR-MolDef translation pipeline
        ↓
FHIR MolecularDefinition Allele Profile

File Format

The main dataset is provided as JSON Lines (.jsonl), where each line contains one complete FHIR MolecularDefinition Allele resource.

JSONL is useful for this repository because:

each translated allele can be read independently
large datasets can be streamed line by line
the format works well with command-line tools and data pipelines
it avoids loading the full dataset into memory
it is consistent with the JSONL-style outputs used by ClinVar-GKS

{"resourceType":"MolecularDefinition","id":"example-allele-1","type":"allele"}
{"resourceType":"MolecularDefinition","id":"example-allele-2","type":"allele"}

For readability, selected examples may also be included as pretty-printed .json files in the examples/ directory.


