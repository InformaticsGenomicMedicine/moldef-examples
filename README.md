# moldef-examples

## Overview

This repository contains example inputs, generated outputs, and pipeline statistics for translating ClinVar GKS variation data into FHIR Allele resources.

The examples are intended to show how ClinVar GKS records are processed by the MolDef translation pipeline and what the resulting FHIR output looks like.

This repository is a companion repository for [`fhir-moldef`](https://github.com/InformaticsGenomicMedicine/fhir-moldef). The translation code is maintained in `fhir-moldef`, while this repository stores example inputs, generated outputs, and run metadata.

## Data source

The input data comes from the ClinVar Genomic Knowledge Standards (GKS) project. ClinVar GKS is a ClinGen-supported effort that transforms ClinVar releases into GA4GH-compliant representations.

The source data is maintained in the [clinvar-gks github repository](https://github.com/clingen-data-model/clinvar-gks).

This repository does not maintain the original ClinVar GKS data. It only stores selected example inputs, generated outputs, and metadata about the pipeline runs.

## Pipeline

The pipeline reads ClinVar GKS variation files and looks for VRS Allele objects in each record's `members` array.

Valid VRS Alleles are translated into FHIR Allele resources using the `VrsToFhirAlleleTranslator`.

Records or alleles that cannot be translated are tracked separately so the results can be inspected later.

The pipeline implementation is part of [`fhir-moldef`](https://github.com/InformaticsGenomicMedicine/fhir-moldef) and can be found under [`src/fhir_moldef/pipelines`](https://github.com/InformaticsGenomicMedicine/fhir-moldef/tree/main/src/fhir_moldef/pipelines).


<!-- This repository contains example FHIR MolecularDefinition Allele resources generated from ClinVar-GKS data.

The source data comes from the [`clingen-data-model/clinvar-gks`](https://github.com/clingen-data-model/clinvar-gks) project, which transforms ClinVar release data into GA4GH Genomic Knowledge Standards formats, including VRS outputs. The translated examples in this repository focus on VRS Allele records from ClinVar and convert them back into FHIR Allele profile instances using the [`fhir-moldef`](https://github.com/InformaticsGenomicMedicine/fhir-moldef) translation pipeline.

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


