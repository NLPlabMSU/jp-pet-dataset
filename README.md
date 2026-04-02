# JP-PET Dataset

This repository contains the JP-PET dataset for Japanese euphemism classification, introduced in:

*Challenges in Japanese Euphemism Classification: An Analysis of Pretrained Japanese and Multilingual Models*

---

## Overview

JP-PET is a dataset of Japanese Potentially Euphemistic Terms (PETs), where each instance is annotated as:

- `1` = euphemistic usage  
- `0` = literal usage  

The dataset captures context-dependent meaning and includes metadata such as domain and register.

---

## Dataset Structure

The dataset consists of two main files:

### 1. `data/jp_pet_sentences.csv`

Sentence-level annotations.

Each row represents one instance of a PET in context.

**Columns:**
- `row_id`: unique identifier for each sentence
- `PET_id`: identifier linking to the PET inventory
- `PET`: target expression
- `expanded_text`: sentence with `[PET_BOUNDARY]` markers around the PET
- `span_text`: the PET span only
- `label`:  
  - `1` = euphemistic  
  - `0` = literal
- `whole_text`: original sentence without boundary markers

---

### 2. `data/jp_pet_list.csv`

PET-level metadata.

Each row corresponds to a unique PET.

**Columns:**
- `PET_id`: unique identifier
- `PET_jp`: Japanese expression
- `Domain`: semantic category (e.g., Death & Dying, Workplace)
- `Register`: formal / neutral / informal
- `Literal equivalent (JP)`: literal meaning in Japanese
- `English gloss (euphemism)`: euphemistic interpretation
- `English gloss (literal)`: literal interpretation
- `Euphe_status`:  
  - `always`: always euphemistic  
  - `sometimes`: context-dependent

---

### Linking

The two files are connected via `PET_id`.

---

## Data Splits

We provide predefined splits used in the paper.

### Split 1 (Lexical Overlap)
- PETs may appear in training, validation, and test sets  
- Evaluates contextual generalization  

### Split 2 (PET-Disjoint)
- PETs in test set do not appear in training  
- Evaluates generalization to unseen euphemisms  

Each split contains **10 folds**, with train/validation/test files.

---

## Task

Binary classification:

**Input:** sentence with `[PET_BOUNDARY]`  
**Output:**  
- `1` = euphemistic  
- `0` = literal  

## Data Source Notice

This dataset was constructed using sentences from the Balanced Corpus of Contemporary Written Japanese (BCCWJ) via the Shonagon interface.

The original copyright of the corpus belongs to the National Institute for Japanese Language and Linguistics (NINJAL), and the copyright of individual text samples belongs to their respective authors.

This dataset is released for research and educational purposes only. Users must comply with the original BCCWJ usage conditions, including restrictions on redistribution and reproduction of the source texts.
