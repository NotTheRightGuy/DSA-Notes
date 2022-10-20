Selection sort is a neat [[algorithm]], but it's not very fast. [[Quicksort]] is a faster sorting algorithm that only takes O($n log n$) times.

The following is the code for selection sort in C++

```cpp
int smallestNumber(vector<int> arr)

{

    int length = arr.size();

    int smallest = arr[0];

    for (auto x : arr)

    {

        if (x < smallest)

        {

            smallest = x;

        }

    }

    return smallest;

}

  

vector<int> selectionSort(vector<int> arr)

{

    int length = arr.size();

    vector<int> returnArr;

    for (int i = 0; i < length; i++)

    {

        returnArr.push_back(smallestNumber(arr));

        arr.erase(find(arr.begin(), arr.end(), smallestNumber(arr)));

    }

    return returnArr;

}
```
It utilises a function called *smallestNumber* which takes an array as input and returns the shortest element in the array and at the same time removing it from the array.

The *selectionSort* simply takes an array as input and one by one finds the smallest element in the given array and push it to a newly made array. Once there are no items in array it returns the new Array.

![[Pasted image 20221020194941.png]]