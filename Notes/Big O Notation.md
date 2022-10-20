
Big O notation is a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity. It is a member of a family of notations invented by Paul Bachmann, Edmund Landau, and others, collectively called Bachmann–Landau notation or asymptotic notation.

*In plain words, Big O notation describes the **complexity** of your code using algebraic terms.*

Big O notation tells you how fast an algorithm is. For example, suppose you have a list of size n. [[Simple search]] needs to check each element, so it will take n operations. he run time in Big O notation is O(n). Where are the seconds? here are none—Big O doesn’t tell you the speed in seconds. Big O notation lets you compare the number of operations. It tells you how fast the algorithm grows.

Here’s another example.[[ Binary search]] needs log n operations to check a list of size n. What’s the running time in Big O notation? It’s O(log n). In general, Big O notation is written as follows.

![[Pasted image 20221020192948.png]]

This tells you the number of operations an algorithm will make. It’s called Big O notation because you put a “big O” in front of the number of operations (it sounds like a joke, but it’s true!).

## Big O establishes a worst-case run time
Suppose you’re using simple search to look for a person in the phone book. You know that simple search takes O(n) time to run, which means in the worst case, you’ll have to look through every single entry in your phone book. In this case, you’re looking for Adit. his guy is the irst entry in your phone book. So you didn’t have to look at every entry—you found it on the irst try. Did this algorithm take O(n) time? Or did it take O(1) time because you found the person on the irst try? Simple search still takes O(n) time. In this case, you found what you were looking for instantly. hat’s the best-case scenario. But Big O notation is about the worst-case scenario. So you can say that, in the worst case, you’ll have to look at every entry in the phone book once. hat’s O(n) time. It’s a reassurance—you know that simple search will never be slower than O(n) time.

### Some common Big O run times
Here are five Big O run times that you’ll encounter a lot, sorted from fastest to slowest:
- O(log n), also known as log time. Example: [[Binary search]]. 
- O(n), also known as linear time. Example: [[Simple search]].
- O(n * log n). Example: A fast sorting algorithm, like [[Quicksort]]
- O(n 2 ). Example: A slow sorting algorithm, like [[selection sort]].
- O(n!). Example: A really slow algorithm, like [[The traveling salesperson]] 


![[Pasted image 20221020192551.png]]


The main takeaways are
- Algorithm speed isn’t measured in seconds, but in growth of the number of operations.
- Instead, we talk about how quickly the run time of an algorithm increases as the size of the input increases.
- Run time of algorithms is expressed in Big O notation.
- O(log n) is faster than O(n), but it gets a lot faster as the list of items you’re searching grows.