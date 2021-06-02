# **[Paper Reading]** Fast and Furious: Real Time End-to-End 3D Detection, Tracking and Motion Forecasting with a Single Convolutional Net

Wenjie Luo, Bin Yang and Raquel Urtasun

CVPR 2018

## Contribution
* Propose a novel deep neural network that is able to jointly reason about 3D detection, tracking and motion forecasting given data captured by a 3D sensor.

## Method

#### Data Parameterization
* Voxel Representation
    1. Quantize the 3D world to form a 3D voxel grid to get a representation where convolutions can be easily applied
    2. Assign a binary indicator for each voxel encoding whether the voxel is occupied
    3. Using 2D convolutions and treat the height dimension as the channel dimension because 3D convolutions on our single frame representation as this operation will waste most computation since the grid is very sparse
    
* Adding Temporal Information
    1. Take all the 3D points from the past n frames and perform a change of coordinates to represent then in the current vehicle coordinate system.
    2. Compute the voxel representation for each frame. 
    * ![](https://i.imgur.com/kDcRtCN.png)
#### Model Formulation
* Two different ways to exploit the temporal dimension on 4D tensor:
    * Early Fusion
        * It might lack the ability to capture complex temporal features as this is equivalent to producing a single point cloud from all frames, but weighting the contribution of the different timestamps differently.
    * Late Fusion
        * Using multiple predefined boxes allows us to reduce the variance of regression target, thus makes the network easy to train.
        *  do not use predefined heading angles. Fur- thermore we use both sin and cos values to avoid the 180 degrees ambiguity.
    * ![](https://i.imgur.com/zfx7IYl.png)

* Decoding Tracklets
    * At each timestamp, the model outputs the detection bounding boxes for n timestamps. Reversely, each timestamp will have current detections as well as n − 1 past predictions.
    * we can aggregate the information for the past to produce accurate tracklets without solving any trajectory based optimization problem.
#### Loss Function and Training
* Minimize a combination of classification and regression loss include both the current frame as well as our n frames forecasting into the future.
    * ![](https://i.imgur.com/C81LJaY.png)
* Classification loss binary cross-entropy computed over all locations and predefined boxes
    * ![](https://i.imgur.com/0jFiELz.png)
* Define the regression targets as
    * ![](https://i.imgur.com/ypGZXbB.png)
* Use a weighted smooth L1
    * ![](https://i.imgur.com/8GGhk9m.png)

* Using hard data mining due to the imbalance of positive and negative samples.
## Experimental Evaluation
* Dataset
    * 546,658 frames collected from 2762 different scenes. 

* Detection Results
    * ![](https://i.imgur.com/ZnIewTb.png)
    * ![](https://i.imgur.com/i3IbZiG.png)
    * ![](https://i.imgur.com/QvSEUZw.png)


* Tracking performances
    * ![](https://i.imgur.com/axx6MHq.png)

* Motion Forecasting
    * ![](https://i.imgur.com/jQK6Ycq.png)

* Qualitative Results
    * ![](https://i.imgur.com/4hHzDzJ.png)

## Conclusion
* Proposed a holistic model that reasons jointly about detection, prediction and tracking in the scenario of autonomous driving.

###### tags: `ammai`
