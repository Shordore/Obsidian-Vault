


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

