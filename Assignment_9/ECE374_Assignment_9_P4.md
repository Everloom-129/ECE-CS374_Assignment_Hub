# ECE374 Assignment 8 

# T4 SAT-related Problems

04/14/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

## 4. **Let T = {〈M〉|M is a TM that accepts $w^{R}$ whenever it accepts $w$ }  . Show that T is undecidable.**

For the sake of argument, suppose there is an Oracle algorithm **DecideAcceptT** that correctly decides the language T, then we can solve the halting problem as follows:

```pseudocode
DecideHALT(<M,w>):
	Encode the following Turing machine M':
		M'(x):
			run M on input w
			if M halts on input w 
				if x = w or x = w^R:
					return True
				else
					return False
			else
            	return False
	if DecideAcceptT(<M'>)
		return True
	else
		return False
```

​	We prove this reduction correct as follows:

### $\Rightarrow$ Suppose M halts on input w.

- Then M' accepts both w and w^R and rejects all other input strings.
- Since M' accepts w^R whenever it accepts w, DecideAcceptT(<M'>) = True.
- Thus, DecideHALT(<M,w>) = True.

### $\Leftarrow$ Suppose M does not halt on input w.

- Then M' never accepts any input string, as it runs M on input w indefinitely.
- Since M' does not accept any input string, it trivially accepts w^R whenever it accepts w.
  - TODO
- Thus, DecideAcceptT(<M'>) = True. 
- However, this leads to a contradiction, as it implies that DecideHALT(<M,w>) = True, even though M does not halt on input w.

Since the halting problem is known to be undecidable, the existence of the Oracle algorithm DecideAcceptT leads to a contradiction.

Therefore, we conclude that T is undecidable.





## Reference:

- Format is basically based on Lab21 Solution
- [algorithm - Let T = { | M is a TM that accepts $w^R$ whenever it accepts w}. Show that T is undecidable - Stack Overflow](https://stackoverflow.com/questions/50083011/let-t-m-m-is-a-tm-that-accepts-wr-whenever-it-accepts-w-show-that-t) (Yes there was a same question, LOL)
- 