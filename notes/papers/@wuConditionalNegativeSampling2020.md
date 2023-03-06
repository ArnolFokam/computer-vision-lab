---
title: Conditional Negative Sampling for Contrastive Learning of Visual Representations
authors: Mike Wu, Milan Mosse, Chengxu Zhuang, Daniel Yamins, Noah Goodman
year: 2020
---

## TLDR;
This paper proposes negative sampling strategy that condition the selection of appropriate negatives on their similiarity value with anchor. In other words, they select a subset of the original negatives that are the closest to the original anchor representation.

## Problem Indentified
- Contrastive self-supervised learning extensively depends on negative samples
- Besides random sampling, some techniques hard negative mining
- However, it is not clear if these methods the MI related to the infoNCE objective function
- Additionally, the paper claims that we do not if this approach is beneficial to the downstream tasks.

## Solution proposed 
- The paper proposes a new sampling strategy the conditional the sampling of negatives based on their similarity with the positive example.

## Contributions
- A novel negative sampling strategy that depends on a conditional distribution
- A theoritical framework that provides a way to select the appropriate distribution that still preserves the MI bound

## Methodology
- This method proposes the following distribution
	- Choosing negative whose similarity with the anchor is above a certain threshold
	- The **w** percentile with similarities greater than these thresholds are chosen are choosen.
	- The sampled negatives almost form something like a ring around the positive anchor
	- Additional the size of this ring is reduce over training.

## Findings
- The paper proofs that that family of distribution that still preserves the bound are those that takes a subset of all the negatives and are closer to the positive.
- In the overall, this method is very beneficial to transfer accuracy

## Limitations
- Discards the other negative samples discards information that could be used during training

## Improvements (sort of)
- What about weighting the instance instead of discarding them

## Cross-Reference
- 