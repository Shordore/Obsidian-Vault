


Sample Space
	All possible outcomes in an experiment organized in a set.
	Denoted by S

Sample Point
	Each outcome in S is called a Sample Point, or element, or member of S
	When a point belongs in S we say $x \in S$
	![[Pasted image 20240826144855.png]]
	![[Pasted image 20240826145126.png]]
	

Event
	subset of a sample space(S)
	if A is a subset of S then $A \subseteq S$

Empty set
	Denoted by $\emptyset$
	$\emptyset \subseteq S$

$S \subseteq S$ (Duh)

Set Equality
	Sets A and B are equal iff $A \subseteq B$ and $B \subseteq A$
	One common way to show set A and B equal is to prove that any element in A must be in B and vice versa.

Complement
	Complement of event A is denoted by $A^\prime$ or $A^\complement$ 
	EX
		![[Pasted image 20240826151902.png]]

Union
	event containing all elements belonging to A, B, or both
	Denoted by $A \cup B$
	![[Pasted image 20240826205649.png]]

Intersection
	Event containing all elements that are found in both A, and B.
	Denoted by $A \cap B$
	![[Pasted image 20240826205900.png]]

Mutually Exclusive
	aka disjoint
	A and B are disjoint if $A \cap B = \emptyset$
	a collection of events are disjoint if $A_i \cap A_j = \emptyset$ for all $i \not = j$ 

For event A
	$A \cap \emptyset = \emptyset$
	$A \cap A^\prime = \emptyset$

Set Difference
	Events that are in A but not B
	$A / B = A \cap B^\prime$
	 ![[Pasted image 20240826215040.png]]
	![[Pasted image 20240826215114.png]]

Basic Properties
	Demorgan's
		$(A \cup B$)$^\prime$ = $A^\prime \cap B^\prime$
		$(A \cap B$)$^\prime$ = $A^\prime \cup B^\prime$
	Distributive
		$A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$ 
		$A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$ 
	(i)
		$(A^\prime)^\prime = A$
	(ii)
		$A \cup A^\prime = S$
	(iii)
		$A \cup B = B \cup A$
		$A \cap B = B \cap A$
	(iv)
		$A \cup (B \cup C) = (A \cup B) \cup C$
		$A \cap (B \cap C) = (A \cap B) \cap C$
	![[Pasted image 20240827194512.png]]


Multiplication Rule
	an action that can be performed in $n_1$ ways, if for each way, a second operation caan be performed in $n_2$ ways, then two operations can be performed in $n_1 * n_2$ ways.
	![[Pasted image 20240827195255.png]]
	![[Pasted image 20240827195608.png]]


Factorial
	Given by:
	$n! = n(n-1) ... (2)(1)$
	$0! = 1$
	
Theorem
	Number of permutations of n objects with r length
	$nPr = \frac {n1} {(n-r)!}$ 
	Proof
		![[Pasted image 20240904150937.png]]
	![[Pasted image 20240904150956.png]]

Theorem
	Number of distinct permutations of n objects of which $n_k$ of a $k_th$ kind
		$\frac {n!} {n_1 ! n_2 ! ... n_k !}$
		![[Pasted image 20240904151319.png]]

Combination
	Subset of n distinct objects
	![[Pasted image 20240904151459.png]]

Theorem
	Number of combinations of distinct objects taken r at a time
		$n \choose {r}$ $= \frac {n!} {r!(n-r)!}$ 
		![[Pasted image 20240904151722.png]]


<p style = "font-size: 30px;"> Probability of an Event </p>
The probability of an outcome is the proportion of times the outcome would occur in a long run of observations

Axioms of Probability
	A is an event. P is a probability function if:
		(i) $0 \leq P(A) \leq 1$
		(ii) P(S) = 1
		(iii) if $A_1, A_2, A_3, ...$ is a sequence of mutually exclusive events, then
			$P(A_1 \cup A_2 \cup A_3 \cup ...) = \sum_{i = 1}^{\infty} P(A_i)$ 

Theorem
	S has N different equally likely outcomes, exactly n of these outcomes correspons to event A, then prob of event A is:
		$P(A) = \frac {n} {N}$
		![[Pasted image 20240904153123.png]]


Theorem
	If $A \subseteq B$ then $P(A) \leq P(B)$
	Proof
		If $A \subseteq B$ then
		$0 \leq P(B\cap A^\complement) = P(B) - P(B\cap S) = P(B) - P(A)$



Theorem
	If A and B are two events
		$P(A\cup B) = P(A) + P(B) - P (A\cap B)$
	If A and B are mutually exclusive then
		$P(A\cup B) = P(A) + P(B)$
	![[Pasted image 20240905000036.png]]
	![[Pasted image 20240905000116.png]]


Theorem
	If A and $A^\prime$ are complementary events, then
		$P(A^\prime) = 1 - P(A)$ 
	![[Pasted image 20240904154114.png]]

Theorem
	if $A \subseteq B$, then $P(A) \leq P(B)$
	![[Pasted image 20240904154226.png]]


<p style="font-size: 30px;"> Conditional Probability and Independence</p>

Conditional Probability
	A and B are events. conditional probability of B given A 
	Denoted as $P(B|A)$
	$P(B|A) = \frac {P(A\cap B)} {P(A)}$
	![[Pasted image 20240906110244.png]]

Product Rule
	$P(A\cap B) = P(A)P(B|A)$
	![[Pasted image 20240906110328.png]]

Independent Events
	A and B are independent iff
		$P(B|A) = P(B)$ or $P(A|B) = P(A)$
		provided conditional probabilities exist, otherwise they are dependen
	Two event are independent iff
		$P(A\cap B) = P(A)P(B)$
	Suppose A and B are independent, then
		(i) A and $B^\prime$ are independent
		(ii) $A^\prime$ and B are independent
		(iii) $A^\prime$ and $B^\prime$ are independent
	![[Pasted image 20240906111415.png]]

Mutually Independent
	collection of events are mutually independent if
		$P(A_{i_1}\cap ... \cap A_{i_k}) = P(A_{i_1})...P(A_{i_k})$



<p style="font-size: 30px;"> Baye's Rule </p>
Theorem of total probability
	$P(A) = \sum_{i = 1}^{k} P(B_i \cap A) = \sum_{i = i}^k P(B_i)P(A|B_i)$ 
	![[Pasted image 20240917150113.png]]
	![[Pasted image 20240917150128.png]]

Baye's Rule
	if constitutes a partition of sample space, then for any event A in S such that P(A) $\not =$ 0
	$P(B_j|A) = \frac {P(B_j \cap A)}{P(A)} = \frac {P(B_j)P(A|B_j)}{\sum_{i = 1}^k P(B_i)P(A|B_i)}$
	for j = 1,2,...,k
	![[Pasted image 20240917150547.png]]
	![[Pasted image 20240917150604.png]]


<p style="font-size: 30px;"> Random Variables</p>

Random Variable
	A function from S to real numbers
	Denoted by capital letters and value it takes denoted by lowercase letters

Discrete sample space
	If S contains finite number or infinite number of elements, it is called a discrete sample space.

Discrete random variable
	Random variable X is called such if its set of possible outcomes is countable
	![[Pasted image 20240917151904.png]]

Probability mass function
	pmf of discrete random variable X is given by
	$f_x (x) = P(X = x)$
	for all $x \in R$
	function $f_x (x)$ is a pmf of discrete random variable X iff:
		(i) $f_x (x) \geq 0$ for all $x \in R$
		(ii) $\sum_x f_x (x) = 1$
	![[Pasted image 20240917153235.png]]

Cumulative distribution function
	cdf is a discrete random variable X given by
			$F(x) = P(X \leq x) = \sum_{t \leq x} f(t)$
	![[Pasted image 20240917153410.png]]

Continuous sample space
	if S contains an infinite number of outcomes it is called continuous

Continuous random variable
	X is called continuous if its set of outcomes is infinite

Probability density function
	pdf for X if:
		$P(a \leq X \leq b) = \int_{a}^{b} f_x (x)dx$
		for all R $a \leq b$
	A function is a pdf iff
		(i)$f_x (x) \geq 0$ for all $x \in R$
		(ii)$\int_{-\infty}^\infty f_x (x) dx = 1$

Cumulative distribution function
	$F(x) = P(X \leq x) = \int_{-\infty}^x f_x (t)dt$
	for all $x \in R$
	![[Pasted image 20240917185343.png]]


<p style = "font-size: 30px;"> Joint Probability Distributions</p>

Joint pmf
	function is a joint pmf of X and Y if
	$P(X = x, Y = y) = f_x,y (x,y)$
	for all $x,y \in R$

Joint pdf
	$P[(X,Y) \in A] = \int \int_A f_{X,Y} (x,y) dx dy$ 