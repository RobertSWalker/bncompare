# bncompare
Bayesian networks and comparative causal models of human complexity 

## Data
Bayesian networks and causal inferences of complexity across anthropological datasets, including Western North American Indian dataset, Binford hunter-gatherers, SESHAT, Ethnographic Atlas, and the Standard Cross-Cultural Sample

## R package bnlearn
bnlearn (bnlearn.com) is an `R` package for learning the graphical structure of Bayesian networks, estimating their parameters and performing some useful inference. We use the boostrap feature for understanding causal structures in each of the 5 datasets.

## Structure learning example: bootstrap multiple network structures
```splus
library(bnlearn)
set.seed(1)
boot <- boot.strength(all, R = 10001, cpdag = FALSE,
                      algorithm = "tabu")
boot[boot$strength > 0.8 & boot$direction >= 0.5, ]
avg.boot <- averaged.network(boot, threshold = .8)
plot(boot)
avg.boot

strength.plot(avg.boot, boot, threshold=.8,
              layout = "dot",
              shape = "rectangle")
```
