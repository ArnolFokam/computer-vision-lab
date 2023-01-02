---
title: A Simple Framework for Contrastive Learning of Visual Representations
authors: Ting Chen, Simon Kornblith, Mohammad Norouzi, Geoffrey Hinton
year: 2020
---
[link to paper](https://arxiv.org/abs/2002.05709)

## TLDR;
The paper proposes a simple method of doing contrastive self-supervised learning that relies on training a model to give high similiraty score to augmentations of the same image and low similiraty score to augementation from different images.

## Problem Indentified
- Learning useful representations without human supervision is a long-standing problem
- Discriminative approaches relying on contrastive learning has been promising.
- However, methods proposed relies on complicated architectures to make it work.

## Solution proposed 
- This paper proposes a simple contrastive learning framework for self-supervised learning.

## Contributions
- A simple constrative learning framework
- Additionaly, they study the components of contrastive self-supervised learning that makes it work.

## Methodology
- The framework is divided into 4 steps:
	1. A *stochastic data augmentation* procedure that originally consist of:
		- Random cropping and resize
		- Random color distortion
		- Random Gaussian blur
	2. A *neural network encoder* $f(.)$ that turns the augmented samples $x \in \mathbb{R}^{H \times W \times C}$  into representations   $h = f(x) \in \mathbb{R}^{d}$
	3. A *non-linear projection head* $g(.)$ that turns the representations $h$ into $z$ through $\boldsymbol{z}=g\left(\boldsymbol{h}\right)=W^{(2)} \sigma\left(W^{(1)} \boldsymbol{h}\right)$ where $\sigma$ is a ReLU activation function.
	4. A *contrastive loss function* that operates on a pair of positive representations (representations of augmentation of the same image) w.r.t negative examples (representations of augmentations from different images). (see paper for formula)
	5. The LARS Optimizer is used due to its stability against large batch size.
	

## Findings
- This paper found that the critical components of contrastive self-supervised learning were:
	- Data augmentation. (Random crop and color distortions are very beneficial)
	- Non-linear transformation between the represenation and the contrastive loss.
	- Embedding normalization and appropriate temperature.
	- Batch size, training time and the size of the network (the bigger, the better)

## Limitations
- This frameworks is suitable when you have enough compute ressources to hold large batch sizes and train large models for a long period of time.

## Improvements (sort of)
- The framework works only for one positive pair. Can we upgrade the model to use more than one positive with respect to the anchor image?

## Cross-Reference
- This paper is a the precursor of the follow-up paper [[@chenBigSelfSupervisedModels2020]]

