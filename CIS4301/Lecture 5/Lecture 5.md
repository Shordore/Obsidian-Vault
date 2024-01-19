
Disjoint/overlapping specialization:
	All sublclasses of a superclass are pairwise disjoint/overlapping.

Total Specialization:
	the superclass explicit elements is given by the union of its subclasses.
	See: Partial Specialization.

Main steps for design an E-R diagram:
	Identify weak entity sets
	Draw weak entity sets
	Identify key attributes of weak entity sets
	Draw key attributes of weak entity sets
	identify identifying weak relationship sets
	Draw identifying relationship sets
	Identify attributes of identifying relationship sets
	Insert cardinalities

E.X. Gym Management:	![][[Pasted image 20240119094445.png]]
	
Draw weak entity sets:	![[Pasted image 20240119094254.png]]

Identify key attributes of weak entity sets:
![[Pasted image 20240119094515.png]]
	
Draw said attributes:
![[Pasted image 20240119094405.png]]
	
Identify relationship sets:
![[Pasted image 20240119094610.png]]

Draw relationship sets:	
![[Pasted image 20240119094638.png]]

Identify attributes of identifying relationship sets:
![[Pasted image 20240119094759.png]]

Draw attributes of identifying relationship sets:	
![[Pasted image 20240119094836.png]]

Insert cardinalities:		
![[Pasted image 20240119094859.png]]


**Relational Data Model**
	Commercial DBMSs including Oracle, Informix, SQL Server, Sybase, DB2, as well as other are based on the relational data model.
	Main Reasons for the success of the relational data model:
		Utilizes a "flat" table to represent relations between the data.
![[Pasted image 20240119095336.png]]
		Set oriented:
			processes data by set rather than record oriented processing (*Hierarchal model, network model*)
		Easy to understand by an unskilled user.
		Good performance for alphanumeric databases
		Existence of a mature, formal theory (*What????*)
		
