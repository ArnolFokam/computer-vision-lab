---
title: Rethinking Minimal Sufficient Representation in Contrastive Learning
authors: Haoqing Wang, Xun Guo, Zhi-Hong Deng, Yan Lu
year: 2022
---
#representation-learning #contrastive-learning #self-supervised-learning #sampling-methods 

## TLDR;

This paper proves the traditional contrastive maximize shared information between representation of similar but at the detriment of ignored task-relevant information. As a result, it devices a second objective term that maximizes the shared information between the view and its representation. The objective is to use this unsupervised objective to enable representations to contain task relevant information.

## Problem Indentified
- In contrastive self-supervised leanring, the objective is something to increase the mutual information between representations of views of the same image.
- To perform this, one view is the supervisory signal of the other view.
- However, this encorage the ssl model to ignore non-shared information and as a result, might remove task relevant information.

## Solution proposed 
- The paper proposes a new contrastive framework that first maximizes the mutual information between the input and representation to introduce more task relevant information.

## Contributions
- Theoritical proof that contrastive learning overfit to shared-information between viewa
- A new contrastive framework that also aims a maximizing the mutual information between the input and the representation.

## Methodology
- Proofs use bayes error rate (classification) and Expected Squared Prediction Error (regression) to show that minimal suffiecient representation will be less powerful becaus it does not contain task specidication.
- The papers also proposes to maximize mutual information between the input and the representation through two methods.
	- Method 1
		- Through a reconstruction loss function
	- Method 2
		- (at the representation level) perform an InfoNCE objective between z (representation) and v (views)

## Findings
- Using reconstruction loss to conserve task-relavant information is better than the second implementation
- Representation learning by contrastive leanring are already close to minimal as removing further infromation does to seem to change something.
- There is a sweep spot in the amount of mutual information between the input and the representation we can obtain.

## Limitations
- Increasing the mutual information between views and their representation can also introduce noise. So there is the need to adjust the hyperparameters accordingly
- Non-shared task information can not be ignore for cross-domain tasks but could be for tasks in the training with a similar distribution as the pre-training data

## Improvements (sort of)
- 

## Cross-Reference
- 
