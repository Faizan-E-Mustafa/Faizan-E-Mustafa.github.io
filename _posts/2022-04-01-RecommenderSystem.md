---
title: "Recommender System for a German Healthcare Provider"
date: 2022-04-01
permalink: /RecommenderSystem/
tags: [Projects]
excerpt: "At QUIBIQ GmbH, developed a graph neural network recommender to suggest GOP service codes based on patient ICD diagnosis codes."
toc: false
---

## Project overview

At **QUIBIQ GmbH**, I worked in Research and Development on a recommender system for a German healthcare provider. The system recommends GOP service codes based on a patient's ICD diagnosis codes.

## Approach

1. **Patient graph construction.** Built a patient graph connecting patients with shared or similar diagnosis patterns. Patient representations included demographic and diagnosis information; one representation used an autoencoder to reduce the dimensionality of ICD diagnosis vectors.
2. **Recommend procedures.** Trained a graph neural network to predict GOP service codes from the patient graph. The paper evaluated the models on a synthetic patient database and reported an average 6.48% F1-score improvement over baseline models.
3. **Analyze patient clusters.** Used the graph models to identify groups of patients associated with distinct treatment patterns.
4. **Interpret and present results.** Applied saliency maps to examine model recommendations, and built a Dash dashboard to display the results.

For more details, see the [paper](https://pubmed.ncbi.nlm.nih.gov/36100347/).
