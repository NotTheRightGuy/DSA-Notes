A greedy [[algorithm]] is simple: at each step, pick the optimal move. In this case, each time you pick a class, you pick the class that ends the soonest. In technical terms: at each step you pick the locally optimal solution, and in the end you’re let with the globally optimal solution.

Greedy is an algorithmic paradigm that builds up a solution piece by piece, always choosing the next piece that offers the most obvious and immediate benefit. So the problems where choosing locally optimal also leads to global solution are the best fit for Greedy.

For example consider the [[KnapSack Problem]]. The local optimal strategy is to choose the item that has maximum value vs weight ratio. This strategy also leads to a globally optimal solution because we are allowed to take fractions of an item.

![[Pasted image 20221020213248.png]]

[[Set Cover Problem]] and [[The traveling salesperson]] problem can also be solved using greedy algorithms