Any time we talk about an algorithm, we discuss about it's running time. Generally we want to choose the most efficient algorithm - whether you are trying to optimise for time or space

Back to [[Binary Search]]. How much time do you save by using it? Well, the irst approach was to check each number, one by one. If this is a list of 100 numbers, it takes up to 100 guesses. If it’s a list of 4 billion numbers, it takes up to 4 billion guesses. So the maximum number of guesses is the same as the size of the list. his is called *[[linear time]]*

Binary search is diferent. If the list is 100 items long, it takes at most 7 guesses. If the list is 4 billion items, it takes at most 32 guesses. Powerful, eh? Binary search runs in *[[logarithmic time]]* (or log time, as the natives call it).

![[Pasted image 20221020191548.png]]

The [[Big O Notation]] notation is written as follows.

![[Pasted image 20221020192236.png]]

his tells you the number of operations an algorithm will make. It’s called Big O notation because you put a “big O” in front of the number of operations (it sounds like a joke, but it’s true!).