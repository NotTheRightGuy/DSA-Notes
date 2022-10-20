**Dijkstra's algorithm** ([/ˈdaɪkstrəz/](https://en.wikipedia.org/wiki/Help:IPA/English "Help:IPA/English") [_DYKE-strəz_](https://en.wikipedia.org/wiki/Help:Pronunciation_respelling_key "Help:Pronunciation respelling key")) is an [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm") for finding the [shortest paths](https://en.wikipedia.org/wiki/Shortest_path_problem "Shortest path problem") between [nodes](https://en.wikipedia.org/wiki/Vertex_(graph_theory) "Vertex (graph theory)") in a [graph](https://en.wikipedia.org/wiki/Graph_(abstract_data_type) "Graph (abstract data type)"), which may represent, for example, [road networks](https://en.wikipedia.org/wiki/Road_network "Road network"). It was conceived by [computer scientist](https://en.wikipedia.org/wiki/Computer_scientist "Computer scientist") [Edsger W. Dijkstra](https://en.wikipedia.org/wiki/Edsger_W._Dijkstra "Edsger W. Dijkstra") in 1956 and published three years later.
The [[algorithm]] exists in many variants.

Dijkstra's original algorithm found the shortest path between two given nodes, but a more common variant fixes a single node as the "source" node and finds shortest paths from the source to all other nodes in the graph, producing a [shortest-path tree](https://en.wikipedia.org/wiki/Shortest-path_tree "Shortest-path tree").

For a given source node in the [[Graphs]], the algorithm finds the shortest path between that node and every other.  It can also be used for finding the shortest paths from a single node to a single destination node by stopping the algorithm once the shortest path to the destination node has been determined. For example, if the nodes of the graph represent cities and edge path costs represent driving distances between pairs of cities connected by a direct road (for simplicity, ignore red lights, stop signs, toll roads and other obstructions), Dijkstra's algorithm can be used to find the shortest route between one city and all other cities.

# Working with Dijkstra's algorithm
Let's see how it works with this graph.
![[Pasted image 20221020210758.png]]

Each segment has a travel time in minutes. We’ll use Dijkstra’s algorithm to go from start to finish in the shortest possible time.

If you ran breadth-first search on this graph, you’d get this shortest path.

![[Pasted image 20221020210829.png]]

But that path takes 7 minutes. Let's se if you can find a path that takes less time! There are four steps to Dijkstra's algorithm:
1. Find the "cheapest" node. This is the node you can get to in the least amount time.
2. Update the costs of the neighbours of this node.
3. Repeast untill you've done this for every node in the graph.
4. Calculate the final path.


Step 1: Find the cheapest node. You're standing at the start, wondering if you should go to A or B. How long does it take to get to each node?

![[Pasted image 20221020211107.png]]

It takes 6 minutes to get to node A and 2 minutes to get to node B. he rest of the nodes, you don’t know yet. Because you don’t know how long it takes to get to the inish yet, you put down ininity (you’ll see why soon). Node B is the closest node … it’s 2 minutes away

![[Pasted image 20221020211125.png]] 


Step 2: Calculate how long it takes to get to all of node B’s neighbors by following an edge from B.
![[Pasted image 20221020211210.png]]

Hey, you just found a shorter path to node A! It used to take 6 minutes to get to node A.

![[Pasted image 20221020211224.png]]
But if you go through node B, there’s a path that only takes 5 minutes

![[Pasted image 20221020211243.png]]

When you find a shorter path for a neighbor of B, update its cost. In this case, you found
- A shorter path to A (down from 6 minutes to 5 minutes)
- A shorter path to the finish (down from infinity to 7 minutes)

Step 3 : Repeat!

1. Find the node that takes the least amount of time to get to. You’re done with node B, so node A has the next smallest time estimate.
![[Pasted image 20221020211348.png]]
2. Update the costs for node A’s neighbors.
![[Pasted image 20221020211405.png]]

Woo, it takes 6 minutes to get to the inish now! You’ve run Dijkstra’s algorithm for every node (you don’t need to run it for the inish node). At this point, you know
- It takes 2 minutes to get to node B.
- It takes 5 minutes to get to node A.
- It takes 6 minutes to get to the finish.
![[Pasted image 20221020211527.png]]

Breadth-irst search wouldn’t have found this as the shortest path, because it has three segments. And there’s a way to get from the start to the inish in two segments.

![[Pasted image 20221020211547.png]]
In the last chapter, you used breadth-irst search to find the shortest path between two points. Back then, “shortest path” meant the path with the fewest segments. But in Dijkstra’s algorithm, you assign a number or weight to each segment. then Dijkstra’s algorithm finds the path with the smallest total weight.
![[Pasted image 20221020211557.png]]


# Terminology
When you work with Dijkstra's algorithm, each edge in the graph has a number associated with it. There are called weights.
![[Pasted image 20221020211715.png]]
A graph with weights is called a weighted graph. A graph without weights is called an unweighted graph.

![[Pasted image 20221020211731.png]]


To calculate the shortest path in an unweighted graph, use breadth-irst search. To calculate the shortest path in a weighted graph, use Dijkstra’s algorithm. Graphs can also have cycles. A cycle looks like this.
![[Pasted image 20221020211746.png]]
It means you can start at a node, travel around, and end up at the same node. Suppose you’re trying to ind the shortest path in this graph that has a cycle.

![[Pasted image 20221020211800.png]]

Dijkstra's Algorithm cannot work for negative weighted graph for those graph we instead uses [[Bellman-Ford Algorithm]]

Below is the implementation of Dijkstra's algorithm in C++


```cpp
// C++ program for Dijkstra's single source shortest path
// algorithm. The program is for adjacency matrix
// representation of the graph
#include <iostream>
using namespace std;
#include <limits.h>

// Number of vertices in the graph
#define V 9

// A utility function to find the vertex with minimum
// distance value, from the set of vertices not yet included
// in shortest path tree
int minDistance(int dist[], bool sptSet[])
{

	// Initialize min value
	int min = INT_MAX, min_index;

	for (int v = 0; v < V; v++)
		if (sptSet[v] == false && dist[v] <= min)
			min = dist[v], min_index = v;

	return min_index;
}

// A utility function to print the constructed distance
// array
void printSolution(int dist[])
{
	cout << "Vertex \t Distance from Source" << endl;
	for (int i = 0; i < V; i++)
		cout << i << " \t\t\t\t" << dist[i] << endl;
}

// Function that implements Dijkstra's single source
// shortest path algorithm for a graph represented using
// adjacency matrix representation
void dijkstra(int graph[V][V], int src)
{
	int dist[V]; // The output array. dist[i] will hold the
				// shortest
	// distance from src to i

	bool sptSet[V]; // sptSet[i] will be true if vertex i is
					// included in shortest
	// path tree or shortest distance from src to i is
	// finalized

	// Initialize all distances as INFINITE and stpSet[] as
	// false
	for (int i = 0; i < V; i++)
		dist[i] = INT_MAX, sptSet[i] = false;

	// Distance of source vertex from itself is always 0
	dist[src] = 0;

	// Find shortest path for all vertices
	for (int count = 0; count < V - 1; count++) {
		// Pick the minimum distance vertex from the set of
		// vertices not yet processed. u is always equal to
		// src in the first iteration.
		int u = minDistance(dist, sptSet);

		// Mark the picked vertex as processed
		sptSet[u] = true;

		// Update dist value of the adjacent vertices of the
		// picked vertex.
		for (int v = 0; v < V; v++)

			// Update dist[v] only if is not in sptSet,
			// there is an edge from u to v, and total
			// weight of path from src to v through u is
			// smaller than current value of dist[v]
			if (!sptSet[v] && graph[u][v]
				&& dist[u] != INT_MAX
				&& dist[u] + graph[u][v] < dist[v])
				dist[v] = dist[u] + graph[u][v];
	}

	// print the constructed distance array
	printSolution(dist);
}

// driver's code
int main()
{

	/* Let us create the example graph discussed above */
	int graph[V][V] = { { 0, 4, 0, 0, 0, 0, 0, 8, 0 },
						{ 4, 0, 8, 0, 0, 0, 0, 11, 0 },
						{ 0, 8, 0, 7, 0, 4, 0, 0, 2 },
						{ 0, 0, 7, 0, 9, 14, 0, 0, 0 },
						{ 0, 0, 0, 9, 0, 10, 0, 0, 0 },
						{ 0, 0, 4, 14, 10, 0, 2, 0, 0 },
						{ 0, 0, 0, 0, 0, 2, 0, 1, 6 },
						{ 8, 11, 0, 0, 0, 0, 1, 0, 7 },
						{ 0, 0, 2, 0, 0, 0, 6, 7, 0 } };

	// Function call
	dijkstra(graph, 0);

	return 0;
}

// This code is contributed by shivanisinghss2110

```

