# **[Paper Reading]** Graph Embedding and Extensions: A General Framework for Dimensionality Reduction

Yan, Shuicheng, et al. 

IEEE Transactions on Pattern Analysis & Machine Intelligence 1 (2007): 40–51.

## Poblem Definition
The graph embedding framework can be used as a general platform for developing new dimensionality reduction algorithms. 

## Contribution

* Propose a general framework for dimensionality reduction by using graph embedding.
* Marginal Fisher Analysis: 
    * a new supervised dimensionality reduction algorithm.


## Method

#### Graph Embedding
* Linearization: 
    * linear projection: y = X<sup>T</sup>w
    * objective function: ![](https://i.imgur.com/NYKw1ak.png)

* Kernelization
    *  to map the data from the original input space to another higher dimensional Hilbert space.
    *  objective function: ![](https://i.imgur.com/w25fYqJ.png)

* Tensorization
    * to conduct dimensionality reduction with vertices encoded as general tensors of an arbitrary order.
    * objective function:![](https://i.imgur.com/oWPDjmx.png)


#### General Framework for Dimensionality Reduction
* ![](https://i.imgur.com/kynxo9t.png)

* ![](https://i.imgur.com/wq9ReED.png)

#### Related Works and Discussions
* Kernel Interpretation and Out-of-Sample Extension
* Brand’s Work
* Laplacian Eigenmap and LPP

#### Marginal Fisher Analysis
1. PCA projection:
    * project the data set into the PCA subspace by retaining N - N<sub>c</sub> dimensions or acertain energy.
2. Constructing the intra-class compactness and inter-class separability graphs.
3. Marginal Fisher Criterion.
    * ![](https://i.imgur.com/jQ01k6M.png)
4. Output the final linear projection direction
    * ![](https://i.imgur.com/9EsDRLk.png)

#### Kernel Marginal Fisher Analysis
* Marginal Fisher Analysis can be further improved by using the kernel trick.
    * projection direction: ![](https://i.imgur.com/Jp3P048.png)
    * optimal α: ![](https://i.imgur.com/icxPdBD.png)
    * distance: ![](https://i.imgur.com/Rqoa6QQ.png)

#### Tensor Marginal Fisher Analysis
* ![](https://i.imgur.com/ViKcL7H.png)

## EXPERIMENTS
* ![](https://i.imgur.com/mJs1Vns.png)
* ![](https://i.imgur.com/5zAAUPF.png)
* ![](https://i.imgur.com/qvOCimL.png)
* ![](https://i.imgur.com/R9n1zFQ.png)


## Conclusion
* A general framework known as graph embedding, along with its linearization, kernelization, and tensorization, has been proposed to provide a unified perspective for the under-standing and comparison of many popular dimensionality reduction algorithms.
* Proposed a novel dimensionality reduction algorithm called Marginal Fisher Analysis by designing two graphs that characterize the intra-class compactness and the inter-class separability, respectively, and by optimizing their corresponding criteria based on the graph embedding framework.

###### tags: `ammai`