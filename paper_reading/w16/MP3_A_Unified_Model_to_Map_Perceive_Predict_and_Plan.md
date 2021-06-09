# **[Paper Reading]** MP3: A Unified Model to Map, Perceive, Predict and Plan

Ren et al.

CVPR 2021.

## Contribution
* Significantly safer, more comfortable, and can follow commands better than the baselines in challenging long-termclosed-loop simulations, as well as when compared to anexpert driver in a large-scale real-world dataset.

* Mapless, Interpretable for self-driving

#### Why mapless driving
* HD maps has proven hard toscale due to the complexity and cost of generating the mapsand maintaining them.
* Heavy reliance onHD maps introduces very demanding requirements for thelocalization system, which needs to work at all times withcentimeter-level accuracy or else unsafe situations

## Method

* ![](https://i.imgur.com/uZnNb8y.png)

### Interpretable Mapless Driving

#### Extracting Geometric and Semantic Features
* Our model exploits a history of LiDAR point clouds to extract rich geometric and semantic features from the scene over time.

#### Interpretable Scene Representations
* Online map representation:
    * ![](https://i.imgur.com/Ugn46FG.png)

    1. **Drivable area**: Drivable area: Road surface (or pavement) where vehiclesare allowed to drive, bounded by the curb.
    2. **Reachable lanes**: We define the reach-able lanes as the subset of motion paths the SDV can getto without breaking any traffic rules.
    3. **Intersection**: Drivable area portion where traffic is con-trolled via traffic lights or traffic signs. Reasoning aboutthis is important to handle stop/yield signs and traffic lights.

* Dynamic occupancy field:
    * ![](https://i.imgur.com/wxhnJTR.png)
    1. **Initial Occupancy**: a BEV grid cell is active (occupied)if its center falls in the interior of a polygon given by anobject shape and its current pose.
    2. **Temporal Motion Field**:  defined for the occupied pixelsat a particular time into the future.  Each occupied pixelmotion is represented with a 2D BEV velocity vector

* Probabilistic Model:
    * The probability of occupancy flowing from location i1 to location i2 between two consecutive time steps t and t + 1
        * ![](https://i.imgur.com/hmGWG63.png)

    * Compute the probability that no occupancy flow event occurs, and take its complement
        * ![](https://i.imgur.com/MJBKJxP.png)


#### Motion Planning
* Trajectory Sampling
    * We use retrieval from a large-scale dataset of real trajectories. 
        * This approach provides a large set of trajectories from expert demonstrations while avoiding random sampling or arbitrary choices of acceleration/steering profiles 

* Route Prediction
    * To simulate GPS errors, we randomly sample noise from a zero-mean Gaussian with 5m standard deviation. We model the route as a collection of Bernoulli random variables, one for each grid cell in BEV
* Trajectory Scoring
    1. Routing and Driving on Roads
        * ![](https://i.imgur.com/LiIz2aT.png)
    2. Safety
        * We penalize trajectories where the SDV overlapsoccupied regions 
    3. Comfort
        * Penalize jerk, lateral acceleration, cur-vature and its rate of change to promote comfortable driving.

## Experimental Evaluation
* Closed-loop simulation results
    * ![](https://i.imgur.com/61aka8u.png)
* Large-scale evaluation against expert demonstrations
    * ![](https://i.imgur.com/N92uDYJ.png)
* Qualitative results
    * ![](https://i.imgur.com/WfdEZ9Z.png)

## Conclusion
* This paper proposed an end-to-end model for **mapless driving**
* Produces probabilistic intermediate representations that are interpretable andready-to-use as cost functions in our neural motion planner.
* when evaluating the model in a closed-loop simulator without any additionaltraining, it is far more robust than the baselines, achievingvery significant improvements across all metrics.


###### tags: `ammai`
