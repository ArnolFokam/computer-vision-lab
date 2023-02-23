---
title: Unsupervised representation learning by invariance propagation
authors: Feng Wang, Huaping Liu, Di Guo, Sun Fuchun
year: 2020
---

#representation-learning #contrastive-learning #self-supervised-learning  #semi-supervised-learning  #sampling-methods 

## TLDR;
The paper proposes a novel self-supervised method that leverages relationship between unlabelled instance in a KNN graph to sample positive and negative samples for a constrastive loss function though a hard sampling strategy.

## Problem Indentified
- Self--supervised learning is great but ignores the relationship between different instances generated

## Solution proposed 
- A contrastive self-supervised method that builds a graph of instances to identify the relationship betwen anchors and samples
- From such relationship, identity hard sample (positive and negative) for training

## Contributions
- A novel contrastive self-supervised method that leverage relationship between unlabelled instances

## Methodology
- The method is divided into three steps:
	- **Positive Sample Discovery**
		- Identity positive samples through transitive relation in a KNN graph.
			- Nearest neighbours and **nearest neighbours of nearest neighbours**
	- Hard Sampling Strategy
		- Get the top k hardest positive samples from the KNN graph
		- Get all the KNN instances as the background set (denominator infoNCE) 
- Since this method might yield incorrect result during the first steps of training, the paper adds an instance discrimination loss.
- This loss is optimized during the first t steps of training and the second loss that uses the method above is added afterwards though a time-dependent weighting function.


## Findings
- The results are competitve with other  self-supervised learning techniques
- The method seems to give better seperation between catergories compared to the instance discrimination model in [[@wuUnsupervisedFeatureLearning2018]].

## Limitations
- Hard negatives might just be images with the same semantic content as the anchor
- Additional hyper-parameters to tune
- Is it not just more positive samples that makes this method better?

## Improvements (sort of)
- 

## Cross-Reference
- 


