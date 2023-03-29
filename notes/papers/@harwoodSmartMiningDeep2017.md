---
title: Smart Mining for Deep Metric Learning
authors: Ben Harwood, Vijay Kumar B. G, Gustavo Carneiro, Ian Reid, Tom Drummond
year: 2017
---

#mining #deep-metric-learning

## TLDR;
This paper proposes a new mining strategy that selects negative and positive samples according to certain constraints imposed on the negative and positive samples to be mined. Additionaly it add a global loss to the triple to infer some structure to the embeddings  obtained.


## Problem Indentified
- Triplet objectives are very useful techniques for deep metric learning
- However generating triplets can cause a problem for such scenarios
	- Generation all possible combinations is an $O(n^3)$
- Therefore, we need a more effiecient way to generate these triplets

## Solution proposed 
- A novel deep metric learning method that combines a global and triplets loss that operates on triplets generated from a smart sampling method.

## Contributions
- a novel deep metric learning method

## Methodology
- This methods has two components
	- **The loss**
		- In addition to a simple triplet loss, the method uses a global loss to modifies the global structure of the embedding.
		- This global loss function basically ensures that the all positives are roughly the ame distances to the anchor. The same goes for the negatives with respect to the anchor.
	- **The smart triplet mining method**
		- we identity a set of nearest neighbours for each anchor $x_i$
		- Our positive mining region are chosen such that the distance between them and the anchor is non-zero.
		- Our negative mining region are chosen such that there is at least on positive more closer to the anchor than them.
		- More formally we choose any negative such that:
$$
\begin{aligned}
\left\|f^{(1)}\left(\mathbf{x}_i, \theta_f\right)-f^{(3)}\left(\mathbf{x}_i^{-}, \theta_f\right)\right\|_2^2> \\
\kappa \cdot\left\|f^{(1)}\left(\mathbf{x}_i, \theta_f\right)-f^{(2)}\left(\mathbf{x}_i^{+N N}, \theta_f\right)\right\|_2^2,
\end{aligned}
$$
					- Then, we form triplets with our mined samples. Random mining is used for cases where there are no valid negatives.
					- $\kappa$ is tuned through an automatic parameter selection using a linear model
## Findings
- Triplet mining with automatic parameter selection is the best
- This mining strategy gives better triplets than the random sampling strategy.

## Limitations
- 

## Improvements (sort of)
- 

## Cross-Reference
- 
