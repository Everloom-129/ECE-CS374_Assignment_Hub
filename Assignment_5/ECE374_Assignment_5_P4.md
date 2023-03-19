# ECE374 Assignment 4

03/03/2023

**Group & netid**

*Chen Si         chensi3*

*Jie Wang        jiew5*

*Shitian Yang     sy39*

## T4: Contiguous sums:

![image-20230318194822575](./ECE374_Assignment_5_P4.assets/image-20230318194822575.png)

## Solution:

#### (a) Linear case

In order to realize an ***O(n)*** level decision algorithm, we can't sort the array, for it takes at least ***O(nlogn)*** complexity. 

However, since we don't need to specify the repeated value, we can use ***Select(A[1..n], j)*** algorithm we learnt on the course to minimize the time complexity. 

> ***Select(A[1..n], j):*** return the jth smallest value in an arbitrary array A, worst-case time complexity is ***O(n)**

The following is our algorithm on 

````c++
#include<iostream>

vector<int> LinearContiguousSum(A[1..n]){ 
   
    return false;  
````

The ***Select*** function works as the role of "sorting", as the following diagram shows, if the repetition value exists, it will cover at least one of the there "semi points" in the sorted array. So, we just need to go through the array 3 times, judging whether there exist repetition on the 3 semi points. 

#### (b) Circular case 

The following is our algorithm on 

````c++
#include<iostream>

vector<int> CircularContiguousSum(A[1..n]){ 
   
    return false;  
````