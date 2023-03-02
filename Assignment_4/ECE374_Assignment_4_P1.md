# ECE374 Assignment 4

02/28/2023

**Group & netid**

*Chen Si         chensi3*

*Jie Wang        jiew5*

*Shitian Yang     sy39*

## T1: Derive Time complexity

![image-20230228124042088](C:\Users\everloom\AppData\Roaming\Typora\typora-user-images\image-20230228124042088.png)

## Solution:

#### (a) A(n) = A(n-1) + 2n+1;  A(0) = 0

To solve this recurrence relation, we can use the method of iteration.

First, we expand A(n-1) in terms of A(n-2), then we expand A(n-2) in terms of A(n-3), and so on, until we reach the base case A(0).
$$
A(n) = A(n-1) + 2n+1 \\= (A(n-2) + 2(n-1) +1 )+ 2n+1\\ = ...\\ = A(n-n) + 2*(n+n-1+n-2+...+2+1)+ n*1 \\=A(0)+2*\sum_{i=1}^{n} i + n
$$



Now, we use the formula for the sum of the first n natural numbers:

$1 + 2 + ... + n = n(n+1)/2$

Substituting this into the expression above, we get:

$A(n) = 0 + 2n(n+1)/2 + n = n^2 + 2n$

Therefore, the exact solution to the recurrence relation A(n) = A(n-1) + 2n+1, with A(0) = 0, is $A(n) = n^2 + 2n.$

**To justify this solution**, we can use mathematical induction.

Base case: $A(0) = 0^2 + 2*0 = 0$, which satisfies the initial condition.

**Induction hypothesis:** Assume that $A(k) = k^2 + 2k$ for some arbitrary k.

**Induction step:** We want to show that $A(k+1) = (k+1)^2 + 2(k+1)$

By the recurrence relation,

$A(k+1) = A(k) + 2(k+1) + 1  = k^2 + 2k + 2k + 2 + 1 = k^2 + 4k + 3 = (k+1)^2 + 2(k+1)$

Therefore, the induction step holds, and the solution $A(n) = n^2 + 2n$ is verified for all nonnegative integers n.

#### (b) B(n) = B(n − 1) + n(n − 1) − 1; B(0) = 0

To solve this recurrence relation, we can also use the method of iteration.
$$
B(n) = B(n-1) + n(n-1) - 1 \\
= B(n-2) + (n-1)(n-2) - 1 + n(n-1) - 1 \\
= B(n-2) + (n^2 - 3n + 3)\\
= B(n-3) + (n-2)(n-3) - 1 + (n^2 - 3n + 3) = B(n-3) + (n^2 - 5n + 7)\\
= ...\\
= B(0) + Σ(i=1 to n) i(i-1) - 1
$$


Now, we use the formula for the sum of the first n squares:

1^2 + 2^2 + ... + n^2 = n(n+1)(2n+1)/6

And the formula for the sum of the first n natural numbers:

1 + 2 + ... + n = n(n+1)/2

Substituting these into the expression above, we get:

B(n) = 0 + [n(n-1)(2n-1)/6 - 1] = (n^3 - 3n + 2)/3

Therefore, the exact solution to the recurrence relation B(n) = B(n-1) + n(n-1) - 1, with B(0) = 0, is B(n) = (n^3 - 3n + 2)/3.

To justify this solution, we can also use mathematical induction.

Base case: B(0) = (0^3 - 3(0) + 2)/3 = 0, which satisfies the initial condition.

Induction hypothesis: Assume that B(k) = (k^3 - 3k + 2)/3 for some arbitrary k.

Induction step: We want to show that B(k+1) = [(k+1)^3 - 3(k+1) + 2]/3.

B(k+1) = B(k) + (k+1)(k) - 1 (by the recurrence relation) = (k^3 - 3k + 2)/3 + k^2 + k - 1 = (k^3 - 3k + 2 + 3k^2 + 3k - 3)/3 = (k^3 + 3k^2 - k - 1 + 3(k^2 + k))/3 = [(k+1)^3 - 3(k+1) + 2]/3

Therefore, the induction step holds, and the solution B(n) = (n^3 - 3n + 2)/3 is verified for all nonnegative integers n.

#### (c) C(n) = C(n/2) + C(n/3) + C(n/6) + n, find the bigO notation complexity



#### (d) D(n) = D(n/2) + D(n/3) + D(n/6) + n^2

