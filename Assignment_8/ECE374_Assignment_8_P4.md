# ECE374 Assignment 8

04/14/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

## T4 SAT-related Problems

#### (a) Stingy SAT: at most k true variables

Stingy SAT is the following problem: given a set of clauses (each a disjunction of literals) and an integer k, find a satisfying assignment in which **at most k variables are true,** if such an assignment exists. 

**Prove that stingy SAT is NP-hard.**

#### Intuition:

Since there is a **=< k limitation** on the SAT problem, we can use **Vertex Cover** to show it is NP-hard.

> Vertex Cover problem : given an undirected graph G = (V, E) and an integer k, find a subset of vertices V' ⊆ V such that |V'| <= k and e
>
> very edge in E has at least one endpoint in V'.

We will now construct an instance of the Stingy SAT problem from the given instance of the Vertex Cover problem:

1. For each vertex v in V, create a corresponding Boolean variable x_v in the Stingy SAT instance.
2. For each edge (u, v) in E, create a clause (x_u OR x_v) in the Stingy SAT instance.

Now, we have a set of clauses and an integer k for the Stingy SAT problem.

We claim that G has a vertex cover of size k or smaller if and only if the constructed set of clauses has a satisfying assignment in which at most k variables are true.

Proof:

- If G has a vertex cover V' of size k or smaller, assign each variable x_v to true if and only if the corresponding vertex v is in the vertex cover V'. This will satisfy all clauses because for each edge (u, v) in E, at least one of x_u or x_v will be true, as at least one of the vertices u or v is in the vertex cover V'. Since |V'| <= k, at most k variables are true.
- If the constructed set of clauses has a satisfying assignment in which at most k variables are true, we can form a vertex cover V' by including vertex v in V' if and only if the corresponding variable x_v is true. This set V' is a vertex cover because for each edge (u, v) in E, the clause (x_u OR x_v) is satisfied, meaning that at least one of x_u or x_v is true, and thus, at least one of the vertices u or v is in V'. Since at most k variables are true, |V'| <= k.

The reduction from Vertex Cover to Stingy SAT can be done in polynomial time. Since Vertex Cover is NP-complete, this reduction shows that Stingy SAT is NP-hard.

#### Reduction

```python

```

#### Time complexity



#### (b) Double SAT problem

The Double SAT problem asks whether a given satisfiability problem has at least two different satisfying assignments. 

- For example, the problem $ \{\{v_1, v_2\}, \{\overline{v_1}, v_2\}, \{\overline{v_1},\overline{v_2}\}\} $is satisfiable,but has only one solution $(v_1 =F,v_2 =T)$. 

- In contrast, $\{\{v_1, v_2\}, \{\overline{v_1},\overline{v_2}\}\} $ has exactly two solutions. 

**Show that Double-SAT is NP-hard.**

#### Intuition:



#### Reduction

```python

```

#### Time complexity

To show that Double-SAT is NP-hard, we can reduce the classic 3-SAT problem to it. 

- 3-SAT problem
  -  given a set of clauses (each a disjunction of exactly three literals), determine whether there exists a satisfying assignment of Boolean values to the variables.

Given an instance of 3-SAT with a set of clauses, we can construct an instance of Double-SAT as follows:

1. Take the set of clauses from the 3-SAT instance and use them as the set of clauses for the Double-SAT instance.
2. Add a new variable z to the Double-SAT instance.
3. For each clause (x OR y OR w) in the 3-SAT instance, replace it with two clauses in the Double-SAT instance: (x OR y OR w OR z) and (x OR y OR w OR ¬z). This ensures that if the original clause is satisfiable, it remains satisfiable with the addition of z or ¬z.

Now, we claim that the 3-SAT instance is satisfiable if and only if the constructed Double-SAT instance has at least two different satisfying assignments.

Proof:

- If the 3-SAT instance is satisfiable, there exists a satisfying assignment of Boolean values to the variables. We can use this assignment for the Double-SAT instance and set z to both true and false to get two different satisfying assignments. This is because adding z or ¬z to each clause will not affect the satisfiability of the clause, as it was already satisfied by the 3-SAT assignment.
- If the Double-SAT instance has at least two different satisfying assignments, we can find a satisfying assignment for the 3-SAT instance by ignoring the variable z. Since the clauses in the Double-SAT instance were derived from the 3-SAT clauses with the addition of z or ¬z, we know that the assignment will still satisfy the original 3-SAT clauses.

The reduction from 3-SAT to Double-SAT can be done in polynomial time. Since 3-SAT is NP-complete, this reduction shows that Double-SAT is NP-hard.