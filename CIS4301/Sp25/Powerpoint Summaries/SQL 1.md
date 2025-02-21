

**1. Purpose of ER Diagrams and Transition to SQL**

• **ER Diagrams** (Entity-Relationship Diagrams) are used to **sketch** and **brainstorm** how a database should be structured before actually implementing tables. After finalizing the ER diagram (entities, relationships, attributes), you **convert** it into relational tables.

• Once you’ve mapped an ER diagram to a relational schema, you move on to defining those tables and their constraints in an actual **DBMS** (such as MariaDB).

  

**Key Point**: _Design first (ER Diagram), then translate into the relational model (tables), finally implement in SQL._

**2. What is SQL and Why Use It?**

• **SQL (Structured Query Language)** is a **high-level language** focused on **what** data to retrieve or manipulate rather than **how** to do so. It frees developers from worrying about the underlying storage details, indexes, or file structures.

• Because SQL is set-oriented, it can query or update large sets of rows at once. The DBMS’s **query optimizer** determines the best way to execute those operations.

**3. DDL vs. DML Commands**

  

SQL statements are broadly categorized into two groups:

1. **Data Definition Language (DDL)**

• **CREATE**: Create databases or tables (e.g. CREATE TABLE …).

• **ALTER**: Modify existing table structures (e.g. add or drop a column).

• **DROP**: Remove tables or databases entirely.

These operations define or change the **schema** (structure) of the database.

1. **Data Manipulation Language (DML)**

• **SELECT**: Query or retrieve data from existing tables.

• **INSERT**: Add new rows (records) into a table.

• **UPDATE**: Modify existing rows in a table.

• **DELETE**: Remove rows from a table.

These operations work with the **contents** (rows/records) of tables rather than altering the schema.

  

**Key Point**: _DBAs (database administrators) often use DDL to set up the schema. Application developers or end users more frequently use DML to query and manipulate data._

**4. Creating Tables and Specifying Data Types**

  

When converting your ER diagram to tables, you choose **appropriate data types** for each column. Common SQL data types:

• **CHAR(n)**: Fixed-length character field of length n; short strings get padded with spaces.

• **VARCHAR(n)**: Variable-length string up to length n; no extra padding.

• **INT** (or INTEGER): For integer (numeric) data.

• **FLOAT/REAL**: For floating-point numbers.

• **DECIMAL(p, d)** or NUMERIC(p, d): Fixed-point numeric type with precision p and d decimal places.

• **DATE**: Typically stored in YYYY-MM-DD format (SQL standard).

• **TIME**: Typically in 24-hour format HH:MM:SS.

• **BOOLEAN**: May store TRUE, FALSE, or UNKNOWN depending on the SQL dialect.

  

**Declaring Primary Keys & Constraints**

• **Primary Key**: A column (or set of columns) that uniquely identifies each row and does **not** allow NULL values.

• **Unique**: A column that must be distinct across rows but may allow NULLs.

• **DEFAULT**: Used to provide a default value if one is not specified during insert.

  

**Examples**:

```
CREATE TABLE TravelAgent (
   name VARCHAR(50) PRIMARY KEY,
   years_experience INT NOT NULL,
   phone VARCHAR(15) NOT NULL
);
```

You can also specify a **composite key** if multiple columns together form a unique identifier.

**5. Inserting Data (DML)**

  

Use **INSERT** statements to add rows. You specify:

• Which table you’re inserting into.

• The column list (optional if you’re inserting into all columns).

• The actual row values.

  

Example:

```
INSERT INTO TravelAgent (name, years_experience, phone)
VALUES
('Alice Brown', 12, '123-456-7890'),
('John Smith', 8, '234-567-8901');
```

**6. The SELECT-FROM-WHERE Pattern**

  

**General Form**

```
SELECT <columns or expressions>
FROM <one or more tables>
WHERE <conditions>;
```

• **SELECT**: Which columns (or computed expressions) to display in the result.

• **FROM**: One or more table names from which rows will be retrieved.

• **WHERE**: Filters rows according to specified conditions (e.g., comparisons, logical operators).

  

**Interpretation Steps**:

1. Identify the table(s) in the **FROM** clause.

2. Apply the condition(s) in the **WHERE** clause to filter rows.

3. Output only the columns or expressions listed in the **SELECT** clause.

  

**Select All Columns: SELECT ***

• Using SELECT * returns **all attributes** from the table(s) listed in FROM.

  

**Renaming Columns in the Result**

• Use AS to create an **alias** for a column in the query result:

```
SELECT name AS beer, manf
FROM Beers
WHERE manf = 'Anheuser-Busch';
```

This does **not** change the underlying column name—only the label displayed.

  

**Including Expressions or Constants**

• You can include arithmetic operations in the SELECT list (e.g., multiply a price by a factor).

• You can also add **constant strings** to label rows. Example:

```
SELECT drinker, 'likes Bud' AS whoLikesBud
FROM Likes
WHERE beer = 'Bud';
```

**7. Complex Conditions and Pattern Matching**

  

**Combining Conditions**

• **AND**, **OR**, **NOT** can be used in WHERE to form complex filters:

```
SELECT price
FROM Sells
WHERE bar = 'Joe''s Place' 
  AND beer = 'Bud';
```

  

  

**Pattern Matching with LIKE**

• **LIKE** and **NOT LIKE** allow matching substrings or wildcard patterns:

• **%** matches **any sequence** of characters (including empty).

• **_** (underscore) matches **exactly one** character.

  

**Examples**:

• Retrieve phone numbers that start with 352:

```
SELECT name, phone
FROM Drinkers
WHERE phone LIKE '352%';
```

  

• Retrieve addresses that **contain** the word “Main” anywhere:

```
SELECT name, address
FROM Drinkers
WHERE address LIKE '%Main%';
```

  

• Exclude any name exactly matching 'David Harris':

```
SELECT *
FROM Traveler
WHERE name NOT LIKE 'David Harris';
```

**8. Additional Notes on Keys and Combining Tables**

• **Choosing a Key**: Sometimes you must decide whether to combine attributes into a single table or split them. You may choose a composite key if the table doesn’t have a single, obvious unique identifier. For example, a trip leg might need a combination of start location, end location, and dates to guarantee uniqueness.

• **Combining or Not Combining**: The decision to combine relations or keep them separate can be a **designer’s judgment** call. Some database designers rely on the DBMS or specific modeling rules, while others keep multiple tables separate if it makes logical sense or if it is crucial to performance and clarity.

**9. Putting It All Together**

1. **Design** your database structure using **ER diagrams**.

2. **Convert** that structure into **relational tables** (specify columns, keys, and data types).

3. **Use DDL** (CREATE TABLE, ALTER TABLE, DROP TABLE) for defining or modifying table schemas.

4. **Use DML** (INSERT, SELECT, UPDATE, DELETE) to populate tables and query them.

5. **Filter** results with WHERE conditions and **match patterns** with LIKE or NOT LIKE.

6. **Interpret** queries in order: look at FROM (tables), apply WHERE (filters), then SELECT (returned columns/expressions).

  

By following these steps and best practices, you can confidently build and query relational databases in SQL.