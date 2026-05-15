---
title: Image analysis using embeddings and interactive plots
date: 2026-05-15
tags:
- methods
- python
- cv
---

# Data cleaning

Sometimes you may have many images and want a quick way to understand what is in the dataset. Especially, when labels are missing or noisy, when images come from different sources, or when you suspect there are duplicates, odd samples, or hidden groups that are hard to find by looking through files one by one. This is hard to do with 2D-images, which are essentially big matrices that are diffcult to compare meaningfull. An extemely powerful way of dealing with this is to leverage image encoders, and turn 2D images into 1D vectors of visual content: image embeddings.

The basic idea is simple: turn each image into a set of numbers that captures important visual features, then place those images in a low-dimensional map (PCA/tSNE) where similar images sit close together. This makes it easier to spot groups, outliers, mix-ups, and labeling problems. The interactive part is useful because you can inspect points, select subsets, and run the ordination again on smaller parts of the dataset. In practice, this turns embeddings into a practical tool for cleaning image data step by step.

<div class="image-thumb">
    <a href="https://github.com/mluerig/demo-image-embeddings" target="_blank">
        <img src="https://raw.githubusercontent.com/mluerig/demo-image-embeddings/main/int_plot-animation.gif" style="width: 80%;">
    > Interactive plots using dimensionality-reduced embeddings are a powerfull tool for data-wrangling. < </a>
</div>

# Quantiative analysis

Embeddings can also be useful for quantitative analysis, not just visualization. If the encoder is metric and distances in embedding space have a clear meaning, then those distances can be used to compare samples more directly. This makes it possible to measure similarity, find gradients between forms, group related images, or test whether some samples are more distinct than others in a more formal way. 

One example of such an application of metric image embeddings can be found in our preprint: [Aposematic color patterns are the dominant axis of phenotypic diversification in Nymphalid butterflies](https://www.biorxiv.org/content/10.1101/2025.09.30.678834v1) 

