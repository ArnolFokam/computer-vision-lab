---
title: Contrastive Learning with Hard Negative Samples
authors: Joshua Robinson, Ching-Yao Chuang, Suvrit Sra, Stefanie Jegelka
year: 2021
---

#representation-learning #contrastive-learning #self-supervised-learning #sampling-methods

## TLDR;
This paper proposes a new contrastive objective for self-superivsed learning that explicity re-weights the affinity of our loss function to a particular level of hardness for negative samples through a probability distribution that has a tunnable hyper-parameter $\beta$.

## Problem Indentified
- Contrastive Self-Supervised Learning is great but requires sampling from negatives without truthful information about the semantic content of an image (except the content)
- Therefore, random sampling to get negative sample might be detrimentory to model performance.

## Solution proposed 
- This paper proposes a sampling technique that builds a **tunnable** sampling distribution.
- This tunnable distribution  give an importance sampling value to negatives so as to favour a particular similarity score for a negative sample.

## Contributions
- New negative sampling strategy for self-supervised contrastive learning

## Methodology
- This paper designs a distribution which depends on embedding of the anchor.
- The loss proposed is similar to [[@chuangDebiasedContrastiveLearning2020]] however, negative samples are re-weighted such that the model focus on negative samples with a particular level of hardness. This affinity can be ajusted to arbritrary level of hardness using the hyperparameter $\beta$.

## Findings
- Performance is competitive compared to debaised and baseline SimCLR however benefits drops as we increase the negative sample size

## Limitations
- **Principle 2** from the paper might be *false* negative samples with very similar embeddings as the anchor might turn out to be in fact semantically very similar content.
	- *The most useful negative samples are ones that the embedding currently believes to be similar to the anchor.*
- Introduces another tunnable hyperparameter on an already expensive self-supervised contrastive learning method.

## Improvements (sort of)
- Can this still yeild performance improvement without the shenanigans of Debaised Contrastive Learning ([[@chuangDebiasedContrastiveLearning2020]]) ?

## Cross-Reference
- The loss proposed is similar to that of [[@chuangDebiasedContrastiveLearning2020]] but with the ability to vary the level of hardness of negative samples through a custom probability distribution.

