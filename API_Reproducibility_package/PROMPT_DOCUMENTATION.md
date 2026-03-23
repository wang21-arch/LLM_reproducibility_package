
# Prompt Documentation

This document describes the structure of the prompt files used in the evaluation dataset.

All prompts are stored as Microsoft Word (.docx) files inside the directory:

01_question_sets/

The dataset is organized into four groups, each representing a different evaluation scenario.

---

## Group 1 – Molecule Characterization

Directory:
Group1_molecules/

Each file corresponds to a single molecule.

Example file:
alanine.docx

Typical prompt structure includes questions about:

- Chemical formula
- Molecular weight
- Chemical structure
- Physical properties
- Spectroscopic characteristics

Each file contains a series of questions related to the same molecule.

The LLM is expected to provide structured scientific descriptions based on the molecule name.

---

## Group 2 – Drug Information

Directory:
Group2_drugs/

Each file corresponds to a single pharmaceutical compound.

Example file:
ibuprofen.docx

Prompts typically request:

- Chemical identity
- Pharmacological properties
- Molecular characteristics
- Stereochemistry
- Spectroscopic information

These prompts evaluate the model's ability to retrieve and reason about drug-related information.

---

## Group 3 – Comparative Drug Analysis

Directory:
Group3_comparisons/

Each prompt file describes a pair of related compounds.

Examples:
ketamine vs esketamine  
ibuprofen vs dexibuprofen  
formoterol vs arformoterol

Typical questions include:

- Differences in chirality
- Differences in pharmacological activity
- Structural comparisons
- Toxicological differences
- Clinical implications

The goal is to evaluate comparative reasoning capabilities.

---

## Group 4 – Inference Tasks

Directory:
Group4_inference/

These prompts are structured as inference tasks.

Each file provides partial chemical information about a drug, such as:

- Molecular formula
- Molecular weight
- Physical properties
- Chirality
- Spectroscopic characteristics

The model must infer the identity of the drug.

Example questions:

1. Is this drug chiral?
2. Is the drug racemic or enantiomerically pure?
3. What is the degree of chirality?
4. Plot the circular dichroism spectrum.
5. Identify the drug.

Important rule:

The correct drug name is **not included in the prompt sent to the model**.

The script automatically removes identifiers derived from filenames before sending the prompt to the LLM APIs.

This prevents leakage of the correct answer.

---

## Prompt Integrity

The original prompt files are preserved exactly as used in the study.

The reproducibility workflow reads these files directly and sends their contents to the APIs without modification, except for the anonymization rule applied to Group4.

---

