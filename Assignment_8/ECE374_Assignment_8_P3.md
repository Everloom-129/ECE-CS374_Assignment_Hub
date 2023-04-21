# ECE374 Assignment 8

04/14/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

## T5 k-length-path

![image-20230414210357605](./ECE374_Assignment_8_P3.assets/image-20230414210357605.png)

### Solution

### (a) **NP-hard proof**

#### Reduction Algorithm Constructions: 

1) For Hamiltonian path graph **H**, we create some groups. Each group represent a vertex in **G**. There are **k** vertexes in a group, and they are completely connected with each other in this group.
2) Two groups are connected means all the vertexes in this two group are completely connected with each other. And the connection between two group is the edge in **G**

So the graph **G** have spanning tree that have degree at most **k** if and only if there is Hamiltonian path in **H**

#### **Hamiltonian path**  **$\Rightarrow$  Spanning** **tree:** 

1) Because Hamiltonian path will go through all the groups, *all the vertexes in **G** are connected,* 

2) If there is a cycle in groups in **H**, we can cut one of the edge in the cycle, so that the new graph **G** has not cycle
3) Because each group only has **k** vertexes as defined in construction, the path only can get in or get out **k** times, or it will use repetitive vertex.

Therefore, the constructed yes-instance of Hamiltonian path can be treated as the yes-instance of low-degree spanning tree. 

#### Spanning tree $\Rightarrow$ Hamiltonian path:

1) The graph just like the structure in the constructions.
2) It will be a Hamiltonian path in G.
   - If a vertex in the spanning tree has **n** edges, which means the group represent this vertex is connected with other **n** groups. Because **n**<=**k** (it is a **k** low degree spanning tree), each group allow  a path to go through this group **n** times. So, there is a Hamiltonian path.( Because each vertex in the group can provide a opportunity for a path get in and get out to another group, there are just **n** other groups connected with this group. So, it is not possible that a Hamiltonian path algorithm break due to a group is unavailable)

Given **G**, we can easily construct **H** in polynomial time by brute force.

Therefore, arbitrary yes-instance of low-degree spanning tree can be transferred into a special yes-instance of Hamiltonian path. 

### (b) High degree spanning tree problem

For **G(V,E)**, let |**V**|=**n**,|**E**|=**m**. 

1. we search all the vertexes to find the vertexes with **max degree**, which use **O(n+m)**. 

   If **max degree** is smaller than k, return false.

2. Then we do **BFS** by using this vertex as the root. **BFS**  will use all edges of this vertex to ensure max degree vertex of spanning tree is same to the degree of this vertex. And the **BFS** use **O(n+m)**.

3. If **BFS** cannot connect all the vertexes, which means there is not spanning tree for this graph, so return false. Else return true.

#### Algorithm

```python
Find_HDST(V_list,E_list,k):
    find largest degree vertex MDV and its degree D_MDV by V_list and E_list
    if D_MDV<k:
        return false
    if BFS(V_list, E_list, root=MDV)==false:
        return false
    return true
```





#### Time complexity

The search cost is **O(n+m)** and the BFS cost is O(n+m), so the total cost is **O(n+m)**

 
