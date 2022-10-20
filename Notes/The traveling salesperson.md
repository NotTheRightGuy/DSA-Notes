This is a famous problem in computer science, because its growth is appalling and some very smart people think it can’t be improved. It’s called the traveling salesperson problem.


You have a salesperson.
The salesperson has to go to five cities.
![[Pasted image 20221020193350.png]]

This salesperson, whom I’ll call Opus, wants to hit all five cities while travelling the minimum distance. Here’s one way to do that: look at every possible order in which he could travel to the cities.

![[Pasted image 20221020193417.png]]

He adds up the total distance and then picks the path with the lowest distance. There are 120 permutations with 5 cities, so it will take 120 operations to solve the problem for 5 cities. For 6 cities, it will take 720 operations (there are 720 permutations). For 7 cities, it will take 5,040 operations!

In general, for n items, it will take n! (n factorial) operations to compute the result. So this is O(n!) time, or factorial time. It takes a lot of operations for everything except the smallest numbers. Once you’re dealing with 100+ cities, it’s impossible to calculate the answer in time—the Sun will collapse first.

*This is one of the unsolved problems in computer science.* There is no fast known algorithm for it. The best we can do is come up with an appoximation solution.

---
Let's start small. suppose you only have two cities. There are two routes to choose from.

![[Pasted image 20221020214715.png]]
You may be wondering, “In the traveling salesperson problem, is there a speciic city you need to start from?” For example, let’s say I’m the traveling salesperson. I live in San Francisco, and I need to go to four other cities. San Francisco would be my start city. But sometimes the start city isn’t set. Suppose you’re FedEx, trying to deliver a package to the Bay Area. he package is being lown in from Chicago to one of 50 FedEx locations in the Bay Area. hen that package will go on a truck that will travel to diferent locations delivering packages. Which location should it get lown to? Here the start location is unknown. It’s up to you to compute the optimal path and start location for the traveling salesperson. he running time for both versions is the same. But it’s an easier example if there’s no deined start city, so I’ll go with that version. Two cities = two possible routes.

**3 cities**
Now suppose you add one more city. How many possible routes are there?
![[Pasted image 20221020214824.png]]
There are six total routes, two for each city you can start at.
![[Pasted image 20221020214838.png]]

*4 Cities*
Let's add another city, Fremont. Now suppose you start at Fremont.

![[Pasted image 20221020214927.png]]

There are six possible routes starting from Fremont. And hey! hey look a lot like the six routes you calculated earlier, when you had only three cities. Except now all the routes have an additional city, Fremont! here’s a pattern here. Suppose you have four cities, and you pick a start city, Fremont. here are three cities let. And you know that if there are three cities, there are six diferent routes for getting between those cities. If you start at Fremont, there are six possible routes. You could also start at one of the other cities.

Do you see a pattern?
![[Pasted image 20221020215003.png]]


The traveling-salesperson problem and the set-covering problem both have something in common: you calculate every possible solution and pick the smallest/shortest one. Both of these problems are NP-complete.



## Approximating

What’s a good approximation algorithm for the traveling salesperson? Something simple that inds a short path. See if you can come up with an answer before reading on. Here’s how I would do it: arbitrarily pick a start city. hen, each time the salesperson has to pick the next city to visit, they pick the closest unvisited city. Suppose they start in Marin.

![[Pasted image 20221020215056.png]]
Total distance: 71 miles. Maybe it’s not the shortest path, but it’s still pretty short.

