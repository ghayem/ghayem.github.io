---
layout: archive
title: "Projects"
permalink: /projects/
icon: "fas fa-diagram-project"  # This is optional; explained in step 4
author_profile: true
---

A selection of my recent and past projects.

## NeuroConText: Contrastive Learning for Neuroscience Meta-Analysis with Rich Text Representation

- *Objective:* Meta‑analysis is a powerful tool to understand how cognitive processes are represented in the human brain. It aggregates thousands of neuroimaging studies to extract reproducible activation patterns associated with concepts like attention, language, or emotion. However, existing meta‑analysis tools depend on manually curated keywords or sparse coordinate tables, which lose much of the rich conceptual information found in full scientific texts. As the neuroscience literature grows exponentially, automated methods that can directly learn from text and link it to brain data are becoming essential for scalable, data‑driven discovery.

- *What we proposed:* We introduce NeuroConText, a contrastive learning framework that aligns the full text of neuroimaging studies with their corresponding activation maps derived from coordinate‑based meta‑analysis (CBMA):

I. Each article is represented as multiple text chunks processed by a transformer‑based text encoder (LLMs like Mistral 7B) that captures contextual meaning beyond keyword frequency (TFIDF).

II. For the spatial modality, we start from stereotactic activation coordinates reported in each study and use kernel density estimation (KDE) to reconstruct continuous 3D brain maps. These maps are then projected into a low‑dimensional functional space using embeddings from the DiFuMo (Dictionary of Functional Modes) atlas, which captures distributed brain networks.

III. We train the model using a joint loss function that combines a mean squared error (MSE) loss for reconstructing the brain maps from text (text→map), and a contrastive loss to align matching text–map pairs and improve cross‑modal retrieval performance.

IV. Once trained, the model supports several tasks: retrieving relevant brain maps for an input text, and predicting a brain pattern from new text (text→map).

- *Advantages over previous meta‑analytic models:*

1. Improves retrieval: Achieves significantly higher Recall@10 (22.6%) using full-body text vs 7% (NeuroQuery) and 1.4% (Text2Brain).
2. Handles long texts effectively via chunking and mean-pooling, while others mostly rely on abstracts or short snippets.
3. Matches or outperforms in reconstruction, with competitive Dice scores across thresholds, and better qualitative alignment with described brain regions.
4. Bridges semantic gaps using contrastive learning, outperforming bag-of-words and TF-IDF models on meaningful alignment.
5. Supports short-text input via LLM-based augmentation, improving generalization in both retrieval and reconstruction tasks.


- 
## Peaks2Image: Reconstructing fMRI Statistical Maps from Reported Peak Coordinates

- *Objective:* Many neuroscience articles only report activation peaks (stereotactic coordinates), losing rich spatial detail. This limits meta‑analysis and downstream spatial modeling. Recovering full maps from peaks would let us leverage legacy literature data more fully.

- *What we proposed:* We developed Peaks2Image, a neural reconstruction model that converts peak sets into a Gaussian kernel representation, reduced via DiFuMo basis, then uses an MLP to predict full brain maps. Additionally, we integrated decoding tasks to map reconstructed images to their corresponding semantic labels.

- *Advantages over SOTA:*
1. Produces continuous, dense reconstructions where previous methods had none or only sparse interpolations.
2. Enables zero‑shot decoding (concept labeling) from peak inputs — in evaluations, they decoded 58 of 81 cognitive terms in a zero-shot setting across ~43k images.
3. Bridges text and brain domains: once you reconstruct maps, you can apply models originally designed for image-level meta-analysis.

- *Paper:* (Peaks2Image)[https://inria.hal.science/hal-05243856]
