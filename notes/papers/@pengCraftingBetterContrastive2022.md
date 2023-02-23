---
title: Crafting Better Contrastive Views for Siamese Representation Learning
authors: Xiangyu Peng, Kai Wang, Zheng Zhu, Mang Wang, Yang You
year: 2022
---

#representation-learning #contrastive-learning #self-supervised-learning #data-augmentation 

## TLDR;
RandomCrop might generate false positives in self-supervised learning. Therefore, this paper proposes a new cropping technique that leverages the semantic content learned by the model to identify the region of interest to focus on during croping (semantically-rich region)

## Problem Indentified
- Self-supervised learning is great
- But often rely on RandomCrop to generate positive samples views
- Unfortunately, this technique is prone to give false positive
- Therefore, we need a better cropping technique to get those positve samples

## Solution proposed 
- This paper proposes a semantically aware cropping technique that looks at the content of an image and identify pontetial crops that can be used.

## Contributions
- A semantically-aware cropping technique
- A better method to provide crops from images

## Methodology
- This paper analyzes the heatmaps obtained from images in the convulation layers of trained models during on-going epochs and comes to the conclusion that:
	- These models can roughly identify the content of an image
	- However, they might need some warm-up during the early stage of training
- The first steps is to let the model train with RandomCrop for few epochs to allow it to learn enough sematic content

#### Semantic-aware localization
- At each training step, we calculate the image heatmap (normalized between 0 and 1) and threshold this heatmap to get salient points.
- We create a bounding box around those points to get the salient region

#### Center-suppressed Sampling
- Reducing the region of interest might lead to crops having roughly the same content
- Therefore, this paper proposes a technique to reduce probability of crops being sampled at the center.

## Findings
- Performance improvements upon baseline approach is **consistent** in image classification and object detection.
- This technique is also beneficial irrespective of the transform chosen (the authors might have only shown transforms that did just that, but still, very encouraging)

## Limitations
- Nothing huge, could clarify a little the use of terms such as $B_{x0},B_{x1},B_{y0} and B_{y1}$ are they the bounding box coordinates?
- - The technique requires a quite consequential manipulation of the original training loop

## Improvements (sort of)


## Cross-Reference
- 

