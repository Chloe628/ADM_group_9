# ADM_group_9
1.	DATA: The goal of the first exercise was to create a graph G, by applying the graph methodologies. After we brought up the full dblp json file, we decoded json data importing json and defining json.loads(data) as dataset. 

Having the dataset, we created a dictionary, using 2 for loop: one for dic in range(len(dataset)), one for j in range(len(dataset[dic]['authors'])). 
In this dictionary, we have as keys the authors ID, and for values a list of publications’ ID that each author wrote, as well as the conference’s ID in which the publication has been presented. The output has struct {authorID: [list of {confID:pubID}]}.

After that, we defined the Jaccard’s Similarity function. We needed this function to weigh each edge of the graph. In fact, the graph’s nodes are the authors, while the nodes are connected if they share, at least, one publication.
For the jaccardSim we created 2 empty lists, in which we appended the keys. We calculated the length of the intersection between the two lists and as result we put  1 - (intersect / ((len(myList1) + len(myList2)) - intersect)).

   
Importing networkx, we create the graph G. At first, using 3 for loops, and adding the nodes before weighing the edges. We have weighed each edge with the jaccardSim.
After that, we also printed the graph's info:  print(nx.info(G))
 
At the end, importing matplotlib and networkx, we print the graph.

2.	STATISTICS & VISUALIZATIONS
a)	At first, we create a dictionary of struct {conference_id: [list of authors who participated in that conference]}, to have a clear visualization of each conference’s ID and the authors’ ID of who have participated in each conference. 
#a dictionary of struct {conference_id: [list of authors who participated in that conference]}
Conferences = {}
for book in dataset:
    confID = book['id_conference_int']
    for author in book['authors']:
        authorID = author['author_id']
        if confID not in Conferences.keys():
            Conferences[confID] = []
        else:
            Conferences[confID].append(authorID)

Choosing the conference in input, we then create a list of nodes, which are the authors in the input conference. 
#input
searchconfID = input("Search confID: ")

myset = searchconfID.split()

nodeList = []
for i in myset:
    for k,v in myDict.items():
        for j in range(len(v)):
            if(list(v[j].values())[0]==confID):
                nodeList.append(k)


Defining H the graph and importing matplotlib.pyplot, we returned the subgraph induced by the set of authors who published at the input conference. 

H = G.subgraph(nodeList)
import matplotlib.pyplot as plt
plt.clf()
nx.draw(H)
plt.show()

For what concern the centralities measures, we used the Python package networkx. It allowed us to calculate degree centrality, closeness centrality and betweenness centrality.
Besides, for the measures' plots, we imported matlotlib plotting library, and in particular,ticker's module contains classes to support completely configurable tick locating and formatting. We then used the FuncFormatter function, which sets the labels.
import networkx as nx
#degree centrality and its plot:
degree_centrality = nx.algorithms.centrality.degree_centrality(H)
degree_centrality

degree_dict={}
for key, values in degree_centrality.items():
    if values not in degree_dict.keys():        
        degree_dict[values]=1
    else:
        degree_dict[values]+=1
 
from matplotlib.ticker import FuncFormatter
import numpy as np
x = np.arange(len(degree_dict))
y = [i for i in degree_dict.values()]
plt.bar(x, y)
plt.xticks(x, sorted(("%.4f" % a for a in degree_dict.keys())))
plt.show()

#closeness centrality and its plot:
closeness_centrality = nx.algorithms.centrality.closeness_centrality(H)
closeness_centrality

closeness_dict={}
for key, values in closeness_centrality.items():
    if values not in closeness_dict.keys():        
        closeness_dict[values]=1
    else:
        closeness_dict[values]+=1 

from matplotlib.ticker import FuncFormatter
import numpy as np
x = np.arange(len(closeness_dict))
y = [i for i in closeness_dict.values()]
plt.bar(x, y)
plt.xticks(x, sorted(("%.3f" % a for a in closeness_dict.keys())))
plt.show()

#betweenness centrality and its plot:
betweenness_centrality = nx.algorithms.centrality.betweenness_centrality(H)
betweenness_centrality

betweenness_dict={}
for key, values in betweenness_centrality.items():
    if values not in betweenness_dict.keys():        
        betweenness_dict[values]=1
    else:
        betweenness_dict[values]+=1

x = np.arange(len(betweenness_dict))
y = [i for i in betweenness_dict.values()]
plt.bar(x, y)
plt.xticks(x, sorted(("%.4f" % a for a in betweenness_dict.keys())))
plt.show()

b) 
