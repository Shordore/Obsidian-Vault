
**Summary of “ER Conversion” PowerPoint Presentation**

  

This presentation focuses on **converting ER diagrams into relational database schemas**, covering key concepts in the **Relational Model, entity and relationship conversion, weak entities, redundancy, and inheritance**.

  

**Main Topics Breakdown**

  

**1. Introduction to the Relational Model**

• A **relational database** consists of **relations (tables)**.

• Each relation has:

• **Relation Name**

• **Attribute List**

• **Attribute Types**

• **Example Schema:**

  

Beers(name: String, calories: Integer)

  

  

• **Database Schema**: The set of all relation schemas in the database.

  

**2. Why Use Relations?**

• **Advantages**:

• Simple model

• Matches natural data representation

• Works well with **SQL**

• **Entity-Relationship Mapping**:

• **Entity Set → Relation (Table)**

• **Attributes → Columns**

• **Relationship → A table (contains primary keys from related entity sets)**

  

**3. Converting ER Diagrams to Relations**

  

**Mapping Entities**

• **Entity Sets** are directly converted into **Relations (Tables)**.

• Example:

  

Beers(name: String, brewer: String)

  

  

  

**Mapping Relationships**

• A **relationship** between two entity sets is mapped as a separate relation, containing:

• **Primary keys** from the related entity sets.

• **Attributes specific to the relationship**.

• Example:

  

Likes(drinker: String, beer: String)

  

  

• **Many-One relationships** can sometimes be **merged into one relation**.

  

**4. Combining Relations**

• **Many-to-One Relationship Conversion**:

• Example:

  

Drinkers(name: String, address: String)

Favorite(drinker: String, beer: String)

  

  

• Can be combined into:

  

Drinkers_Favorite(name: String, address: String, favorite_beer: String)

  

  

• **Many-to-Many Relationship Conversion**:

• Example:

  

Drinkers(name: String, address: String)

Likes(drinker: String, beer: String)

  

  

• Can be combined into:

  

Drinkers_Likes(name: String, address: String, likes_beer: String)

  

  

• **Issues with Combining Relations**:

• **Redundancy**: Some attributes may be repeated unnecessarily.

• **Normalization** is used to **reduce redundancy**.

  

**5. Handling Weak Entity Sets**

• **Definition**: Weak entity sets **do not have a unique key** and depend on a **strong entity set** for identification.

• **Conversion Strategy**:

• A relation for a weak entity set must include:

• **Attributes for its key** (which may include foreign keys).

• **Non-key attributes**.

• **Example (Buildings & Rooms)**:

  

Buildings(bldg_name: String, address: String)

Rooms(bldg_name: String, number: Integer, seats: Integer)

  

  

• **Supporting Relationships**:

• Often redundant unless they contain **additional attributes**.

• Example redundant relation:

  

Located_In(bldg_name: String, room_number: Integer)

  

**6. Subclass Relations (Inheritance)**

• **Inheritance in ER Diagrams → Relational Model**

• **Three Ways to Convert Subclasses**:

1. **Object-Oriented Approach**:

• One relation per **subclass** (includes all attributes).

2. **ER Style Approach**:

• One relation per **each subclass**, containing:

• **Primary key**

• **Subclass-specific attributes**

3. **Using NULLs**:

• One relation that includes **all attributes**, but non-relevant attributes are **NULL**.

• **Example (Beer Subclass “Ales”)**:

• **Object-Oriented:**

  

Beers(name: String, brewer: String)

Ales(name: String, color: String)

  

  

• **ER-Style:**

  

Beers(name: String, brewer: String)

Ales(name: String, color: String)

  

  

• **Using NULLs:**

  

Beers(name: String, brewer: String, color: String NULLABLE)

  

**Conclusion**

  

This presentation covers **how ER models are converted into relational schemas** using:

1. **Direct entity-to-relation mapping**.

2. **Handling relationships as separate tables or merging them**.

3. **Dealing with weak entity sets**.

4. **Handling inheritance through different conversion strategies**.

  

Would you like a **step-by-step SQL schema example** based on these conversions? 🚀