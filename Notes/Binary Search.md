
Binary Search is an [[Algorithm]]; it's input is a *sorted list* of elements. If an element you're looking for is in that list, binary search returns the position where it's located otherwise, binary search returns **null**

In general for for any list of *n*, binary search will take $log_2 n$ steps to run in the worst case, whereas simple search will take n steps

- One may need to understand the basics of [[Logarithms]] to understand the time complexity.

Let us see how binary search works

![[Pasted image 20221020190112.png]]

In the beginning we assign a value of *low* to the lowest index and *high* to the highest index which will also be equal to `length(arr) - 1` 

Each time you check the middle element:

```python
mid = (low + high) / 2
guess = arr[mid]
```

if the guess is too low, you update low accordingly
![[Pasted image 20221020190533.png]]
```python
if(guess < item):
		low = mid + 1
```
or if the guess is too high, we update the high accordingly
![[Pasted image 20221020190714.png]]
Here's the full code in C++
```cpp
int binarySearch(int *arr, int toSearch, int length)

{

    int low = 0;

    int high = length - 1;

  

    while (low <= high)

    {

        int mid = (low + high) / 2;

        if (arr[mid] == toSearch)

        {

            return mid;

        }

        else

        {

            if (arr[mid] < toSearch)

            {

                low = mid + 1;

            }

            else

            {

                high = mid - 1;

            }

        }

    }

    return 0;

}
```
