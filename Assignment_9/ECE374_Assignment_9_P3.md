# ECE374 Assignment 8 

04/20/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

[toc]

## 3. Algorithmic Complexity Classes

![image-20230420154202934](./ECE374_Assignment_9_P3.assets/image-20230420154202934.png)

## (a) The max kite problem 

It is NP-complete. Let's first analyze the problem with respect to the complexity classes:

1. The problem is in NP:
To show that the problem is in NP, we need to prove that there exists a polynomial-time verifier for the problem. Given a graph G and a goal g, and a certificate (subgraph) H, we can verify in polynomial time whether H is a valid kite of size 2g or not by checking if it has a clique of size g and a tail of size g. Therefore, the max kite problem is in NP.

2. The problem is NP-hard:
To show that the problem is NP-hard, we need to prove that an NP-complete problem can be reduced to the max kite problem in polynomial time. We will use the Clique problem as our NP-complete problem.

Clique Problem: Given a graph G and a goal k, does G contain a clique of size k?

Reduction: Given an instance of the Clique problem (G, k), we can create an instance of the max kite problem (G', g) as follows:
- Set G' = G (i.e., use the same graph G for G').
- Set g = k.

Now, we need to show that this reduction is correct, i.e., G has a clique of size k if and only if G' has a kite of size 2g.

If G has a clique of size k, then G' has a clique of size g. By adding an isolated path of length g to G', we can form a kite of size 2g in G'. Thus, if G has a clique of size k, G' has a kite of size 2g.

If G' has a kite of size 2g, then it has a clique of size g in G' and a tail of length g. Since G' = G, G has a clique of size k. Thus, if G' has a kite of size 2g, G has a clique of size k.

Since we can reduce the Clique problem (an NP-complete problem) to the max kite problem in polynomial time, the max kite problem is NP-hard.

Combining the facts that the max kite problem is in NP and is NP-hard, we can conclude that the max kite problem is NP-complete.





## (b) The 4kite problem 

This is a special case of the max kite problem, where the goal g is fixed to 4. For the 4kite problem, given a graph G, we need to determine if there is a subgraph that is a kite with 4 vertices in the clique and 4 vertices in the tail.

The 4kite problem can be solved in polynomial time, and thus belongs to the class P. Here's an algorithm to solve the 4kite problem:

1. Enumerate all possible subsets of 4 vertices from the graph G. For each subset, check if the vertices form a clique of size 4. This can be done in polynomial time, as there are O(n^4) subsets to check, and for each subset, it takes O(4^2) time to check if it forms a clique.

2. If a clique of size 4 is found, enumerate all possible subsets of 4 vertices outside the clique. For each subset, check if the vertices form a path of length 4. This can also be done in polynomial time, as there are O(n^4) subsets to check, and for each subset, it takes O(4) time to check if it forms a path of length 4.

3. If a clique of size 4 and a path of length 4 are found, check if the path is connected to one of the vertices in the clique. If such a connection exists, then the graph G contains a 4kite, and the algorithm returns True. Otherwise, the algorithm returns False.

Since the algorithm runs in polynomial time, the 4kite problem belongs to the complexity class P.








## Reference:

[(101条消息) 【算法期末作业】课本8.19 kite问题的NP完全问题证明_wenyq7的博客-CSDN博客](https://blog.csdn.net/qq_37333947/article/details/74937933)

