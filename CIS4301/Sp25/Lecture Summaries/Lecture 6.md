
**Lecture Summary: ER Diagrams - Attributes, Roles, Subclasses, Inheritance, and Weak Entity Sets**

  

This lecture continued the discussion on **Entity-Relationship (ER) Diagrams**, covering topics such as **alternative ways to represent attributes**, **roles in relationships**, **subclasses and inheritance**, and **weak entity sets**. The lecture also emphasized the importance of following **notation standards** when creating ER diagrams.

  

**1. Recap of Previous Lecture**

• Defined **entities, entity sets, relationships, and attributes**.

• Discussed **multiplicities** (Many-to-Many, One-to-Many, Many-to-One, One-to-One).

• Explained **attributes on relationships** and the **proper placement of attributes** (e.g., placing “price” on the “sells” relationship instead of “bars” or “beers”).

• Covered **notation rules** for ER diagrams, stressing that incorrect notation in **homework** could result in point deductions.

  

**2. Alternative Ways to Represent Attributes**

• **Instead of placing an attribute on a relationship**, an alternative approach is to create a **new entity set**.

• Example: Instead of adding **“price”** as an attribute to the **“sells”** relationship between **bars and beers**, a new entity **“Prices”** can be introduced.

• This **multi-way relationship** (Bars, Beers, and Prices) ensures that **each bar can sell each beer at a different price**.

  

**3. Roles in Relationships**

• **Roles** are used when an **entity set appears more than once** in a relationship.

• Example: **Married Relationship**

• The **“Drinkers”** entity set appears twice in the **“married”** relationship.

• **Roles** such as **“husband”** and **“wife”** label the edges.

• The relationship **ensures a One-to-One multiplicity** (each husband has one wife, and vice versa).

• Example: **Drinking Buddies Relationship**

• The **“Drinkers”** entity appears twice in the **“buddies”** relationship.

• Roles such as **“Buddy 1”** and **“Buddy 2”** label the edges.

• Since there are **no arrows**, it indicates a **Many-to-Many** relationship (one drinker can have multiple drinking buddies).

  

**4. Subclasses & Inheritance**

  

**Definition**

• **Subclasses** allow modeling of **special cases** within an **entity set**.

• A **subclass** shares attributes of its **superclass** but also has **unique attributes**.

• Example: **Beers have subtypes such as Lagers and Ales**.

• **Ales** may have an additional attribute **“Color”**.

• **Lagers** may have an additional attribute **“Type”**.

  

**Modeling Inheritance in ER Diagrams**

• **Use an “is-a” relationship (triangle notation) to represent subclasses**.

• **Inheritance follows a strict One-to-One relationship**, even though **arrows are not drawn**.

  

**Object-Oriented (OO) vs. ER-Style Representation**

• **Object-Oriented (OO) Style**:

• **A subclass contains all attributes of its superclass**.

• Example: Ales table contains **Name, Calories, and Color**.

• **ER-Style Representation**:

• **Subclasses exist separately** but inherit **keys** from the superclass.

• Example: The **Beers** table contains **Name and Calories**, and the **Ales** table contains **Name and Color**.

• **“Name” propagates down the hierarchy** as the key.

  

**5. Keys in ER Diagrams**

• **Keys** uniquely identify entities within an entity set.

• **Keys are underlined** in ER diagrams.

• Example: **Students Entity Set**

• **Name is NOT a key** (many students can have the same name).

• **UFID is a key** (each student has a unique UFID).

• **SSN is also a key** (each student has a unique SSN).

• **Composite Keys**:

• Sometimes, a key consists of **multiple attributes**.

• Example: **Courses**

• **Department + Course Number** together form a unique key.

• **CIS 4301** is different from **COP 4301**, even if both are course number **4301**.

  

**6. Weak Entity Sets**

  

**Definition**

• **A weak entity set lacks a uniquely identifying attribute** and requires a **strong entity set** for support.

• A weak entity **cannot exist without a strong entity**.

  

**Key Characteristics**

• **Weak entities use “supporting relationships”** to derive their keys.

• **Supporting relationships are always “Many-to-Exactly-One”.**

• **Weak entities are represented with double rectangles**, and supporting relationships are shown with **double diamonds**.

  

**Example: Rooms and Buildings**

• **Room numbers are NOT unique** (there are many “Room 100” at UF).

• **A room’s uniqueness depends on its building**.

• **The “Buildings” entity provides the missing uniqueness by adding the “Building Name”.**

• The **full key for a room is (Building Name, Room Number)**, ensuring uniqueness.

  

**7. Converting ER Diagrams to Tables**

• **Keys propagate down the hierarchy in subclass relationships**.

• **Weak entities must include the key of their supporting strong entity**.

• The next lecture will cover **how to convert ER diagrams into relational database tables**.

  

**8. Summary & Next Steps**

• **Roles allow multiple participation of the same entity in a relationship**.

• **Subclasses (Inheritance) help organize entity sets into hierarchical structures**.

• **Keys ensure entity uniqueness**.

• **Weak entity sets depend on strong entities for unique identification**.

• **Next Lecture:**

• Continue **Weak Entity Sets**.

• **Convert ER Diagrams into relational tables**.

  

This lecture strengthened the understanding of **ER diagrams, keys, and inheritance** while preparing students to **translate conceptual models into relational databases**.