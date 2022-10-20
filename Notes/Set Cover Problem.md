Given a universe U of n elements, a collection of subsets of U say S = {S1, S2…,Sm} where every subset Si has an associated cost. Find a minimum cost subcollection of S that covers all elements of U.

U = {1,2,3,4,5}
S = {S1,S2,S3}
S1 = {4,1,3},    Cost(S1) = 5
S2 = {2,5},      Cost(S2) = 10
S3 = {1,4,3,2},  Cost(S3) = 3

Output: Minimum cost of set cover is 13 and 
        set cover is {S2, S3}

There are two possible set covers {S1, S2} with cost 15
and {S2, S3} with cost 13.

## Why is it useful?
It was one of Karp’s NP-complete problems, shown to be so in 1972. Other applications: edge covering, vertex cover  
Interesting example: IBM finds computer viruses (wikipedia)  
Elements- 5000 known viruses  
Sets- 9000 substrings of 20 or more consecutive bytes from viruses, not found in ‘good’ code.  
A set cover of 180 was found. It suffices to search for these 180 substrings to verify the existence of known computer viruses.

Another example: Consider General Motors needs to buy a certain amount of varied supplies and there are suppliers that offer various deals for different combinations of materials (Supplier A: 2 tons of steel + 500 tiles for $x; Supplier B: 1 ton of steel + 2000 tiles for $y; etc.). You could use set covering to find the best way to get all the materials while minimizing cost.


Let us consider the above example to understand Greedy Algorithm.

_First Iteration:_  
I = {}

The per new element cost for S1 = Cost(S1)/|S1 – I| = 5/3

The per new element cost for S2 = Cost(S2)/|S2 – I| = 10/2

The per new element cost for S3 = Cost(S3)/|S3 – I| = 3/4

Since S3 has minimum value S3 is added, I becomes {1,4,3,2}.

_Second Iteration:_  
I = {1,4,3,2}

The per new element cost for S1 = Cost(S1)/|S1 – I| = 5/0  
Note that S1 doesn’t add any new element to I.

The per new element cost for S2 = Cost(S2)/|S2 – I| = 10/1  
Note that S2 adds only 5 to I.

The greedy algorithm provides the optimal solution for above example, but it may not provide optimal solution all the time. Consider the following example.

S1 = {1, 2}
S2 = {2, 3, 4, 5}
S3 = {6, 7, 8, 9, 10, 11, 12, 13}
S4 = {1, 3, 5, 7, 9, 11, 13}
S5 = {2, 4, 6, 8, 10, 12, 13}

Let the cost of every set be same.

The greedy algorithm produces result as {S3, S2, S1}

The optimal solution is {S4, S5}.


## Proof that the above greedy algorithm is Logn approximate.
Let OPT be the cost of optimal solution. Say (k-1) elements are covered before an iteration of above greedy algorithm. The cost of the k’th element <= OPT / (n-k+1) (Note that cost of an element is evaluated by cost of its set divided by number of elements added by its set). How did we get this result? Since k'th element is not covered yet, there is a Si that has not been covered before the current step of greedy algorithm and it is there in OPT. Since greedy algorithm picks the most cost effective Si, per-element-cost in the picked set must be smaller than OPT divided by remaining elements. Therefore cost of k’th element <= OPT/|U-I| (Note that U-I is set of not yet covered elements in Greedy Algorithm). The value of |U-I| is n - (k-1) which is n-k+1.