# Designing an ML System
There's a plethora of resources out there that provides information about how different machine learning models work. However, there's not may resources that show you how to approach designing ML systems that try to solve complex large scale problems.

This project tries to bridge that gap. 


## 1. Set up the problem
Usually, the problem at hand is generally very broad. The first thing you wan't to do is ask questions. Why?
- To bridge the gap between your understanding of the questions and the expectations of the interviewer. 
- Narrow down your problem space
- Chalk out system requirements
- Arrive at a precise problem statement

#### Example 1
You want to design a search engine that displays the most relevant results in response to user queries.
Questions you may want to ask are:
    - Is it a general search engine (Google) or a specialized search engine (Amazon product search)?
    - What kind of queries is it expected to answer?
    
From the findings, you can then define a precise problem statement as follows:
> Build an ML model that allows a generic search engine to return relevant results for queries like "Elon Musk", "Prog Languages" etc.

## 2.  Understand scale and latency requirements
Conversations around performance, and capacity considerations will allow you to clearly understand the scale of the system and its requirments. 

#### Example – A feed-based system
**The problem:** Given a list of tweets, train an ML model that predicts the probability of engagement of tweets and orders them based on that score.

- **Latency Requirements:** Do you want to return the relevant tweets in 100 milliseconds or 500 ms? Knowing that you need to return results quickly will inform the depth and complexity of your models.
- **Scale of the data:** How many tweets would we have to rank according to relevance for a user at a time? Having huge amounts of data will inform you to design the system with scalability in mind.

> Knowing scale and latency requirements will influence how scalable and complex your models will be. 

## 3. Defining Metrics
Metrics will help you to figure out if the system is performing well.
Think of them as criteria for measuring success. 

It's important to discuss metrics early in our design discussions because it helps in understanding the problem and in selecting key architectural components.

### Metrics for offline testing
Offline metrics tests model performance during the development stage. Examples of metrics for binary classification are:
- AUC
- Log Loss
- Precision
- Recall
- F1-Score

You might have to come up with specific metrics for certain problems.
For example, the performance of a search ranking ML model can be measured using NDCG metric (A measure of ranking quality). 

> The metric will help you select the best perfoming models.

### Metrics for online testing
Once we've selected the best performing models offline, we need to test them in a production environment. 

The deployment of the new model will depend on its performance in an online test. 

- **Component-wise metric:** This will measure the performance of the model online.
- **End-to-end metric:** This will test how well the system is performing with the new model plugged in. Here, user engagement and retention rates are good metrics to use.

#### Example: A model that affects another component.
If the component you are designing is going to improve an existing component, you'll have component-wise metrics to evaluate the performance of the model individually. You'll also have to come up with performance metrics for the component that is being affected.

## 4. Architectural Discussion
The next steps is to think about the compoments of the system and how the data will flow through them.

#### Example: A search ranking model
Here's how data will flow through the system components:
1. We'll start with a searcher making a query on the search engine.
2. The query normalizer rewrites and corrects mispelled words ("resturat near me" --> "restaurants near me").
3. The query understanding component helps identify the intent of the query (e.g local intent).
4. Then, the document selector selects relevant documents from billions of web docs.
5 Next, the ranker component ranks the results according to their relevance.
6 Finally, the results are displayed on the search engine result page.

### Architecting for scale
Let's say you are building an ML system that displays relevant ads to users. During the setup, you realize that the number of users and ads in the system are ever-increasing. 

You'll need a scalable system that quickly finds relevant ads for all users despite the increase in ads data.

Here, we can use a funnel approach: Each stage has fewer ads to process. Then, complex models that produce relevant ads can be utilized downstream.

![](images/funnel_approach.svg)