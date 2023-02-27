---
title: Self-supervised Label Augmentation via Input Transformations
authors: Hankook Lee, Sung Ju Hwang, Jinwoo Shin
year: 2020
---

## TLDR;
This paper proposes a label augmentation technique that combines labels from a supervised and self-supervised objective. This technique increases the quantity of self-supervisory signal our model can learn form and regulate the amout of invariance obtained in our representations.

## Problem Indentified
- Self-supervised learning has been shown to be extremly beneficial with the ability to predict which rotation was applied to the image.
- Additionally, most techniques adds this supervisory signal through a multi-task learning objective that might be difficult to optimize.
- These attempts have shown no significant gain in cases where  the dataset was fully annotated.
- The reason the authors put forward was that, the original supervised objective forces the network to be invariant to the transformation that should be predicted by the second objective and therefore, it becomes much more difficult to learn optimize the network.

## Solution proposed 
- The paper proposes a solution that combines the supervised and self-supervised objective into one single objective to jointly the transformation applied and the label to predict

## Contributions
- A new supervised technique that leverages self-supervision to get a boost of performance in the original supervised task.
- A self-distillation that aggregates the knowledge of multiple inference into a single one and backpropagate through the same network.

## Methodology
- Instead of having a multi-objective function to seperately optimize the supvised and the self-supervised objective, this paper combines both objective into one single objective.
- So let's say we have:
	- to classify between N labels
	- to classify between M transform labels
- We now have NxM labels with their corresponding weights.
- The difference with the multi-task objective is that instead of having different weight vectors for each labels we have (N + M), we now have NxM vectors equivalent to the number of new labels we get.

#### Forward pass (one iteration) - Aggregation Inference
- We augment an image M times considering that we have M transform labels
- We pass of each sample through the network and obtaine a softmax prediction on NxM labels
- For each prediction $i  \in  {1, 2, ..., N}$ and $j  \in  {1, 2, ..., M}$
	- We calculate the conditional probability of obtaining label i given j
		- This is done by computing the sofmax over the labels i for each j to obtain j softmax representations.
		- Then aggregating these predictions through the following formula
		$$
		P_{aggregated}(i|x) = \frac{exp(s_i)}{ \sum^{N}_{k=1} exp(s_k)}
		$$
		$$
		s_i = \frac{1}{M}  \sum^{M}_{j=1} w^{T}_{ij} \tilde{z}_j
		$$
- DO NOT FULLY COMPREHEND THE SELF-DISTILLATION MECHANISM

## Findings
- This technique provides a performance boost compared to baseline for case where there are imbalanced datasets
- This looks like a way to reduce the invariance of representation to transformation.
	- More specifically, with this techniques, we do not ignore the transforms for cases that matters. Color distortion for flowes and rotation for digits
- This technique gives a big boost in performance for cases when there is few data
![]()


## Limitations
- Induces another hyperparameter
- With respect to the experiments, it would have been convinient to compared the representation learned from the baseline and the proposed approach. Not just the baseline

## Improvements (sort of)
- 

## Cross-Reference
- 
