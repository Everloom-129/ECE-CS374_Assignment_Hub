# ECE374 Assignment 6

03/30/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

## T5 k-length-path

![image-20230330212921555](./ECE374 Assignment_7_p5.assets/image-20230330212921555.png)
### Solution
#### (a) at most k case

#### Intuition:

Here we choose to use **Bellman-Ford algorithm** to find the shortest path.    

We need V_list and E_list from G, two dictionary: ***dic_min_path_value*** and ***dic_min_path***, start point s, end point t and number k.

The dic_min_path_value[i] stores the distance from s to i, which is used to check and update the dic_min_path[i]. The dic_min_path[i] stores the path from s to i, and it will be updated when find a smaller distance path.

At first, we need to initial all the dic_min_path_value to infinite except the dic_min_path_value[s], because it is the start point. And initial the dic_min_path[s]=[s]. Then we will read the E_list k times, each time we will do:

1. get the edge (u,v,w), w is the weight of this edge.
2. if dic_min_path_value[v]>dic_min_path_value[u]+w, then dic_min_path_value[v]=dic_min_path_value[u]+w and dic_min_path[v]=dic_min_path[u]+[v]

After k times, we return the dic_min_path_value[e] and dic_min_path[e], which means the min distance and min path from s to e.



```python
import math
def Bellman_Ford(V_list,E_list,s,t,k):
    dic_min_path_value={}
    dic_min_path={}
    #init
    for node in V_list:
        dic_min_path_value[node]=math.inf
    dic_min_path_value[s]=0
    dic_min_path[s]=[s]
    
    #k times loop
    for ki in range(k):
        for edge in E_list:
            u=edge[0]
            v=edge[1]
            w=edge[2]
            if dic_min_path_value[v]>dic_min_path_value[u]+w:
                dic_min_path_value[v]=dic_min_path_value[u]+w
                dic_min_path[v]=dic_min_path[u]+[v]
                    
    return dic_min_path_value[t],dic_min_path[t]
```

Because we use n to initial and k*m in the loop. So it is **O(n+k * m)** which is equivalent to **O(k(n+m)).**

#### (b) Exactly k case

![image-20230331102043593](./ECE374 Assignment_7_p5.assets/image-20230331102043593.png)

In this case, we do not care about the weight of each edge. So we can use modified dfs to search the k-path node. We allow the algorithm to go back, and just limit the number of paths it passed by decrease the k in each recursion. So it will only run k times and make sure the ending point is t, or it will return nothing.

```python
def modified_dfs(V_list,E_list,s,t,k):
    if k==0:
        if s==t:
            #this k level node is t! finish
            return [t]
        else:
            #this k level node is not t.
            return None
    else:
        for every edge start from s:
        	path=modified_dfs(V_list,E_list,edge[1],t,k-1)
            if path!=None:
                #Because it must have one k distance path as the question
                #we do not need to consider the situation it cannnot find a path
               return [s]+path

            
```

Compared with the original dfs which is O(n+m), this algorithm will at most visit each node or edge k times. So the complexity is **O(k(n+m))**.
