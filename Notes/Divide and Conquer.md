A divide-and-conquer [[algorithm]] **recursively breaks down a problem into two or more sub-problems of the same or related type, until these become simple enough to be solved directly**. The solutions to the sub-problems are then combined to give a solution to the original problem.

This technique can be divided into the following three parts:

1.  **Divide:** This involves dividing the problem into smaller sub-problems.
2.  **Conquer:** Solve sub-problems by calling recursively until solved.
3.  **Combine:** Combine the sub-problems to get the final solution of the whole problem.

## What does not qualifies as Divide and Conquer:

Binary Search is a searching algorithm. In each step, the algorithm compares the input element x with the value of the middle element in the array. If the values match, return the index of the middle. Otherwise, if x is less than the middle element, then the algorithm recurs for the left side of the middle element, else recurs for the right side of the middle element. Contrary to popular belief, this is not an example of Divide and Conquer because there is only one sub-problem in each step (Divide and conquer requires that there must be two or more sub-problems) and hence this is a case of Decrease and Conquer.

*D&C isn’t a simple algorithm that you can apply to a problem. Instead, it’s a way to think about a problem.*

Suppose you have to add up all the numbers and return the total in an array, it's easy to do using a loop,

buy how will we do this with a recursive function?

- Figure out the base case. What’s the simplest array you could get? hink about the simplest case, and then read on. If you get an array with 0 or 1 element, that’s pretty easy to sum up.
![[Pasted image 20221020200927.png]] 
- You need to move closer to an empty array with every recursive call. How do you reduce your problem size? Here’s one way.
![[Pasted image 20221020201006.png]]
It’s the same as this.
![[Pasted image 20221020201018.png]]
In either case, the result is 12. But in the second version, you’re passing a smaller array into the sum function. that is, you decreased the size of your problem!

Your sum function could work like this
![[Pasted image 20221020201055.png]]
![[Pasted image 20221020201111.png]]
Remember, [[recursion]] keeps track of the state.
![[Pasted image 20221020201124.png]]