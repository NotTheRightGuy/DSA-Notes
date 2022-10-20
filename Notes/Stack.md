Stack is **a linear[[ data structure]] which follows a particular order in which the operations are performed**. The order may be LIFO(Last In First Out) or FILO(First In Last Out). There are many real-life examples of a stack. Consider an example of plates stacked over one another in the canteen

## The call stack
Your computer uses a stack internally called the call stack.
In [computer science](https://en.wikipedia.org/wiki/Computer_science "Computer science"), a **call stack** is a [stack](https://en.wikipedia.org/wiki/Stack_(abstract_data_type) "Stack (abstract data type)") [data structure](https://en.wikipedia.org/wiki/Data_structure "Data structure") that stores information about the active [subroutines](https://en.wikipedia.org/wiki/Subroutine "Subroutine") of a [computer program](https://en.wikipedia.org/wiki/Computer_program "Computer program"). This kind of stack is also known as an **execution stack**, **program stack**, **control stack**, **run-time stack**, or **machine stack**, and is often shortened to just "**the stack**". Although maintenance of the call stack is important for the proper functioning of most [software](https://en.wikipedia.org/wiki/Software "Software"), the details are normally hidden and automatic in [high-level programming languages](https://en.wikipedia.org/wiki/High-level_programming_language "High-level programming language"). Many computer [instruction sets](https://en.wikipedia.org/wiki/Instruction_set "Instruction set") provide special instructions for manipulating stacks

## The call stack with recursion
Recursive functions use the call stack too! Let’s look at this in action with the factorial function. factorial(5) is written as 5!, and it’s defined like this: 5! = 5 * 4 * 3 * 2 * 1. 

Similarly, factorial(3) is 3 * 2 * 1.

Here’s a recursive function to calculate the factorial of a number in python

```py
def fact(x):
	if x == 1:
	 return 1
	else:
		return x * fact(x-1)
```

![[Pasted image 20221020195939.png]]


![[Pasted image 20221020195954.png]]