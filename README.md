# ER Network
<p align="center">
 <img src="https://github.com/DrAliSeif/2D_visualization_network/blob/main/ER%20Network/plot.png?raw=true" >
 </p>
 
# FC Network

<p align="center">
 <img src="https://github.com/DrAliSeif/2D_visualization_network/blob/main/Fully%20Connected%20Network/plot.png?raw=true" >
 </p>

# SF Network


<p align="center">
 <img src="https://github.com/DrAliSeif/2D_visualization_network/blob/main/SF%20Network/plot.png?raw=true" >
 </p>
 
# SW Network
<p align="center">
 <img src="https://github.com/DrAliSeif/2D_visualization_network/blob/main/SW%20Network/plot.png?raw=true" >
 </p>
 


# 2D visualization network
## two-dimensional visualization of the structure of a network (Directional and without direction)


I will be using NetworkX Python (2.4) library along with Matplotlib (3.2.2). (Updated on 01.06.2020)
First, we are defining a simple method to draw the graph and the centrality metrics of nodes with a heat map.
Zachary’s Karate Club graph is defined as the example graph G. It is basically a social network of members of an university karate club, where undirected edges connects people who interact outside the club.
We also need a directed graph to demonstrate some other centrality measures. Here we are defining the toy directed graph DiG which is given as an example in wikipedia.


<p align="center">
 <img src="https://github.com/aliseif321/2D_visualization_network/blob/main/2D_Network/Picture/matrix.png?raw=true" >
 </p>
 
 
 <p align="center">
 <img src="https://github.com/aliseif321/2D_visualization_network/blob/main/2D_Network/Picture/rand.png?raw=true" >
 </p>
 
 
 
 <p align="center">
 <img src="https://github.com/aliseif321/2D_visualization_network/blob/main/2D_Network/Picture/dir.png?raw=true" >
 </p>
 
# Code


```sh
#/************************************************************************************************/
#/*** Topic: 2D_visualization_network                                                          ***/
#/***                                                                         Ali-Seif         ***/
#/*** Version Release 17.12 rev 11256                                                          ***/
#/*** Date: 5/30/2021                                                                          ***/
#/*** Code Python 3 in Anaconda Navigator compiler,                                            ***/
#/*** MSI: PX60 6QD/ DDR4                                                                      ***/
#/*** Run under a Intel® Core™ i7-6700HQ CPU @ 2.60GHz × 64 based processor with 16 GB RAM     ***/
#/************************************************************************************************/
import networkx as nx                                                 #import networkx library
import matplotlib.pyplot as plt                                       #import matplotlib library
def draw(G, pos, measures, measure_name):                             #define function for draw network 2d
    nodes = nx.draw_networkx_nodes(G, pos, node_size=250,             #calculate node for draw
                                   cmap=plt.cm.gist_rainbow,          #
                                   node_color=list(measures.values()),#
                                   nodelist=measures.keys())          #
    labels = nx.draw_networkx_labels(G, pos,font_color='k')           #labels for nodes
    edges = nx.draw_networkx_edges(G,pos,width=0.8,edge_color='0.2')  #edges between each 2 nodes
    plt.title(measure_name)                                           #title measure_name='Degree Centrality'
    plt.colorbar(nodes)                                               #color bar
    plt.axis('off')                                                   #do not show axis and mesh
    plt.show()                                                        #show figure
textFile = open("matrix.txt")                                         #read matrix
lines = textFile.readlines()                                          #put matrix in arrey 2d
G=nx.Graph()                                                          #define G for node and connections
for i in range(18):                                                   #for loop for each column
    for j in range(18):                                               #for loop for each row
        if int(lines[i][j])==1:                                       #if connection was exist
            edge = (i, j)                                             #create edge
            G.add_edge(*edge)                                         #add edge in G
#G = nx.random_geometric_graph(10, 0.5,seed=896801)                   #create rand network(num of node,Possibility,seed rand)
pos = nx.spring_layout(G, seed=675)                                   #position of network
draw(G, pos, nx.degree_centrality(G), 'Degree Centrality')            #call draw function
```


______________________________________________

```sh
DiG = nx.DiGraph()
DiG.add_edges_from([(2, 3), (3, 2), (4, 1), (4, 2), (5, 2), (5, 4),
                    (5, 6), (6, 2), (6, 5), (7, 2), (7, 5), (8, 2),
                    (8, 5), (9, 2), (9, 5), (10, 5), (11, 5)])
dpos = {1: [0.1, 0.9], 2: [0.4, 0.8], 3: [0.8, 0.9], 4: [0.15, 0.55],
        5: [0.5,  0.5], 6: [0.8,  0.5], 7: [0.22, 0.3], 8: [0.30, 0.27],
        9: [0.38, 0.24], 10: [0.7,  0.3], 11: [0.75, 0.35]}
draw(DiG, dpos, nx.in_degree_centrality(DiG), 'DiGraph Degree Centrality')



```




<p align="center">
 <img src="https://matplotlib.org/_static/logo2_compressed.svg" width="250" height="250" >
 </p>
 

<p align="center">
 <img src="https://networkx.org/_static/networkx_logo.svg" width="300" height="70">
 </p>
 

sorce: https://aksakalli.github.io/2017/07/17/network-centrality-measures-and-their-visualization.html
