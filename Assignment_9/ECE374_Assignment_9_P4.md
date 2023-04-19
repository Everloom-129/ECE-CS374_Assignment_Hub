# ECE374 Assignment 8 

# T4 SAT-related Problems

04/14/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

[toc]

4. Let T = {〈M〉|M is a TM that accepts w R whenever it accepts w }  . Show that T is undecidable.



To show that T is undecidable, we can use a reduction from the Halting Problem (HP), which is a known undecidable problem. The Halting Problem is defined as follows:

Halting Problem (HP) := {<M, w> | M is a Turing machine that halts on input w}

We want to show that if we could decide T, then we could decide the Halting Problem, which would lead to a contradiction since the Halting Problem is undecidable.

Assume that there exists a Turing machine D that decides T. Now, we will construct another Turing machine B that decides the Halting Problem using D.

Given a Turing machine M and an input w, B works as follows:

1. Construct a new Turing machine M' that, on any input x, performs the following steps: a. Simulate M on input w. b. If M halts on input w, then M' checks if x = wR (i.e., x is the reverse of w). If x = wR, accept the input x; otherwise, reject the input x.
2. Run Turing machine D on the description of M' (i.e., <M'>).
3. If D accepts <M'>, it means M' accepts wR if and only if it accepts w. Therefore, M halts on input w, and B accepts <M, w>. If D rejects <M'>, it means M' does not have the property that it accepts wR if and only if it accepts w. Therefore, M does not halt on input w, and B rejects <M, w>.

The Turing machine B decides the Halting Problem using the assumed Turing machine D that decides T. However, this leads to a contradiction since the Halting Problem is undecidable. Therefore, our assumption that there exists a Turing machine D that decides T must be incorrect, and we conclude that the language T is undecidable.