---
title: A Theoretical Analysis of Contrastive Unsupervised Representation Learning
authors: Sanjeev Arora, Hrishikesh Khandeparkar, Mikhail Khodak, Orestis Plevrakis, Nikunj Saunshi
year: 2019
---

#theory #representation-learning #contrastive-learning 

## TLDR;

## Problem Indentified
- Contrastive representation learning has a positive effect on downstream task performance
- However, its theoritical foundations has received little to no interest

## Solution proposed 
- Theoritical analysis of contrastive learning

## Contributions
- Introduce latent classes to formalize semantic similarity
- The paper shows solution to inherent limitations of negative sampling
- It also proposes a revised objective function that can work with more positive samples 
- All this through its theoritical framework.

## Methodology
- 

## Findings
- 

## Limitations
- Assumes latent classes suggested will always be equivalent to classes from downstrean taskch 
- The bases on which the framework sits constrains contrastive learning to a particular way of doing it
	-  $(x, x^+) \sim \mathcal{D}_c$ are assumed to be $i.i.d$ but *what if I condition the sampling of $x^+$ from $x$ through a custom positive strategy?*
	- Latent classes are the same as classes from downstream tasks but **what if class from downstream tasks are compositions of those latent class instead.**
		- To be fair, the paper also makes this statement *Since classes are allowed to overlap and/or be fine-grained, this is a plausible formalization of “similarity.”*
	This limits the theoritical framework to a subset of problems.

## Improvements (sort of)
- 

## Cross-Reference
- 

