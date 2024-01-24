
E-R model can be transformed into the Relational Data Model.

For each strong entity set E we make a relation schema R which has all the simple attributes of E. Only the simple attributes of a composite attribute is taken

The names of attributes must be changed to work with the relation schema.

Each attribute has its name extended by its domain (data type)

The key of the entity set is the primary key of the relation shcema

Each tuple in R is one entity in E

![[../../Pasted image 20240124095111.png]]


For each weak entity set W with the strong entity E, an independent relation schema R is made with simple attributes, and simple composites of W

Primary key attributes of E are added to R as foreign key attributes. Key of R arises from primary keys of E and partial keys of W.

![[../../Pasted image 20240124095400.png]]

For each 1:1 relationship set R let S and T be the relational schemas that corresponds to the entity set in R. S is selected and primary key T is added to S as a foreign key. if S totally participates in R you should add the primary ket of T to S. All simple attributes and all simple component of composite attributes of R are taken as attributes of S.

![[../../Pasted image 20240124095929.png]]

![[../../Pasted image 20240124100024.png]]
Each department is linked to exactly one employee
No null values for attribute "emp_ID"

- For each binary 1:m-relationship set R let S be the relation schema which corresponds to the entity set participating in R on the m-side. Add to S as foreign key the primary key of relation schema T, which corresponds to the other entity set participating in R. The reason for this is that each entity on the m-side is associated with at most one entity on the 1-side of R. Furthermore, all simple attributes and all simple components of composite attributes of R are taken as attributes of S.

The names of attributes of a foreign key have to be changed sometimes in order to ensure the uniqueness of names in a schema.

- For each binary m:n-relationship set R a new relation schema S is created. Add to S as foreign keys the primary keys of the relation schemas that correspond to the two entity sets participating in R. Their combination forms the primary key of S. Furthermore, all simple attributes and all simple components of composite attributes of R are taken as attributes of S.

- For each n-ary relationship set R with n > 2 a new relation schema S is created. Add to S as foreign keys the primary keys of the relation schemas corresponding to entity sets participating in R. Furthermore, all simple attributes and all simple components of composite attributes of R are taken as attributes of S. The primary key of S is the combination of all foreign keys.

- A new relation schema R is created for each multivalued attribute A. R comprises an attribute corresponding to A and as a foreign key the primary key K of the relation schema which corresponds to the entity set or relationship set containing A as an attribute. The primary key of R is the combination of A and K. If the multivalued attribute is composite, its simple components are added to R.

![[../../Pasted image 20240124100636.png]]

Generalizations are not represented by own relation. It is already expressed by the fact that the key of the common superclass is used as the key of the specialized subclasses.

![[../../Pasted image 20240124100751.png]]

Information on a professor is distributed by two tuples of two relations. Relation of *employees* to a tuple of *professors*.

requires connection of both relations and tuples to complete the information. No inheritance.