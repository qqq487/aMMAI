# **[Paper Reading]** Image Denoising Via Sparse and Redundant Representations Over Learned Dictionaries

Elad and Aharon. 

Image Processing, IEEE Transactions on Image Processing (2006) vol. 15 (12) pp. 3736 – 3745.

## Poblem Definition
Image Denoising (white and homogeneous Gaussian additive noise)

## Contribution
* Using sparse coding and dictionary to denoise.

* By using K-SVD algorithm, the dictionary describes the image content more effectively.


## Method

### From local to global bayesian reconstruction

#### Sparseland Model for Image Patches
* ![](https://i.imgur.com/I6aXZs7.png)

#### From Local Analysis to a Global Prior
* ![](https://i.imgur.com/6pkKXqr.png)

#### Numerical Solution
* ![](https://i.imgur.com/iiMPZP4.png)

### Algorithm
* ![](https://i.imgur.com/TBZfz2L.png)


## EXPERIMENTS

* Denoising Results for the DCT Dictionary
    * ![](https://i.imgur.com/2NRRtZd.png)
* Dictionary
    * ![](https://i.imgur.com/fi1H1jS.png)


## Conclusion
* This method is based on local operations and involves sparse decompositions of each image block under one fixed over-complete dictionary, and a simple average calculations.
