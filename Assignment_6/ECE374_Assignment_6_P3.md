# ECE374 Assignment 6

03/23/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

## T3 Chess Championship

![image-20230323212527690](./ECE374_Assignment_6_P3.assets/image-20230323212527690.png)

### a)  Recurrence Relationship

Intuition: 

HMI 模型 ，arlpb

第N场比赛，每个人分数的情况

会受前一场比赛影响

expectation matrix 统计



To solve this problem, we need to calculate the probability of the each game win k score. And at the end, we just sum all the probability that in gth that win equal or more than i scores

Because we need to consider the black and white status, so we create a $p_{status}=[[ww,wd,wl],[bw,bd,bl]]$ to store the probability.

The base case is:
$$
P[status][0][0]=p_{status}[status][2]
\\P[status][0][1]=p_{status}[status][1]
\\P[status][0][2]=p_{status}[status][0]
$$


The recurrence is:
$$
\begin{aligned}
P[status][g][i]&= p_{status}[!status][0]*P[!status][g-1][i-1]
\\&~~~~+p_{status}[!status][1]*P[!status][g-1][i-0.5]
\\&~~~~+p_{status}[!status][2]*P[!status][g-1][i+0]
\end{aligned}
$$
**status is 0 or 1. 0 represents white, 1 represent black.**

So the probability that the champion retains the title is 
$$
P_{retain} = \sum_{k=i}^{i_{max}}P[final\_status][g][k]
$$


### b) Dynamic Programming Algorithm

```python
import numpy as np
def findp(ww,wd,wl,bw,bd,bl):
    #create probability status list for white and black
    p_status=[[ww,wd,wl],[bw,bd,bl]]
    
    #create a all 0s grid. row represent g, col represent score
    P= np.zeros([24,49]) #24 rows, 48 cols. each col represent 0.5 score
    color_flag=0 #white
    
    #base case
    P[0][0]=wl
    P[0][1]=wd
    P[0][2]=ww
    
    for row in range(1,24):
        # we have initial the first row because the base case
        
        color_flag=not(color_flag) #change black and white status
        # each element in row
        for col in range(49):
            if col-2>=0:
                #win
                P[row][col]+=p_status[color_flag][0]*P[row-1][col-2]
            if col-1>=0:
                #draw
                P[row][col]+=p_status[color_flag][1]*P[row-1][col-1]
            #loss
            P[row][col]+=p_status[color_flag][2]*P[row-1][col]
            
    return sum(P[24][24:])
   
```



### c) Running Time Analysis

Because we need to win more than [n/2] score to retains the title, 

we need to create a n*(2n+1) grid. And we need to traverse this grid in $O(n (2n+1)) $

And we need to calculate for each element, and the other operation is constant time.

Therefore, the overall time complexity is $O(n^2)$



