# **[Paper Reading]** Adaptive Subspaces for Few-Shot Learning

Christian Simon, Piotr Koniusz, Richard Nock, Mehrtash Harandi

CVPR 2020

## Contribution
* Provide a framework for few-shot learning by introducing dynamic classifiers that are constructed from few samples. A subspace method is exploited as the central block of a dynamic classifier. 
* Develop a discriminative form which can boost the accuracy.

## Method

#### Subspaces for Few-Shot Classification
* We propose to model points by subspaces {Zi}, i = 1 -> N. Each subspace Zi has a basis represented by R. 
* Our goal is to learn the feature extractor Θ to generate subspaces
     * the function in a way that the resulting space is suitable for subspace classifiers.
* Our goal is to assess whether the concept of subspace modeling for few-shot learning is well justified, thus we opt for truncated SVD in our implementation.
#### Subspace Classifiers
* High-order information is preferred than low-order to improve the capability of the classifier, and a subspace method can form a robust classifier
* Our general subspace classifier is defined as:
    * ![](https://i.imgur.com/hP5NyNZ.png)
    * Pc is a truncated matrix of a matrix Bc with orthogonal basis for the linear subspace.
 * We define the probability of the query assigned to class c using a softmax function as:
     * ![](https://i.imgur.com/dKewYO8.png)


#### Discriminative Deep Subspace Networks
* ![](https://i.imgur.com/OtoAXSm.png)

* The goal is to enhance DSN by learning representations that lead to more discriminative subspaces 
    * make use of the Grassmannian geometry
    * propose to maximize the distance between subspaces during training.
    * ![](https://i.imgur.com/ub9Gvfa.png)



#### DSN for Semi-Supervised Few-Shot Learning
* To address semi-supervised few-shot learning, we need to take advantage of the unlabeled data to fit better subspaces to our data by refining the center of each class according to:
    * ![](https://i.imgur.com/ULwgNrS.png)
    * ![](https://i.imgur.com/tAqBzbk.png)
    * mi is the soft-assignment score for unlabeled samples
    * To work at the presence of distractors, we use a fake class with zero mean.

## Experiments

#### Few-shot Learning
* 5-way few-shot classification results on tiered-ImageNet with 95% confidence intervals
    * ![](https://i.imgur.com/A156w9j.png)
* 5-way few-shot classification results on the CIFAR-FS dataset using ResNet-12 with 95% confidence intervals.
    * ![](https://i.imgur.com/2LfH1Yk.png)
* Few-shot classification results using Conv-4 on the Open MIC dataset for 5-way 1-shot and 3-shot.
    * ![](https://i.imgur.com/c3OSdR1.png)




#### Semi-Supervised Few-shot Learning
* 5-way semi-supervised few-shot classification results using Conv-4 on mini-ImageNet and tiered-ImageNet with 40% and 10% labeled data, respectively. We show the classification results with (w/ D) and without distractors(w/o D).
    * ![](https://i.imgur.com/ZmMxQje.png)




## Discussion
* Robustness to Perturbations
    * some noise patterns might not be obvious when collecting the data.Thus, the data cannot be guaranteed to be free from noise.
    * ![](https://i.imgur.com/15gFFmO.png)


* Computational 
    * Compared to the complexity of the prototypical networks approach, our method is somewhat slower due to the use of the SVD step. However, to address the complexity of SVD, fast approximate SVD algorithms can be used.


## Conclusion
* This paper presents the DSN, a novel few-shot learning approach that employs a few-shot learning model via affine subspaces.
* The subspace model is proven to improve existing models by a large margin due to its nature to represent a few datapoints on a subspace.
* We showedthat DSN is robust to noise in few-shot learning.
###### tags: `ammai`
