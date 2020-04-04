# Eluvio coding challenge 

## The main problems I would like to address.

* What are the topics in the news titles?
* Because news is inherently sequential and temporal, I want to know how the topic evolve over time. In other words, what happened, when and how long did it last?

## What I did.

* Preprocess the news titles for LDA model
* Determine the number of topics using topic coherence score 
* Fit LDA model for all news titles and return the topics 
* Link the topics at consecutive time based on Hellinger distance 

## Findings.

1. The best number of topics for all news titles, which achieves highest coherence socre is 14. 

2. The topics found by LDA make a lot of sense observing the returned words distribution. For example,
   - Topic: 1, Words: 0.046*"russian" + 0.026*"russia" + 0.023*"iraq" + 0.022*"putin" + 0.019*"milit" + 0.017*"forc" + 0.014*"state" + 0.013*"strike" + 0.013*"say" + 0.013*"troop" 
   
     Topic 1 should be Russian military activities in the Middle East.
     
   - Topic: 9, Words: 0.092*"kill" + 0.036*"attack" + 0.034*"bomb" + 0.023*"peopl" + 0.023*"polic" + 0.022*"dead" + 0.016*"citi" + 0.016*"suicid" + 0.013*"injur" + 0.012*"blast" 
   
     Topic 9 should be terrorist attacks.
     
3. As for the evolvement of topics, I only consider the news titles in 2016 for simplicity. This idea can also scale up to the entire dataset. The main procedure is to find the topics for each month and link similar topics for consecutive months. We say two topics are similar if the Hellinger distance between them is smaller than some pre-specified threshold. 
    - There was a topic chain lasting about 4 months, starting in February and ending in June. This topic is mainly about Syrian refugee.

    - The news topics in different months are actually quite different in terms of the word distributions. So the threshold has to be set high to construct the links. 
