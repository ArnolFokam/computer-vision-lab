---
title: Rethinking the Augmentation Module in Contrastive Learning: Learning Hierarchical Augmentation Invariance with Expanded Views
authors: Junbo Zhang, Kaisheng Ma
year: 2022
---

#representation-learning #contrastive-learning #self-supervised-learning  #data-augmentation 

## TLDR;
This paper proposes a new contrastive frameword at data augmentation from a different perspective. it claims that all operations used in the data augmentation are treated uniformly in the data augmentation pipeline for the original data augmentation pipeline. Therefore, we need to make sure the model treats different operations differently. A solution proposed is to heirarchically make the model invariant to differnet transforms at different depth of its architecture

## Problem Indentified
- self-supervised learning is very valuable.
- But if we consider the way augmentation are done, this incentivises the model to treat all augmentation equally
- In addition, augmentaion impacts performance in different ways, rotation in flowers might be more beneficial than color distrotion when compare to imagenet.
- Also, strong augmentation are sometimes incentivized in contrastive self-supervised learning
- However, they may bring unecessary invariance in the representation. (Invariance to color of flowers)

## Solution proposed 
- This paper proposes to solve the above problem by diluting the dependency of representations on augmentations operation to other layers of the self-supervised model.

## Contributions
- A new contrastive learning framwork that provide a ney way of learning invariance from data augmentation.

## Methodology
- This contrastive learning framework is divided into different phases

#### Hierachical augmentation invariance
- Constructs multiplue augmentation pipeline by *"add one strategy"*
- add one strategy = next pipeline has +1 new operation than the previous
- 4 pipelines = 4 pairs of views generated

- Then, contrastive loss is computed at different depths of the newtork and summed up to form the overall loss function.
		- Each pair of views  is passed to its corresponding depth.
			- For each pipeline in a set of N pipelines the encoder network divided into N sub-parts.
			- Each pair of view generated by a pipeline is passed to its corresponding sub-parts
			- The objective to make each part of the enoder invariant to a specific transform
		- Extra CNN layers are added to the shallower layers of the network so that they match the output representation shape of the last layer of the network.
		- Therefore the is no extra layers for the last sub-part of the network as it already contains the last layer of the original network

- For each depth, we use the augmentation embedding $f_{aug}$ to first input the augmentation params. The output is concatenated and pass through the projection head to get a final representation.
	- Note: the input of $f_{aug}$ is a 4-d array that are the parameters of a specific augmentation operation we want to be invariant to at stage $i$
- The augmenation embedding is used to prevent the invariance brought by the self-supervised task to remove all the information about the transform used.


## Findings
- The order of augmentation operations seems to drastically influence the performance of our models

## Limitations
- Computational overhead
	- More views generated
	- Need run N forward pass because of the N pipelines
	- Extra layers on the shallower layers because of multi-stage loss function
	- Might need to run N models if not using share weights (because of the N pipelines)
- Complexifies the simple contrastive framework  originally proposed.

## Improvements (sort of)
- Don't know...

## Cross-Reference
- The work is inspired by the idea of [[@leeSelfsupervisedLabelAugmentation2020]] to do something with augmentation embeddings
