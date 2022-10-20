A Hash Table in C/C++ (Associative array) is **a [[Data Structure]] that maps keys to values**. This uses a hash function to compute indexes for a key. Based on the Hash Table index, we can store the value at the appropriate location.

## Hash Function
A hash function is a function where you put in a string and you get back a  number (not always the case, you can have hash function to convert integer to char and vica versa).

![[Pasted image 20221020204040.png]]

Requirement of a hash function
- It needs to be consistent. For example, suppose you put in “apple” and get back “4”. Every time you put in “apple”, you should get “4” back. Without this, your hash table won’t work.
- It should map diferent words to diferent numbers. For example, a hash function is no good if it always returns “1” for any word you put in. In the best case, every diferent word should map to a diferent number.


Put a hash function and an array together, and you get a data structure called a [[hash tables]].

Hash tables are probably the most useful complex data structure you’ll learn. hey’re also known as hash maps, maps, dictionaries, and associative arrays. And hash tables are fast!

You can get an item from an array instantly. And hash tables use an array to store the data, so they’re equally fast.

## Collisions
Like I said earlier, most languages have hash tables. You don’t need to know how to write your own. So, I won’t talk about the internals of hash tables too much. But you still care about performance! To understand the performance of hash tables, you irst need to understand what collisions are. he next two sections cover collisions and performance. First, I’ve been telling you a white lie. I told you that a hash function always maps diferent keys to diferent slots in the array.

![[Pasted image 20221020204339.png]]

In reality, it’s almost impossible to write a hash function that does this.

When the hash function creates the same output for two different input it is known has *collisions*.

Collisions are bad, and you need to work around them. here are many diferent ways to deal with collisions. he simplest one is this: if multiple keys map to the same slot, start a linked list at that slot.
![[Pasted image 20221020204525.png]]

There are two lessons here:
- Your hash function is really important. Your hash function mapped all the keys to a single slot. Ideally, your hash function would map keys evenly all over the hash.
- If those linked lists get long, it slows down your hash table a lot. But they won’t get long if you use a good hash function!


## Load Factor

The load factor of a hash table is easy to calculate. 
![[Pasted image 20221020204642.png]]

Hash tables use an array for storage, so you count the number of occupied slots in an array. For example, this hash table has a load factor of 2 /5, or 0.4.

![[Pasted image 20221020204702.png]]
Suppose you need to store the price of 100 produce items in your hash table, and your hash table has 100 slots. In the best case, each item will get its own slot.
This hash table has a load factor of 1. What if your hash table has only 50 slots? hen it has a load factor of 2. here’s no way each item will get its own slot, because there aren’t enough slots! Having a load factor greater than 1 means you have more items than slots in your array. Once the load factor starts to grow, you need to add more slots to your hash table. his is called resizing. For example, suppose you have this hash table that is getting pretty full.
![[Pasted image 20221020204810.png]]
You need to resize this hash table. so you create a new array that's bigger.
*The rule of thumb is to make an array that is twice the size.*
Now you need to re-insert all of those items into this new hash table using the hash function:
![[Pasted image 20221020204845.png]]
his new table has a load factor of 3 /8. Much better! With a lower load factor, you’ll have fewer collisions, and your table will perform better. *A good rule of thumb is, resize when your load factor is greater than 0.7.*