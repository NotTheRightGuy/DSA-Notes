Dynamic Programming is **mainly an optimization over plain recursion**. Wherever we see a recursive solution that has repeated calls for same inputs, we can optimize it using Dynamic Programming. The idea is to simply store the results of subproblems, so that we do not have to re-compute them when needed later.

Dynamic programming starts by solving subproblems and builds up to solving the big problem.
Let's revisit the [[knapsack problem]], you'll start by solving the problem for smalled knapsacks (or "sub-knapsacks") and then work up to solvinf the original problem.


---

Every dynamic-programming algorithm starts with a grid. Here's a gird for the knapsack problem.
![[Pasted image 20221020215727.png]]

The rows of the grid are the items, and the columns are knapsack weights from 1 lb to 4 lb. You need all of those columns because they will help you calculate the values of the sub-knapsacks. he grid starts out empty. You’re going to ill in each cell of the grid. Once the grid is illed in, you’ll have your answer to this problem! Please follow along. Make your own grid, and we’ll ill it out together.

**The guitar row**
![[Pasted image 20221020215831.png]]

This is the guitar row, which means you’re trying to it the guitar into the knapsack. At each cell, there’s a simple decision: do you steal the guitar or not? Remember, you’re trying to ind the set of items to steal that will give you the most value.
The first cell has a knapsack of capacity 1 lb. he guitar is also 1 lb, which means it its into the knapsack! So the value of this cell is $1,500, and it contains a guitar.

Let's start filling in the grid.

![[Pasted image 20221020215915.png]]

Like this, each cell in the grid will contain a list of all the items that it into the knapsack at that point.
Let’s look at the next cell. Here you have a knapsack of capacity 2 lb. Well, the guitar will deinitely it in there!
The same for the rest of the cells in this row. Remember, this is the irst row, so you have only the guitar to choose from. You’re pretending that the other two items aren’t available to steal right now.
![[Pasted image 20221020215947.png]]

At this point, you’re probably confused. Why are you doing this for knapsacks with a capacity of 1 lb, 2 lb, and so on, when the problem talks about a 4 lb knapsack? Remember how I told you that dynamic programming starts with a small problem and builds up to the big problem? You’re solving subproblems here that will help you to solve the big problem.

Remember, you’re trying to maximize the value of the knapsack. his row represents the current best guess for this max. So right now, according to this row, if you had a knapsack of capacity 4 lb, the max value you could put in there would be $1,500.
![[Pasted image 20221020220020.png]]

**The Stereo Row**
Let’s do the next row. his one is for the stereo. Now that you’re on the second row, you can steal the stereo or the guitar. At every row, you can steal the item at that row or the items in the rows above it. So you can’t choose to steal the laptop right now, but you can steal the stereo and/or the guitar. Let’s start with the irst cell, a knapsack of capacity 1 lb. he current max value you can it into a knapsack of 1 lb is $1,500.

![[Pasted image 20221020220052.png]]
Should you steal the stereo or not? You have a knapsack of capacity 1 lb. Will the stereo it in there? Nope, it’s too heavy! Because you can’t it the stereo, $1,500 remains the max guess for a 1 lb knapsack.
![[Pasted image 20221020220108.png]]
he stereo still doesn’t it, so your guesses remain unchanged. What if you have a knapsack of capacity 4 lb? Aha: the stereo inally its! he old max value was $1,500, but if you put the stereo in there instead, the value is $3,000! Let’s take the stereo.
![[Pasted image 20221020220127.png]]

You just updated your estimate! If you have a 4 lb knapsack, you can it at least $3,000 worth of goods in it. You can see from the grid that you’re incrementally updating your estimate.

![[Pasted image 20221020220140.png]]

**The laptop row**
Let’s do the same thing with the laptop! he laptop weighs 3 lb, so it won’t it into a 1 lb or a 2 lb knapsack. he estimate for the irst two cells stays at $1,500.

![[Pasted image 20221020220201.png]]

At 3 lb, the old estimate was $1,500. But you can choose the laptop instead, and that’s worth $2,000. So the new max estimate is $2,000!

![[Pasted image 20221020220215.png]]

At 4 lb, things get really interesting. his is an important part. he current estimate is $3,000. You can put the laptop in the knapsack, but it’s only worth $2,000.
![[Pasted image 20221020220254.png]]

Hmm, that’s not as good as the old estimate. But wait! he laptop weighs only 3 lb, so you have 1 lb free! You could put something in this 1 lb.

![[Pasted image 20221020220307.png]]
What’s the maximum value you can it into 1 lb of space? Well, you’ve been calculating it all along.
![[Pasted image 20221020220331.png]]

According to the last best estimate, you can it the guitar into that 1 lb space, and that’s worth $1,500. So the real comparison is as follows.
![[Pasted image 20221020220355.png]]

The final grid looks like this.


![[Pasted image 20221020220412.png]]


By observing, we find the value of each cell is calculated by the formula
![[Pasted image 20221020220447.png]]

