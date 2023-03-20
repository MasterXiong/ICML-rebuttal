SWAT incorporate morphology context into the controller via positional encoding (PE) and relational encoding (RE).   

For PE, SWAT actually solves a uniqueness issue, as using a single tree traversal method to index the nodes cannot uniquely reconstruct the original tree. 
SWAT solves it by using multiple tree traversal methods to avoid ambiguity. 
However, SWAT PE also can't solve the consistency issue we discussed in Appendix C.1, because SWAT is also sensitive to how we determine the order of a node's children nodes, and the nodes that play different roles in different robots may still have the same PE index (although this may happen less frequently because the PE index has more dimensions in SWAT). 
Empirically, SWAT is developed in a codebase different from MetaMorph and evaluated on a different benchmark, so we cannot directly compare with the results in the SWAT paper. 
Instead, we tried to reproduce SWAT PE in our codebase, and found it to be not helpful, possibly because the much larger number of robots used in the UNIMAL benchmark amplifies SWAT PE's inconsistency issue.

For RE, the key difference between RE and our method is that our method computes fixed attention weights conditioned on morphlogy context *alone*, while SWAT first computes dynamic attention weights based on node embedding, then adds RE as an additional term to adjust the attention map. 
Empirically, the ablation in SWAT paper shows that using RE alone only provides a little performance gain. We also tried to reproduce RE in our codebase by adding it to MetaMorph, but found that there is little difference in training performance. 
In contrast, the fixed attention module in our method significantly improves learning performance, possibly due to the more proper inductive bias of conditioning the attention map on morphology alone. 
