# **[Paper Reading]** Neural Architecture Search: A Survey

Thomas Elsken, Jan Hendrik Metzen, Frank Hutter

JMLR ’19

## Contribution
* Categorize methods for Neural Architecture Search (NAS) according to three dimensions:  
    * search space
    * search strategy
    * performance estimation strategy:
* ![](https://i.imgur.com/kIh2kyY.png)


#### Search Space
* Defines which neural architectures a NAS approach  might discover inprinciple.  
* A relatively simple search space is the space ofchain-structured neural networks:
    * ![](https://i.imgur.com/1k5NI4l.png)
* The final architecture is then built by stacking these cells in a predefined manner:
    * ![](https://i.imgur.com/RIld7Zf.png)

* Three major advantages:
    1. The size of the search space is drastically reduced since cells usually consist of significantly less layers than whole architectures.
    2. Architectures built from cells can more easily be transferred or adapted to other datasets by simply varying the number of cells and filters used within a model. 
    3. Creating architectures by repeating building blocks has proven a useful design principle  in  general

#### Search Strategy
* Many different search strategies can be used to explore the space of neural architectures, including:
    * random search
    * Bayesian optimization
        * add kernel function
        * tree structure model
        * Monte Carlo Tree Search 
    * evolutionary methods
        * Using evolutionary algorithms for optimizing.
    * reinforcement learn-ing (RL)
        * agent's action => neural architecture
        * action space => search space
        * reward => model perfoemance
    * gradient-based methods
        * Focus on optimizing layer hyperparameters or connectivity patterns

#### Performance Estimation Strategy
* Performance can be estimated based on lower fidelities of the actual performance after full training
    * ![](https://i.imgur.com/ONBpR0R.png)
* One-Shot  Architecture  Search:
    *  treats all architectures as different sub-graphs of a supergraph (the one-shot model) and shares weights between architectures that have edges of this supergraph in common
    *  Only the weights of a single one-shot model need to be trained (in one of various ways),and architectures (which are just subgraphs of the one-shot model) can then be evaluated without any separate training by inheriting trained weights from the one-shot model. 

#### Future Directions
* Go beyond image classification problems by applying NAS to less explored domains.
* Develop methods for multi-task problems and for multi-objective problems.
* defining  more  general  and  flexible  search  spaces
* evaluate NAS methods not in isolation but as part of a full open-source AutoML system, where also hyperparameters and data augmentation pipeline are optimized along with NAS.


###### tags: `ammai`
