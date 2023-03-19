MetaMorph concatenates the morphology context features $c^i$ with state features $s^i_t$ as the input to node $i$, so the node embedding is computed as $e^i = W \left[ s^i_t; c^i \right] + b = W_s s^i_t + W_c c^i + b$, where $W_s$ and $W_c$ are the sub-matrices that encode state and context features respectively.
As $c^i$ is fixed, this is equivalent to adding a context-conditioned bias $W_c c^i$ to $e^i$. 

As the reviewer suggested, this additional bias term could in principle enable further computation to condition on the morphology. 
However, empirically it may not be the optimal way to do so. 
Previous work, e.g. [Galanti and Wolf (2020)](https://arxiv.org/pdf/2002.10006.pdf) and [Beck et al. (2022)](https://proceedings.mlr.press/v205/beck23a.html), has shown that hypernetwork (HN) can better model context conditioning than concatenation, which motivates us to use HN to better model morphology-policy dependence.
