---
title: Rethinking the Augmentation Module in Contrastive Learning: Learning Hierarchical Augmentation Invariance with Expanded Views
authors: Junbo Zhang, Kaisheng Ma
year: 2022
---

#representation-learning #contrastive-learning #self-supervised-learning  #data-augmentation 

## TLDR;

## Problem Indentified
- self-supervised learning is very valuable.
- But if we consider the way augmentation are done, this incentivises the model to treat all augmentation equally
- In addition, augmentaion impacts performance in different ways, rotation in flowers might be more beneficial than color distrotion when compare to imagenet.
- Also, strong augmentation are sometimes incentivized in contrastive self-supervised learning
- However, they may bring unecessary invariance in the representation. (Invariance to color of flowers)

## Solution proposed 
- This paper proposes to solve the above program 

## Contributions
- A new contrastive learning framwork that leverages multiple 

## Methodology
- This contrastive learning framework is divided into different phases

#### Hierachical augmentation invariance
- Constructs multiplue augmentation pipeline by *"add one strategy"*
- add one strategy = next pipeline has +1 new operation than the previous
- 4 pipelines = 4 pairs of views generated

- Then, contrastive loss is computed at different depths of the newtork and summed up to form the overall loss function.

- For each depth, we use the augmentation embedding $f_{aug}$ to first input the augmentation params that is concatenated and pass through the projection head to get a final representation.
	- Note: the input of $f_{aug}$ is a 4-d array that are the parameters of a specific augmentation operation we want to be invariant to at stage $i$



## Findings
- 

## Limitations
- Increases the number of views generated.
- Complexifies the simple contrastive framework  originally proposed.
- Dependency in pipelines is not taken into account if the pipelines are generated through a *add-one strategy*.
- The paper computes multiple loss at different network depth and claims it distributes augmentation invariance impact more widely and restricts insignificant variance to deep layers
	- How and Why is that the case?

## Improvements (sort of)
- 

## Cross-Reference
- 
