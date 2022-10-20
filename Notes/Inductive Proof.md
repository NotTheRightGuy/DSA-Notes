A proof by induction is just like an ordinary proof in which every step must be justified. However it employs a neat trick which allows you to prove a statement about an arbitrary number n by first proving it is true when n is 1 and then assuming it is true for n=k and showing it is true for n=k+1. The idea is that if you want to show that someone can climb to the nth floor of a fire escape, you need only show that you can climb the ladder up to the fire escape (n=1) and then show that you know how to climb the stairs from any level of the fire escape (n=k) to the next level (n=k+1).

**Example 1: Prove 1+2+...+n=n(n+1)/2 using a proof by induction.**

**n=1:** 1=1(2)/2=1 checks.

**Assume n=k holds:** 1+2+...+k=k(k+1)/2 (Induction Hyypothesis)  
**Show n=k+1 holds:** 1+2+...+k+(k+1)=(k+1)((k+1)+1)/2  
_I just substitute k and k+1 in the formula to get these lines. Notice that I write out what I want to prove._

_Now I start with the left side of the equation I want to show and proceed using the induction hypothesis and algebra to reach the right side of the equation._ 1+2+...+(k+1)=1+2+...+k+(k+1)  
=k(k+1)/2 + (k+1) by the Induction Hypothesis  
=(k(k+1)+2(k+1))/2 by 2/2=1 and distridution of division over addition  
=(k+2)(k+1)/2 by distribution of multiplication over addition  
=(k+1)(k+2)/2 by commutativity of multiplication  
  
QED