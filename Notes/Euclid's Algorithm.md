`“If you ind the biggest box that will work for this size, that will be the biggest box that will work for the entire farm.”`

The Euclidean algorithm is a way to find the greatest common divisor of two positive integers. GCD of two numbers is the largest number that divides both of them. A simple way to find GCD is to factorize both numbers and multiply common prime factors.

Recall that the Greatest Common Divisor (GCD) of two integers A and B is the **largest integer that divides both A and B**.

## **Basic Euclidean Algorithm for GCD:**

The algorithm is based on the below facts. 

-   If we subtract a smaller number from a larger one (we reduce a larger number), GCD doesn’t change. So if we keep subtracting repeatedly the larger of two, we end up with GCD.
-   Now instead of subtraction, if we divide the smaller number, the algorithm stops when we find the remainder 0.

Below is the implementation of Euclid's [[algorithm]] in C++

```cpp
int gcd(int a, int b){
	if(a == 0){
	return b;
	}
	return gcd(b % a,a);
}
```