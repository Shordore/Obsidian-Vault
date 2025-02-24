
**1. DBMS Fundamentals**

  

**a. Definition & Purpose**

• **Database vs. File System**:

• A **file system** stores data in separate files with little built-in structure.

• A **DBMS** centralizes data management, ensuring **data integrity**, **concurrency control**, **recovery**, and **security**.

  

**b. DBMS Architecture**

• **Components**:

• **Query Compiler**:

• **Parser**: Checks syntax; creates a parse tree.

• **Preprocessor**: Performs semantic checks and converts SQL to an algebraic form.

• **Optimizer**: Reorders operations for efficiency.

• **Execution Engine**: Executes the optimized query plan.

• **Index/Record Manager**: Manages data storage structures (e.g., B-trees).

• **Buffer Manager**: Loads pages into memory to reduce disk I/O.

• **Storage Manager**: Reads/writes physical data pages.

• **Query Flow**:

User SQL → Parser → Preprocessor → Optimizer → Execution Engine → (Buffer, Index, Storage Managers) → Result

  

**c. ACID Properties**

• **Atomicity**: Transactions are “all or nothing.”

• **Consistency**: Transactions move the database from one valid state to another.

• **Isolation**: Concurrent transactions don’t interfere.

• **Durability**: Once committed, transactions persist even after a crash.

**2. ER Diagrams**

  

**a. Basic Elements**

• **Entity**: A real-world object (e.g., Traveler, TravelAgent).

• **Attribute**: A property of an entity (e.g., name, ssn).

• **Relationship**: How entities are related (e.g., Booking, Likes).

• **Key**: An attribute (or set) that uniquely identifies an entity.

• **Multiplicity**:

• **One-to-One**: Each entity relates to at most one in the other set.

• **Many-to-One**: Many entities relate to one entity.

• **Many-to-Many**: Entities in both sets can relate to many.

• **Weak Entity**: Cannot be uniquely identified without a supporting (owner) entity.

• **Subclasses**: Specialized entities that inherit from a superclass.

  

**b. Design Principles**

• **Avoid Redundancy**: Use entities only when necessary.

• **Entity vs. Attribute**: Decide if an item should be a separate entity or just an attribute.

• **Use of Weak Entities**: Apply only when no global key exists.

  

**c. Practice Tips**

• Draw or analyze ER diagrams from narratives.

• Check relationship types (e.g., many-to-one vs. many-to-many).

**3. Converting ER Diagrams to the Relational Model**

  

**a. Conversion Rules**

• **Entity Set → Table**: Each entity becomes a table; attributes become columns; the key becomes the primary key.

• **Many-to-Many Relationships → New Table**: Create a relation that holds the keys of both participating entities.

• **Many-to-One Relationships → Foreign Key**: Place the key of the “one” side into the table on the “many” side.

• **Weak Entity Sets**: Combine the supporting entity’s key with the weak entity’s partial key.

• **Subclasses**:

• **Object-Oriented**: One table per class (with repeated superclass key).

• **ER-Style**: One table per subclass (include superclass key).

• **Using NULLs**: One table for all with nullable subclass fields.

  

**b. When to Combine**

• In many-to-one relationships without extra attributes, you can sometimes merge the entities into one table.

**4. SQL Language (SQL I)**

  

**a. DDL (Data Definition Language) Commands**

• **CREATE TABLE**: Define a new table, its attributes, data types, primary keys, and default values.

```
CREATE TABLE TravelAgent (
    name VARCHAR(50) PRIMARY KEY,
    years_experience INT NOT NULL,
    phone VARCHAR(15) NOT NULL
);
```

  

• **ALTER TABLE**: Modify an existing table (e.g., add/drop columns).

```
ALTER TABLE TravelAgent ADD email VARCHAR(100);
```

  

• **DROP TABLE**: Remove a table.

```
DROP TABLE TravelAgent;
```

  

  

**b. DML (Data Manipulation Language) Commands**

• **INSERT**: Add rows to a table.

```
INSERT INTO TravelAgent (name, years_experience, phone)
VALUES ('Alice Brown', 12, '123-456-7890');
```

  

• **SELECT-FROM-WHERE**: Query data.

```
SELECT name, phone FROM TravelAgent WHERE years_experience > 10;
```

• **Pattern Matching**:

```
SELECT name FROM Traveler WHERE name LIKE 'A%';
```

  

• **Aliases & Expressions**:

```
SELECT name, Salary * 1.10 AS NewSalary FROM Employee;
```

  

  

**c. Data Types & Constraints**

• **Data Types**: INT, CHAR(n), VARCHAR(n), DATE, FLOAT

• **Primary Key vs. UNIQUE**:

• Primary keys uniquely identify rows and disallow NULL.

• UNIQUE allows one NULL in some systems.

  

**d. Practice**

• Write queries with multiple conditions, pattern matching, and use the proper DDL commands to create and modify tables.

**5. Relational Algebra**

  

**a. Core Operations**

1. **Selection (σ)**:

• Filters rows based on a condition.

• Example:

1. **Projection (π)**:

• Selects specific columns (removes duplicates).

• Example:

1. **Cartesian Product (×)**:

• Combines every row of one relation with every row of another.

• Example:

1. **Natural Join (⋈)**:

• Joins two relations on all common attributes (removing duplicates).

• Example:

\[

\text{Traveler} \bowtie \text{Booking}

\]

1. **Theta Join (⋈₍C₎)**:

• A Cartesian product followed by a selection on condition .

• Example:

\[

\text{Traveler} \bowtie_{Traveler.ssn = Booking.traveler\_ssn} \text{Booking}

\]

1. **Renaming (ρ)**:

• Renames a relation and/or its attributes.

• Example:

  

**b. Set Operations**

• **Union (∪)**: Combines tuples from two relations.

• **Intersection (∩)**: Returns tuples common to both relations.

• **Difference (−)**: Returns tuples in one relation but not the other.

• **Note**: Both operands must have the same schema.

  

**c. Building Complex Expressions**

• **Chaining Operators**:

• Use parentheses to control precedence.

• **Precedence**: σ, π, ρ (highest) → ×, ⋈ → ∩ → ∪, − (lowest)

• **Expression Trees**: Visual representations where leaves are base relations and internal nodes are operations.

  

**d. Examples**

• **Query 1**: List traveler names and booked trip IDs:

\[

\pi_{\text{Traveler.name},\ \text{Booking.trip\_id}}(\text{Traveler} \bowtie \text{Booking})

\]

• **Query 2**: Find names of travelers who booked trip ID 201:

\[

\pi_{\text{Traveler.name}}(\sigma_{\text{Booking.trip\id}=201}(\text{Traveler} \bowtie{Traveler.ssn=Booking.traveler\_ssn} \text{Booking}))

\]

• **Query 3**: Find travel agent(s) for traveler ‘Laura White’:

\[

\pi_{\text{Booking.agent}}(\sigma_{\text{Traveler.name}=‘Laura White{\prime}}(\text{Traveler} \bowtie_{Traveler.ssn=Booking.traveler\_ssn} \text{Booking}))

\]

  

**e. Practice**

• Manually work through small examples to understand how each operator transforms your data.

**6. Integration and Big Picture**

• **ER Diagrams → Relational Schema → SQL Implementation**:

• Understand how entities and relationships convert into tables (with keys and constraints).

• **Relational Algebra as the Foundation for SQL**:

• Most SQL queries are internally translated into relational algebra expressions.

• **Key Terminology**:

• Know definitions for **weak entity**, **theta join**, **ACID**, **primary key vs. unique**, etc.

**Final Study Tips**

1. **Revisit Homework & Activity Solutions**: Practice SQL queries and relational algebra expressions.

2. **Do Manual Examples**: Work through small relation examples to see how operators work.

3. **Understand the Big Picture**: Connect ER modeling with schema conversion, SQL DDL/DML, and relational algebra.

4. **Memorize Key Notations & Definitions**: Ensure you are comfortable with the symbols (σ, π, ×, ⋈, ρ, ∪, ∩, −) and their meanings.

Keep this cheat sheet handy as you review the material. Good luck on your exam!