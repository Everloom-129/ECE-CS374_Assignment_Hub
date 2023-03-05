# ECE374 Assignment 4

02/01/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

## T3 FifthSort

![image-20230303183814593](./ECE374 Assignment 4 p3.assets/image-20230303183814593.png)

### (a) Prove correctness

1)when n <100, it will be sorted by brute force, it should be correct

2)when n>=100, each recursion uses some parts of the A[n], so the number decreases (or say convergent) all the time, so one of the son recursion can reach the n<100 status.

let us use a list to represent each k numbers in A:[unknown,unknown,unknown,unknown,unknown]

The AF or AS mean the list after the sort.

after "first sort":

[smallest k number in A[0:3k],middle k numbers,largest k numbers in A[0:3k],unknown,unknown]=AF

after "second sort": 

[smallest k number in AF[0:3k], middle k numbers, smallest k number in AF[2k+1:n],middle k numbers,largest k numbers in all]=AS

after "third sort":

[smallest k number in all,middle k numbers,middle k numbers,middle k numbers,largest k numbers in all]

after "fourth sort": it sorts the middle k numbers in the list, because it has got the smallest and largest k numbers in n.

### (b)

No. When n=11, it will trigger the else statement. So k=3, but in the fourth sort, 4*k=12, which overflow and will cause an error. 



### (c)

Yes, because the n<? only affect the biggest size we need to use brute force. But we need to pay attention to the overflow due to the ceil(n/5) and the fourth sort's 4k, which means 4k should smalled than n. 

Assume that n=5m+l (0<=l<=4), so 4k = 4 ceil(n/5)= 4m+4=<n=5m+l <=> 4<=m+l

1) if n=13: m=2,l=3, m+l>4
2) if n=14: m=2,l=4, m+l>4
3) if n=15: because it is the multiple of 5, so the ceil function will not trigger +1. k=3 => 4k=12<15, it is acceptable.
4) if n>16: so m+l>=m=4, so it is acceptable.



### (d)

No. assume that there are 104 number, and the largest 24 numbers in A[1,24]. after first sort, they are in A[37,60]. after second sort, they are splitted, in A[37,40] and A[85,104]. And the  A[37,40] will not have chance to be in the right place( A[81,84]), because the rest sort are sort the number from A[1] to A[80].



### (e)

T(n)=4*T($\frac{3n}{5}$) +O(1)

If we use master theory, so a=4,b=5/3, a>b

So the complexity is $O(n^{\frac{\lg(4)}{\lg(\frac{5}{3})}})\approx O(n^{2.7138})$

