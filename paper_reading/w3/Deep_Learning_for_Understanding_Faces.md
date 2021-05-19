# **[Paper Reading]** Deep Learning for Understanding Faces

Rajeev Ranjan, Swami Sankaranarayanan, Ankan Bansal, Navaneeth Bodla, Jun-Cheng Chen, Vishal M. Patel, Carlos D. Castillo, and Rama Chellappa

## Introduction
Introduces some deep learning methods in automatic face recognition.

Three parts:
1. Locating faces by face detection.
2. Using key-point detection to locate some crucial face key-points ( eye centers, nose tip, etc. ).
3. Extracting some sufficient identifiable information by using feature description.
## Contribution and Discussion

1. Contribution
    * List a lot of deep learning methods on face detection, identification and verification with their pros and cons.

2. Challenges
    * Face detection: The wide range of variations in the appearance of faces ( color, angle, lightness ).
    * Fiducial detection: Need more data.
    * Face identification/verification: Limited by the memory. 



## Method

#### Face Detection
1. Region based:
    1. Using object proposal generators like Selective Search to generate some proposal (2000 per image).
    2. Then using models like DCNN to classify whether a given proposal contains a face or not.
    ![](https://i.imgur.com/Ba9tkPJ.png)

2. Sliding-window based
    1. computes a face detection score and bounding-box coordinates at every location in a feature map at a given scale. (**faster** than region based)
    2. Detections at different scales are carried out by creating an image pyramid at multiple scales.
    ![](https://i.imgur.com/z0ifsUe.png)

3. Single-shot detector
    1. A sliding-window-based detector, using the inbuilt pyramid structure  present in DCNNs.  
    2. Because the detections are obtained in a single forward pass of the  network, the overall computation time of SSD is lower than faster R-CNN.

#### Key-point detection
1. Model based
    * AAM, ASM, and CLM, learn a shape model during training and use it to fit new faces aduring  testing. 
    

2. Cascaded regression based
    * learning a model that directly maps the image appearance to the target output.
    ![](https://i.imgur.com/qWKeGSF.png)

#### Face identification and verification
* Robust feature learning for faces using deep learning
    * DeepFace, DeepID, FaceNet, etc.
* Discriminative metric learning for faces
    * Learning a classifier or a similarity measure from data is a key component for improving the performance. 
* Implementation
    * Subdivide into two tasks:
        1. face verification 
        2. face identification.
* Training data sets for face recognition
* ![](https://i.imgur.com/95TWZRU.png)
