Quicksort is a sorting [[algorithm]]. It’s much faster than [[selection sort]] and is frequently used in real life. For example, the C standard library has a function called [[qsort]], which is its implementation of quicksort. Quicksort also uses D&C.

Let’s use quicksort to sort an array. What’s the simplest array that a sorting algorithm can handle (remember my tip from the previous section)? Well, some arrays don’t need to be sorted at all.

![[Pasted image 20221020202224.png]]

Empty arrays and arrays with just one element will be the base case. You can just return those arrays as is—there’s nothing to sort:

```py
def quickSort(array):
	if(len(array) < 2):
		return array 
```

Let’s look at bigger arrays. An array with two elements is pretty easy to sort, too.

![[Pasted image 20221020202336.png]]

What about an array of three elements?
Remember, you’re using D&C. So you want to break down this array until you’re at the base case. Here’s how quicksort works. First, pick an element from the array. his element is called the pivot.

Now ind the elements smaller than the pivot and the elements larger than the pivot.
![[Pasted image 20221020202412.png]]

This is called partitioning. Now you have
- A sub-array of all the numbers less than the pivot
- The pivot
- A sub-array of all numbers greater than the pivot
The two sub-arrays aren’t sorted. hey’re just partitioned. But if they were sorted, then sorting the whole array would be pretty easy.
![[Pasted image 20221020202505.png]]
This will work with any pivot.
Now what about an array of four elements?
![[Pasted image 20221020202600.png]]
Suppose you choose 33 as the pivot again
![[Pasted image 20221020202618.png]]
The array on the left has three elements. You already know how to sort an array of three elements: call quicksort on it recursively.
![[Pasted image 20221020202715.png]]
Similary you can sort any array recurrsively, the code for such in python as as follows

```py
def quicksort(array):
	if len(array) < 2:
		return array
	else:
		pivot = array[0]
		less = [i for i in array[1:] if i < pivot]
		greater = [i for i in array[1:] if i > pivot]
		return quicksort(less) + [pivot] + quicksort(greater)
```

## Big O notation revisted
Quicksort is unique because its speed depends on the pivot you choose.

There's another sorting [[algorithm]] called *merge sort*, which is O(n log n). Much Faster! Quicksort is a tricky case. In the worst case, quicksort takes O($n^2$) time.

It is as slow as selection sort! But that's the worst case. In the average case, quicksort takes O(n log n) time.