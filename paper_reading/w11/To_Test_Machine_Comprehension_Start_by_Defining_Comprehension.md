# **[Paper Reading]** To Test Machine Comprehension, Start by Defining Comprehension

Jesse Dunietz et al.

ACL 2020

## Contribution
* Redefine the Machine Reading Comprehension (MRC) task
* Present a TEMPLATE OF UNDERSTANDING for a  widely useful class of texts, namely short narratives.

## Existing MRC dataset designs and problems

#### Manually written questions
* Most of them can be answered using lexical cues, and  it makes the tasks questionable measures of comprehension.
#### Naturally occurring questions
* Useful for answering common queries, but not for comprehension.
* Common queries are less thorough than annotators at probing important elements of understanding.

#### Questions from tests designed for humans
* Tests designed for humans rarely bother to test content that most humans find obvious (which is important for comprehension).

#### Automatically generated questions
* Answering Cloze-style questions != comprehension
* Multi-hop questions are not a sufficiently well-motivated body of content to constitute a measure of reading comprehension.

## Defining deep story understanding

#### The case for stories
* Stories have several convenient properties:
    * Humans tend to think and communicatein terms of stories
    * Stories come with a strong prior from cognitive science about what elements of understanding will be useful. 
    * A story entails a highly structured network of relations. Thus, stories do exercise abilities beyond simple factoid extraction. 
    * Stories rely on a large body of implicit world knowledge. 

#### A ToU for stories
1. Spatial: 
    * Where are entities positioned overtime, relative to landmarks and each other
    * Where do events take place
2. Temporal:
    * What events and sub-events occur,and in what order
    * for what blocks of that timeline do entities’ states hold true
3. Causal
    * How do events and states lead mechanistically to the events and states describedor implied by the text
4. Motivational
    * How  do  agents’ beliefs, desires, and emotions lead to their actions

#### Towards a story understanding task
* Annotating ToU answers
    * Annotator generate ToU and corresponding questions by Spatial, Temporal, Causal and Motivational.
* Competing to satisfy judges
    * Human scoring
* ![](https://i.imgur.com/l8QPhzV.png)
* ![](https://i.imgur.com/vd0rGKf.png)



## EXPERIMENTS

* ![](https://i.imgur.com/18edm8V.png)


## Conclusion
* The experiment results shows that the existing methods have pretty bad performance, what the model learned does not seem to be an understanding of the content.
###### tags: `ammai`
