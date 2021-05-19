# **[Paper Reading]** Self-training with Noisy Student improves ImageNet 

Qizhe Xie and Minh-Thang Luong and Eduard Hovy and Quoc V. Le. CVPR2020

## Poblem Definition
To improve the accuracy and robustness on ImageNet classification.

## Contribution and Discussion

1. Contribution
   Shows that Noisy Student Training improves:
   * Robustness: 
        * ImageNet-A top-1 accuracy 61.0% -> 83.7%
        * ImageNet-C mean corruption error 45.7 -> 28.3
        * ImageNet-P mean flip rate 27.8 -> 12.2
   * Performances: 2% better than SOTA but reduce 90% of required data on ImageNet-A, C and P.


2. Limitation
    As the other self-training methods, it requires lots of unlabeled data. In this paper, they use the JFT dataset, which has around 300,000,000 images.
    
    Another limitation is that it needs a lot of time to train because of it has to iterative training teacher and student model. 

## Method

#### Requirement
Labeled images and **lots of** unlabeled images.

#### Step 1. Train teacher model

Train teacher model with labeled data. In this paper, they use EfficientNet-B0 as the teacher.

#### Step 2. Generate pseudo-label

After training on labeled data, now we use the teacher to generate pseudo-labels on unlabeled data. 

There are two types of pseudo-labels, soft (continous distribution) and hard (one-hot distribution). But the results shows that soft pseudo labels worl slightly better for out-of-domain unlabeled data in paticular.

#### Step 3. Self-training with noisy student

Combine labeled and unlabeled data, add some **noise**, then train an equal-or-larger student model on it.

After training, use the student as a teacher and repeat Step 3. several times.

Noise: 
1. Data augmentation: Using RandAugment.
2. Dropout: apply to the final layer with a dropout rate of 0.5.
3. Stochastic depth: 0.8 survival probability for the final layer and linear decay for other layers. 
