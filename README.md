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

