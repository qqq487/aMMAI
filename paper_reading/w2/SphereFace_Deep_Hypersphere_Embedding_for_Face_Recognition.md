# **[Paper Reading]** SphereFace: Deep Hypersphere Embedding for Face Recognition

Weiyang Liu, Yandong Wen, Zhiding Yu, Ming Li, Bhiksha Raj, Le Song

## Introduction

Ideal face features are expected to have smaller maximal intra-class distance than minimal inter-class distance. 

This paper propose the angular softmax loss that enables CNN to learn angularly discriminative features.

## Contribution and Discussion

1. Contribution
    * Propose a method, Angular-Softmax（A-Softmax）to better solve the open-set face recognition problem.
    
2. Why angular margin
    * Angular margin directly links to discriminativeness on a manifold,which intrinsically matches the prior that faces also lie ona manifold.
    * Incorporating angular margin to soft-max loss is actually a more natural choice

3. Comparison with existing losses
    * The existing losses only impose Euclidean margin to the learned features and the A-Softmax considers angular margin which is naturally motivated.
    * This paper's method requires no sample mining and imposes discriminative constraints to the entire mini-batches.
### Note: open-set vs closed-set
* Open-set: 
    * the identities have never shown in the training set. 
    * metric learning, intra-class distance small, iter-class distance large.
* Closed-set: 
    * the identities have overlap in the training and testing set.
    * classification
![](https://i.imgur.com/uluxGKU.png)


## Method

#### Deep Hypersphere Embedding
1. Revisiting the Softmax Loss
    * ![](https://i.imgur.com/TIXAKDk.png)

    * f<sub>j</sub> denotes the *j*-th element, *j* $\in$ [1,*K*], *K* is the class  number of the class score vector ***f***, and *N* is the number of training samples. 


2. Introducing Angular Margin to Softmax Loss
    ![](https://i.imgur.com/o8TBx8u.png)
    ![](https://i.imgur.com/PwyjrQX.png)
    * add angle metric into softmax loss, then train the model to generate decision boundaries based on the angle in the feature space.
    

3. Hypersphere Interpretation of A-Softmax Loss
   ![](https://i.imgur.com/PnaPHyA.png)

   * A-Softmax loss is equivalent to learning features that are discriminative on a hypersphere manifold, while Euclidean margin losses learn features in Euclidean space.
   * analysis shows that optimizing angles with A-Softmax loss essentially makes the learned features more discriminative on a hypersphere.

4. Properties of A-Softmax Loss
   1. With larger m,the angular margin becomes larger, the constrained regionon the manifold becomes smaller, and the corresponding learning task also becomes more difficult.
   2. (lower bound of *m*<sub>min</sub> in binary-class case).In binary-class case, we have *m*<sub>min</sub> ≥ 2+√3.
   3. (lower bound of *m*<sub>min</sub> in multi-class case).Under the assumption that *W*$_i$, ∀$_i$ are uniformly spaced in the Euclidean space, we have *m*<sub>min</sub> ≥ 3.
