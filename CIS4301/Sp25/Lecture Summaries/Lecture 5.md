
**Lecture Summary: ER Diagrams, High-Level Database Design, and Multiplicities**

  

This lecture focused on **Entity-Relationship (ER) diagrams**, their purpose in **high-level database design**, and **multiplicity relationships** between entities. It also included general announcements about **TA grading assignments**, the **CISE Career Fair**, and an **advertisement for the Open Source Club**.

  

**1. Announcements**

• **TA Grading Assignments**: Each student has been assigned a TA responsible for grading their homework and assignments. The assignments are available on a spreadsheet.

• **CISE Career Fair**: Encouragement to attend, network with recruiters, and explore internship/job opportunities.

• **Open Source Club Advertisement**: Information about an upcoming **GBM** and the club’s focus on **open-source projects**.

  

**2. Recap of Previous Lecture**

• **Databases and DBMS**:

• **Defined databases and database management systems (DBMS)**.

• **Explored DBMS architecture** and its components.

• **Reviewed the distinction between schema and data**:

• **Schema**: The **structure** of tables (e.g., table names, column names, data types).

• **Data**: The **actual entries** stored in the tables.

• **Data Models**:

• **Relational Model**: Uses **tables** to store data.

• **Other Models**:

• **Free-text model** (Human-readable).

• **Semi-structured model** (Uses XML).

• **Graph model** (Uses nodes and edges).

• The **relational model** is the **most widely used** in commercial databases.

  

**3. Introduction to ER Diagrams**

  

**Purpose of ER Diagrams**

• **ER diagrams provide a conceptual framework for database design**.

• They help developers **visualize relationships between data entities** before implementing them as tables.

• **Steps to database design**:

1. **Sketch a high-level design** (ER diagram).

2. **Convert it into relational tables**.

3. **Implement it in a relational DBMS**.

  

**Key Components of ER Diagrams**

• **Entity**: Represents a **thing** or **object** (e.g., a bar, a student, a beer).

• **Entity Set**: A **collection of similar entities** (e.g., all bars in a city).

• **Attributes**: Properties of an entity (e.g., a bar has a **name, address, and license**).

• **Relationships**: Define **associations** between two or more entities (e.g., a bar **sells** beers).

• **Multiplicities**: Define **how many** entities in one set are related to entities in another set.

  

**4. ER Diagram Notation**

• **Entities** → Represented by **rectangles**.

• **Attributes** → Represented by **ovals** connected to an entity.

• **Relationships** → Represented by **diamonds** connecting entities.

• **Multiplicities** → Indicated using **arrows**.

  

**5. Example ER Diagram: Bars, Beers, and Drinkers**

• **Entities**:

• **Bars**: Each bar has **a name, address, and license**.

• **Beers**: Each beer has **a name and calorie count**.

• **Drinkers**: Each drinker has **a name and address**.

• **Relationships**:

• **Bars “sell” beers**.

• **Drinkers “frequent” bars**.

• **Drinkers “like” beers**.

  

**Sample ER Diagram Interpretation**

• **Bars sell beers** (Many-to-Many).

• **Drinkers frequent bars** (Many-to-Many).

• **Drinkers like beers** (Many-to-Many).

  

**6. Multiplicities in Relationships**

  

**Types of Multiplicities**

1. **Many-to-Many**:

• Example: **Bars sell beers**, and beers are sold by multiple bars.

• **Notation**: No arrows.

2. **Many-to-One**:

• Example: **Drinkers have a favorite beer** (One beer can be a favorite of multiple drinkers, but each drinker has only one favorite).

• **Notation**: Arrow pointing to the **one side**.

3. **One-to-Many**:

• Example: **Brewers make beers** (One brewer can make many beers, but each beer is made by only one brewer).

• **Notation**: Arrow pointing to the **one side**.

4. **One-to-One**:

• Example: **Each bar has one best-selling beer**.

• **Notation**: Arrows pointing **both ways**.

  

**7. Multi-Way Relationships**

• **Most relationships are between two entities (binary)**.

• **Multi-way relationships** involve **three or more** entities.

• **Example**:

• **Drinkers prefer certain beers at certain bars**.

• Instead of **separate relationships**, a **single “preferences” relationship** can link **drinkers, bars, and beers**.

  

**8. “Exactly One” vs. “At Most One” Multiplicities**

• **Exactly One (Rounded Arrow)**:

• A **user must have a password** (each user has exactly one password).

• **At Most One (Regular Arrow)**:

• A **beer may or may not be a bestseller** for a manufacturer.

  

**9. Attributes on Relationships**

• **When should an attribute belong to a relationship instead of an entity?**

• **Example: Price of a Beer at a Bar**

• **Wrong Approach**:

• If **“price” is an attribute of bars**, all beers at the bar must have the same price.

• If **“price” is an attribute of beers**, all bars must sell the beer at the same price.

• **Correct Approach**:

• **Attach “price” to the “sells” relationship** to allow each bar to sell each beer at different prices.

  

**10. Converting ER Diagrams into Relational Models**

• **Future Lectures**:

• Learn to **convert ER diagrams into database tables**.

• Implement designs in a **relational DBMS**.

  

**11. Summary & Next Steps**

• **ER diagrams** help in **high-level database design**.

• **Entities**, **attributes**, and **relationships** define how data is **structured**.

• **Multiplicities (Many-to-Many, Many-to-One, One-to-One)** define **relationships between data**.

• **“Exactly One” vs. “At Most One”** ensure **data integrity**.

• **Attributes on relationships** help resolve **design conflicts**.

  

**Next Lecture:**

• **Continue ER diagrams**.

• **Learn how to convert ER diagrams into relational models**.

  

This lecture provided **a foundation for database design using ER diagrams**, focusing on **relationships, multiplicities, and attributes**. Future sessions will explore **converting ER diagrams into database tables** and implementing them in **relational database management systems (RDBMS)**.