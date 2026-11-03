# Cross-Country Tuberculosis Gene Expression & HIV Confounding Analysis

This repository contains the analysis code, statistical validation pipelines, and machine learning models accompanying the research manuscript evaluating **cross-country transferability of host-transcriptomic TB signatures, HIV confounding mechanisms, and latent tuberculosis diagnostic interference**.

---

## Project Overview

Host-transcriptomic biosignatures hold immense promise for tuberculosis (TB) triage and diagnosis. However, their real-world clinical translation is frequently hindered by two major vulnerabilities:
1. **Geographic Instability:** Models trained in one clinical setting often fail when deployed across different countries due to technical and biological batch effects.
2. **HIV Confounding:** Chronic immune activation in HIV-positive individuals frequently triggers false-positive "active TB" predictions.

This project investigates these dynamics using public microarray data (**GSE37250**) comparing cohorts from Malawi and South Africa, analyzing 31 published legacy TB signatures, and implementing strict cross-country machine learning transfer models paired with rigorous random-removal controls.

---

## Key Findings

* **Universal Latent TB Confounding:** Evaluation across 31 published host-transcriptomic signatures revealed that **30 out of 31** show significantly higher active-TB scores in HIV-positive patients with purely latent (sleeping) TB ($p_{adj} < 0.05$ for 28 signatures), uncovering a universal mechanism of diagnostic interference.
* **Rigorous Cross-Country Transfer:** Training predictive models in South Africa and testing on Malawi (and vice versa) demonstrated that targeted feature selection outperforms random-removal baseline controls, isolating true biological signals from data-shrinkage artifacts.
* **Transparent Null & Positive Results:** Openly reports both the successful mitigation of cross-national transfer friction and the honest negative result that univariate HIV gene-filtering alone does not fully close the within-cohort HIV performance gap.

---

## Repository Structure

* `TB_HIV_clean_analysis.ipynb` — The primary end-to-end computational notebook containing data preprocessing, signature scoring, multi-signature LTBI evaluations, cross-country `glmnet` models, bootstrap evaluations, and random-removal control scripts.

---

## Data Availability

This study utilizes publicly available transcriptomic data from the Gene Expression Omnibus (**GEO**), specifically accession **GSE37250** (Malawi and South Africa cohorts), alongside external validation sets (GSE19442, GSE19444, GSE69581). 

---

## Software Requirements & Environment

The analysis is written in **R** and utilizes standard bioinformatics and machine learning libraries, including:
* `glmnet` (for regularized logistic regression and cross-validation)
* `pROC` / custom fast AUC functions
* Core R base packages for statistical evaluations and Benjamini-Hochberg (BH) false discovery rate corrections.

---

## Citation & License

If you use or build upon the code in this repository, please cite the accompanying manuscript and reference the permanent DOI provided via Zenodo. 

* Code released under the MIT License.
