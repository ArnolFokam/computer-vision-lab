---
title: Understanding Contrastive Representation Learning through Alignment and Uniformity on the Hypersphere
authors: Tongzhou Wang, Phillip Isola
year: 2022
---

#representation-learning #contrastive-learning #self-supervised-learning 

## TLDR;
The paper proposes to replace the origin InfoNCE used in contrastive self-supervised with two metrics that optimizes for alignment and uniformity of representation on a hypersphere latent space.

## Problem Indentified
- Contrastive Self-Supervised Learning is outstanding.
- No problem rely identified!

## Solution proposed 
- The paper does not provide a solution to a problem but instead provide empirically result to just a particular hypothesis while proposing new optimizable metrics for SSL based on these hypothesis.

## Contributions
- Proposes *alignment* and *uniformity* as two measures of representations quality.
- A proof that contrastive loss optimizes these metrics
- A showcase of a strong agreement between both metrics and downstream performance
- A empirical demonstration of the advantage of use both metrics as objective function with no other contrastive loss.

## Methodology
- The paper proves that contrastive loss optimizes for two metrics
	- **alignment**: distance between positive samples
	- **uniformity**: spread of the representation across the hypershere
- In other terms, if we simplify the logarithmic fraction in terms of addition and substraction, we get two terms where optimizing these terms are equivalent to optimizing *uniformity* and *alignment*.
- The paper proposes a way to calculate each metric
	- **alignment**: l2 distances between positive pairs
	- **uniformity**:  gaussian kernel density estimation
- They optimize these terms instead of optimizing the original InfoNCE loss function

## Findings
- Optimizing these metrics affects downstream performance and can be beneficial to representations if tuned appropriately.

## Limitations
- The representation learned on a hypersphere are not the representation used during finetuning
- The model also mostly learn from longer training, bigger models and using the right augmentations. The paper didn't really explained how those factors affects alignment and uniformity.
- It might be more difficult to validate this geometric properties w.r.t high dimensional representation. How would this observation hold when comparing dataset size against representation's dimensionality.
- - The method only work with hyperparemeter tuning and the average perf compared to using the original metric was not given

## Improvements (sort of)
- Focus on alignment, it seems to be a decisive factor in quality of representations.

## Cross-Reference
- 
