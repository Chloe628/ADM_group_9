# ADM_group_9

This is the repository for Homework 4 of Algorithmic Methods for Data Mining - Group 9


#### From the root folder run:

```
python3 module.py
```

It is possible to choose between:


* "reduced" or "full" database; 


Then you can also select the excercise to be performed using the following options:


* 2a, 2b, 3a or 3b.


Each choise is related with the two exercises (part one and part two for both of them). for each one, according with the task of the exercise, you have different arguments explained in detail below. Let's go on details about each exercise.


## Exercise 2) - statistics and visualizations.

### 2a)

Since the task is to have the subgraph induced by the set of authors who published at least once in a given conference, as first output is given a list of the conference ID from which you can choose the one you prefer. 
After putting as input the ID conference, you'll receive as first output the plot of the subgraph; after closing this first figure, the program will show the histograms related to the centralities measures in the following order: degree, closeness and betweeness centralities.


### 2b)

Given an author ID as input we'll give as a result the subgraph of the nodes which have at most distance equal to a certain level, that we'll call "d". In order to provide our result, at first, you have to choise the author ID and secondly the maximum hop distance (equal to "d") that you want to check.  We used the ego_graph function belonging to the networkx library to calculate this subgraph. 




## Exercise 3) - some generalized version of the Erdos number.










