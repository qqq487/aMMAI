# **[Paper Reading]** A survey on Image Data Augmentation for Deep Learning

Shorten, C., Khoshgoftaar, T.M.

## Problem Definition
To avoid or reduce overfitting due to limited data.

## Contribution
    List a lot of common data augmentation techniques with pros and cons.
## Method

### Data Augmentations based on basic image manipulations
* Geometric transformations
    * Flipping: 
        * easy to implement
        * Flipping by horizontal axis is more common than by vertical axis.
        * not label-preserving
        * not suitable for text recognition. 
    
    * Color space:
        * Isolating a single color channel such as R, G , or B (adding 2 zero matrices from the other color channels.).
        * Changing the intensity values in these color histograms.
    
    * Cropping: 
        * Cropping the center area of images with mixed height and width.
        * Random crop.
        * Usually not label-preserving, depending on reduction threshold.
        
    * Rotation:
        * Rotate the image right or left on an axis between 1 and 359 degree.
        * when rotation degree larger than ±20 usually not label-preserving.
    
    * Translation:
        * Avoid positional bias in the data by shifting images (left, right,  up, or down), and remaining space can be filled with constant value or Gaussian noise.
    
    * Noise injection:
        * Add Gaussian noise to images.
        * Help CNNs learn more robust features.
    
### Geometric versus photometric transformations
* Kernel filter:
    * Sharpening: 
        * more details to learn.
    * Blurring: 
        * resistance to motion blur.
    * PatchShuffle Regularization: 
    ![](https://i.imgur.com/mBGULKI.png) 

* Mixing images:
    * SamplePairing augmentation strategy: Generate a new images by picking two images randomly and averaging intensity of each channel (labels is the same as the first-pick image).
    * Non-linearly mixing images:
    ![](https://i.imgur.com/tNTmQjb.png)
    * Mixing images through random image cropping and patching: Random cropping images and then mix them up.

* Random erasing:
    * Randomly selecting patchs of an image and masking it with 0, 255, mean pixel values, or random values.
    * Random values is the best.
* A note on combining augmentations
    Combining augmentations may cause further overfitting if the dataset is very small.


### Data Augmentations based on Deep Learning
* Feature space augmentation:
    * synthetic minority over-sampling technique (SMOTE)
    * data-space augmentations usually better than feature-space augmentations
* Adversarial training
    * Fast gradient sign method: missleading the classfication
* GAN‑based Data Augmentation
    * DCGANs
    * Progressive Growing GANs: growing of resolution.
    * Conditional GANs: to solve model collapse, add conditional vector in both generator and discriminator.
    * CycleGANs: image to image (horse to zebra).
* Neural Style Transfer
* Meta learning Data Augmentations
    * Neural augmentation
        * fast style transfer: change loss function from per-pixel to perceotual.
    * Smart Augmentation
    * AutoAugment: RL + RNN

### Design considerations for image Data Augmentation
* Test-time augmentation: 
    * aiming at improving accuracy, but costly. (maybe it can be used in med images)
* Curriculum learning: 
    * Find a strategy to select training data, not randomly.
* Resolution impact: 
    * various of resolution, like downsample and up sample.
* Final dataset size: 
    * storing problem
* Alleviating class imbalance with Data Augmentation: 
    * if the dataset is imbalance, using simple random oversampling may cause overfitting, try adversarial training, neural style transfer, GANs, and meta-learning.
