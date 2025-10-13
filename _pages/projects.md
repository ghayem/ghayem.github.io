---
layout: archive
title: "Projects"
permalink: /projects/
icon: "fas fa-diagram-project"
author_profile: true
---

A selection of my recent and past projects.

---

## 🧠 NeuroConText: Contrastive Learning for Neuroscience Meta-Analysis with Rich Text Representation


<p align="center">
  <img width="400" height="1070" alt="NeuroConText_framework_training" src="https://github.com/user-attachments/assets/0c8ff2b2-0650-4778-bf58-762c290a2bc8" />
  
  <img width="400" height="941" alt="NeuroConText_framework_inference" src="https://github.com/user-attachments/assets/a1cd36c0-ebae-4381-8e2e-fc96328bf999" />

</p>

<p align="center">
  <img width="300" height="722" alt="retrieval_leftOutArticles" src="https://github.com/user-attachments/assets/b7aa343c-1f2f-4f7e-a689-da38e1d44c4c"  />

  <img width="300" height="716" alt="DiceScore_articles_test_" src="https://github.com/user-attachments/assets/b716de4d-966c-427b-8b7b-e85512c65b79"  />
  
  <img width="300" height="1056" alt="brain_maps_reconstruction_dice_leftOutArticles_best_median_worst" src="https://github.com/user-attachments/assets/5ee2ca2f-12ea-4fd9-a6c8-00ab1a6535ab" />

</p>

**Objective:**  
Meta‑analysis aggregates thousands of neuroimaging studies to extract reproducible activation patterns associated with concepts like attention, language, or emotion. However, existing tools rely on manually curated keywords or sparse coordinate tables, missing the rich information in full texts. As the literature grows, scalable methods that link full text to brain data are essential.

**What we proposed:**  
We introduce **NeuroConText**, a contrastive learning framework that aligns full-text articles with activation maps derived from coordinate‑based meta‑analysis (CBMA):

- Articles are split into text chunks and processed with transformer-based encoders (e.g., Mistral 7B) to extract rich contextual representations.
- Activation coordinates are used to reconstruct 3D brain maps via kernel density estimation (KDE), then projected into a low-dimensional space using DiFuMo atlas embeddings.
- A joint loss function is used: MSE for text-to-map reconstruction and contrastive loss to align matching text–map pairs.
- Supports retrieval and prediction tasks, including text→map inference.

**Advantages over prior models:**

- 📈 Improves Recall@10 in retrieval: 22.6% vs 7% (NeuroQuery) and 1.4% (Text2Brain)
- 📚 Handles long-form text through chunking and pooling and uses LLM to capture semantic
- 🧩 Matches or outperforms baselines in Dice reconstruction scores
- 🔍 Uses dual loss with convergence guarantee: contrastive learning to improve retrieval and MSE to support reconstruction
- ✍️ Supports generalization with short-text input via LLM-based augmentation

**Papers:**  
1. [NeuroConText - Journal version - bioRxiv](https://www.biorxiv.org/content/10.1101/2025.05.23.655707v1.abstract)
2. [NeuroConText - Conference version - MICCAI'24](https://link.springer.com/chapter/10.1007/978-3-031-72384-1_31)

---

## 🧠 Peaks2Image: Reconstructing fMRI Statistical Maps from Reported Peak Coordinates

<img width="600" height="1708" alt="Peaks2Image" src="https://github.com/user-attachments/assets/df4ddf8f-94ba-43a9-abb4-d2671ad974e6" />


**Objective:**  
Neuroscience articles often report peak activation coordinates instead of full statistical maps, limiting spatial modeling. Recovering full maps from peak sets allows leveraging legacy data for modern meta-analytic pipelines.

**What we proposed:**  
We developed **Peaks2Image**, a neural model that:

- Converts sets of peak coordinates into smoothed kernel density estimation (KDE) maps
- Projects them into DiFuMo space and uses an MLP to reconstruct full 3D images
- Supports semantic decoding (e.g., predicting cognitive concepts) directly from reconstructed maps

**Advantages over prior work:**

- 🧠 Produces dense, continuous reconstructions from sparse peaks
- 🔤 Enables zero-shot concept decoding: 58 of 81 cognitive terms successfully decoded
- 🔄 Bridges coordinate-only articles to text/image-based analysis pipelines


**Paper:**  
[Peaks2Image](https://inria.hal.science/hal-05243856)

---

## 🧠 Sparse Dictionary Learning for Discriminative and Interpretable Brain Connectivity Patterns  
<p align="center">
<img width="500" height="612" alt="interpret_discriminate" src="https://github.com/user-attachments/assets/515b4341-3877-4c5a-a6a3-e209f7f52b2e" />
</p>

<p align="center">
<img width="500" height="881" alt="MIND_talk_Jun4_2024-compressed" src="https://github.com/user-attachments/assets/c69068df-6ce1-4027-a3fd-082819f360da" />
</p>

**Objective:**  
Group-level analysis of resting-state fMRI can extract valuable biomarkers, but traditional pipelines either lack interpretability or fail to model population heterogeneity. Standard ICA + temporal functional network connectivity (tFNC) approaches yield high-dimensional features that are hard to interpret. In this project aimed to extract sparse, low-dimensional, and interpretable features that preserve discriminative information for classifying schizophrenia (Sz) versus healthy controls (HC).

**What we proposed:**  
We introduced a novel framework combining group ICA and dictionary learning:

- Group-ICA with entropy-bound minimization (ICA-EBM) is applied to multi-subject resting-state fMRI to extract subject-specific brain networks and time courses.
- tFNC matrices (Pearson correlations between time courses) are computed per subject, vectorized, and used as high-dimensional connectivity features.
- A dictionary learning model jointly learns:
  - Sparse representations of each subject’s tFNC feature vector.
  - A linear classifier for discrimination between HC and Sz.
- Each learned **dictionary atom** is reshaped into a symmetric matrix, interpretable as a distinct connectivity pattern between brain networks.
- **Two-sample t-tests** are used on the sparse coefficients to identify statistically significant, group-discriminative patterns.

**Advantages over prior models:**

- 🧠 **Interpretable features**: Each dictionary atom corresponds to a meaningful, visualizable brain connectivity pattern.
- 📉 **Dimensionality reduction**: Sparse representations are compact and informative, improving classifier robustness.
- 📊 **Improved classification** based on Accuracy and F1-score.
- 🧪 **Statistical validation**: Multiple atoms show significant between-group differences (HC vs. Sz) via t-tests, suggesting interpretable biomarkers.
- 🔍 **Visualization-ready**: Atoms can be reshaped and visualized as symmetric matrices, analogous to tFNCs.

**Paper:**  
[📄 ICASSP 2023](https://ieeexplore.ieee.org/abstract/document/10096473)

---
