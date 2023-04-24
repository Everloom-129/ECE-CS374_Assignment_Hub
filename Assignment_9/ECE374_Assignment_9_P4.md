# ECE374 Assignment 9

04/14/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

## 4. Decidability Problem

>  **Let T = {〈M〉|M is a TM that accepts $w^{R}$ whenever it accepts $w$ }  . Show that T is undecidable.**

For the sake of argument, suppose there is an Oracle algorithm **DecideAcceptT** that correctly decides the language T, then we can solve the **halting problem** as follows:

```pseudocode
DecideHALT(<M,w>):
	Encode the following Turing machine M_Q:
		M_Q(x):
			run M on input w
			# if M halts on input w
			if x = 01 or x = 10:
				return True
			else
				return False
	if DecideAcceptT(<M_Q>):
		return True
	else
		return False
```

​	We prove this reduction correct as follows:

### $\Rightarrow$ Suppose M halts on input w.

- Then M_Q accepts both 01 and 10, while rejecting all other input strings.
- So DecideAcceptT(<M_Q>) accepts the encoding <M_Q>
- Thus, DecideHALT(<M,w>) correctly accepts the encoding <M, w >

### $\Leftarrow$ Suppose M does not halt on input w.

- Then M_Q diverges on *every* input string x
- In particular, M_Q does not accept  $w^{R}$ or $w$
  - So DecideAcceptT rejects the encoding <M_Q>
  - So DecideHALT correctly rejects the encoding <M,w>


In both cases, DecideHALT is correct. However, since the **halting problem is known to be undecidable,** the existence of the Oracle algorithm DecideAcceptT leads to a contradiction.

Therefore, we conclude that T is undecidable.





## Reference:

- Format is basically based on Lab21 Solution

- [algorithm - Let T = { | M is a TM that accepts $w^R$ whenever it accepts w}. Show that T is undecidable - Stack Overflow](https://stackoverflow.com/questions/50083011/let-t-m-m-is-a-tm-that-accepts-wr-whenever-it-accepts-w-show-that-t) (Yes there was a same question, LOL)

  



