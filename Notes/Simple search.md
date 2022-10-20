A searching algorithm that traverse over every element to check weather the element is the one you are trying to find is a simple search algorithm

It's often the slowest searching algorithm with a *BigO(n)*

```cpp
int Search(int *arr, int n,int length){
	for(int i = 0;int i < length;i++){
		if(arr[i] == n){
			return i;
		}
	}
	return -1;
}
```