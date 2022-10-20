
The process in which a function calls itself directly or indirectly is called recursion and the corresponding function is called a recursive function.

![[Pasted image 20221020195143.png]]


Recursion is an amazing technique with the help of which we can reduce the length of our code and make it easier to read and write. It has certain advantages over the iteration technique which will be discussed later. A task that can be defined with its similar subtask, recursion is one of the best solutions for it. For example; The Factorial of a number.

```cpp
int factorial(int n){
	if(n <= 1){
		return 1;
	}
	else{
		return n * factorial(n-1);
		}
}
```

# Base Case and Recursive case

Because a recursive function calls itself, it’s easy to write a function incorrectly that ends up in an ininite loop.

When you write a recursive function, you have to tell it when to stop recursing. that’s why *every recursive function has two parts: the base case, and the recursive case.*

In our factorial function:

![[Pasted image 20221020195528.png]]