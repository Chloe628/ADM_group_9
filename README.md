# ADM_group_9
1.	DATA: The goal of the first exercise was to create a graph G, by applying the graph methodologies. After we brought up the full dblp json file, we decoded json data importing json and defining json.loads(data) as dataset. 

Having the dataset, we created a dictionary, using 2 for loop: one for dic in range(len(dataset)), one for j in range(len(dataset[dic]['authors'])). 
In this dictionary, we have as keys the authors ID, and for values a list of publications ID that each author wrote, as well as the conference ID in which each publication has been presented. The output has struct {authorID: [list of {confID:pubID}]}.

After that, we defined the Jaccard’s Similarity function. We needed this function to weigh each edge of the graph. In fact, the graph’s nodes are the authors, while the nodes are connected if they share, at least, one publication. For the jaccardSim we created 2 empty lists, in which we appended the keys. We calculated the length of the intersection between the two lists and as result we put  1 - (intersect / ((len(myList1) + len(myList2)) - intersect)).
   
Importing networkx, we create the graph G. we used 3 for loops: one for data in dataset, the second for author in authors and the last one for author2 in authors. We needed 2 author's id, in order to put the condition aId != a2Id in the if, to not create edges on the same node. We defined the nodes before the if and then we have weighed each edge with the jaccardSim.
After that, we also printed the graph's info:  print(nx.info(G))
 
At the end, importing matplotlib and networkx, we print the graph.

2.	STATISTICS & VISUALIZATIONS

a)	At first, we create a dictionary of struct {conference id: [list of authors who participated in that conference]}, to have a clear visualization of each conference’s ID and the authors’ ID of who have participated in each conference. 
Choosing the conference in input searchconfID = input("Search confID: "), we then create a list of nodes, which are the authors in the input conference. 
Defining H the graph and importing matplotlib.pyplot, we returned the subgraph induced by the set of authors who published at the input conference. 
For what concern the centralities measures, we used the Python package networkx. It allowed us to calculate degree centrality, closeness centrality and betweenness centrality. 
Besides, for the measures' plots, we imported matlotlib plotting library, and in particular,ticker's module contains classes to support completely configurable tick locating and formatting. We then used the FuncFormatter function, which sets the labels.

b)	Choosing an author id and a integer, we returned an induced subgraph of neighbors centered at node (node is the author id), within a given radius (radius is the integer), using ego graph. Radius includes all neighbors of distance <= radius from the input node. So, actually radius is the hop distance we want.
Then we plotted and visualized the graph. 
