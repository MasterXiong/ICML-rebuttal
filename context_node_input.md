MetaMorph concatenates the morphology context features $c^i$ with state features $s^i_t$ as the input to node $i$, so the node embedding is computed as $e^i = W \left[ s^i_t; c^i \right] + b = W_s s^i_t + W_c c^i + b$, where $W_s$ and $W_c$ are the sub-matrices that encode state $s^i_t$ and context features $c^i$ respectively.
As $c^i$ is fixed, this is equivalent to adding a context-conditioned bias term $W_c c^i$ to $e^i$. 

As the reviewer suggested, this additional bias term could in principle enable further computation and node interaction to condition on the morphology in flexible ways. 
However, empirically it may not be the optimal way to do so. 
E.g., [Galanti and Wolf (2020)](https://arxiv.org/pdf/2002.10006.pdf) theoretically prove that compared to concatenation, hypernetwork (HN) can more effectively learn a different function for each context instance. 
Empirical results on multi-task and meta reinforcement learning, such as [Sarafian et al. (2021)](http://proceedings.mlr.press/v139/sarafian21a.html) and [Beck et al. (2022)](https://proceedings.mlr.press/v205/beck23a.html) (See Section 6 in our paper for more references), also show that conditioning the policy on task context through HN performs better than concatenation. 
These evidences from previous work motivate us to use HN instead of feature concatenation to better model morphology-policy dependence.
