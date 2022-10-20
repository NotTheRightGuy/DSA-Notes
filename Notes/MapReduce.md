It is a type of [[Parallel algorithm]]

The MapReduce [[algorithm]] contains two important tasks, namely Map and Reduce.

-   The map task is done by means of Mapper Class
-   The reduce task is done by means of Reducer Class.

Mapper class takes the input, tokenizes it, maps and sorts it. The output of Mapper class is used as input by Reducer class, which in turn searches matching pairs and reduces them.

![[Pasted image 20221020222808.png]]

MapReduce implements various mathematical algorithms to divide a task into small parts and assign them to multiple systems. In technical terms, MapReduce algorithm helps in sending the Map & Reduce tasks to appropriate servers in a cluster.

These mathematical algorithms may include the following −

-   Sorting
-   Searching
-   Indexing
-   TF-IDF
