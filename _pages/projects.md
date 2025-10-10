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

[NeuroConText_framework_training.pdf](https://github.com/user-attachments/files/22848778/NeuroConText_framework_training.pdf)

[NeuroConText_framework_inference.pdf](https://github.com/user-attachments/files/22848783/NeuroConText_framework_inference.pdf)

[retrieval_leftOutArticles.pdf](https://github.com/user-attachments/files/22848784/retrieval_leftOutArticles.pdf)

[DiceScore_articles_test_.pdf](https://github.com/user-attachments/files/22848785/DiceScore_articles_test_.pdf)

[brain_maps_reconstruction_dice_leftOutArticles_best_median_worst.pdf](https://github.com/user-attachments/files/22848789/brain_maps_reconstruction_dice_leftOutArticles_best_median_worst.pdf)

**Objective:**  
Meta‑analysis aggregates thousands of neuroimaging studies to extract reproducible activation patterns associated with concepts like attention, language, or emotion. However, existing tools rely on manually curated keywords or sparse coordinate tables, missing the rich information in full texts. As the literature grows, scalable methods that link full text to brain data are essential.

**What we proposed:**  
We introduce **NeuroConText**, a contrastive learning framework that aligns full-text articles with activation maps derived from coordinate‑based meta‑analysis (CBMA):

- Articles are split into text chunks and processed with transformer-based encoders (e.g., Mistral 7B) to extract rich contextual representations.
- Activation coordinates are used to reconstruct 3D brain maps via KDE, then projected into a low-dimensional space using DiFuMo atlas embeddings.
- A joint loss function is used: MSE for text-to-map reconstruction and contrastive loss to align matching text–map pairs.
- Supports retrieval and prediction tasks, including text→map inference.

**Advantages over prior models:**

- 📈 Improves Recall@10 in retrieval: 22.6% vs 7% (NeuroQuery) and 1.4% (Text2Brain)
- 📚 Handles long-form text through chunking and pooling
- 🧩 Matches or outperforms baselines in Dice reconstruction scores
- 🔍 Uses contrastive learning to bridge semantic gaps
- ✍️ Supports generalization with short-text input via LLM-based augmentation

**Paper:**  
[NeuroConText]([https://inria.hal.science/hal-05243856](https://www.biorxiv.org/content/10.1101/2025.05.23.655707v1.abstract))

---

## 🧠 Peaks2Image: Reconstructing fMRI Statistical Maps from Reported Peak Coordinates

**Objective:**  
Neuroscience articles often report peak activation coordinates instead of full statistical maps, limiting spatial modeling. Recovering full maps from peak sets allows leveraging legacy data for modern meta-analytic pipelines.

**What we proposed:**  
We developed **Peaks2Image**, a neural model that:

- Converts sets of peak coordinates into smoothed KDE maps
- Projects them into DiFuMo space and uses an MLP to reconstruct full 3D images
- Supports semantic decoding (e.g., predicting cognitive concepts) directly from reconstructed maps

**Advantages over prior work:**

- 🧠 Produces dense, continuous reconstructions from sparse peaks
- 🔤 Enables zero-shot concept decoding: 58 of 81 cognitive terms successfully decoded
- 🔄 Bridges coordinate-only articles to text/image-based analysis pipelines

**Paper:**  
[Peaks2Image](https://inria.hal.science/hal-05243856)

---
