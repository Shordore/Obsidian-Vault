
**Summary and Key Points from the Lecture**

  

Below is a concise overview of the major themes and details covered in the lecture.

  

**1. Defining and Using Keys**

1. **Keys as Unique Identifiers**

• Each **entity set** should have a **key** (one or more attributes) that uniquely identifies its entities.

• In an ER diagram, key attributes are typically **underlined**.

2. **Key Propagation in Inheritance**

• In cases of **inheritance** (superclass/subclass), the superclass key is automatically propagated to the subclass.

• **Subclass entities** do not introduce their own keys; they simply inherit the key attributes of the superclass.

  

**2. Weak Entity Sets**

1. **Concept of Weak Entities**

• A **weak entity set** cannot form a unique key by itself.

• It needs to combine its **partial key** (also called a **discriminator**) with the **key of a related strong entity** to form a **composite key** that is unique.

2. **Notation in ER Diagrams**

• Weak entity sets are represented by a **double rectangle**.

• The **supporting relationship** (the relationship that provides the additional part of the key) is denoted by a **double diamond**.

3. **Relationship Multiplicity**

• The supporting relationship from a weak entity set to its strong entity set must be **many-to-one** (often read as “many weak entities relate to exactly one strong entity”).

4. **Partial Keys**

• Within a weak entity set, the attribute(s) that serve to distinguish entities **only within** that relationship are sometimes underlined with a **dashed** or **partial** underline.

• The full key becomes a **composite** of that partial key + the key of the strong entity.

5. **Examples**

• **Rooms** in a **Building**: A room number by itself is not globally unique (e.g., “Room 100” appears in many buildings). The full key might be (BuildingName, RoomNumber).

  

**3. Database Design Guidelines**

1. **Faithfulness to the Problem**

• Ensure the ER diagram reflects only attributes and entities relevant to the real-world scenario.

• Do not add unrelated attributes (e.g., “numberOfCylinders” for a “bar” entity would be irrelevant).

2. **Avoid Redundancy**

• Redundancy = repeating the same facts or data in multiple places.

• Leads to **waste of storage** and potential **inconsistencies** (e.g., updating data in one place but forgetting to update it elsewhere).

3. **Choosing an Attribute vs. an Entity Set**

• If something can be captured as a **single attribute** without losing detail, do so.

• If it has multiple attributes or participates on the “many” side of a relationship, it likely should be a separate **entity set**.

4. **Limit Weak Entity Sets**

• If a global or unique identifier can be assigned, prefer creating a strong entity set.

• Only use a weak entity set if there is truly no straightforward global key (e.g., room numbers within buildings).

  

**4. Redundancy and Its Pitfalls**

1. **Definition**

• Redundancy is representing the **same information** in more than one place (e.g., storing “manufacturer address” in two different entities or tables).

2. **Consequences**

• **Inconsistency**: Updating or deleting data in one place but not the other can lead to mismatched records.

• **Loss of Data**: Deleting a record might accidentally remove the **only** stored version of certain data (e.g., the sole row referencing a manufacturer’s address).

3. **Design Examples**

• Good design often splits data into different entities (e.g., “Beers” and “Manufacturers”) to avoid duplication.

• A poor design might store the **same manufacturer address** in every beer record, causing massive repetition.

  

**5. Deciding If Something Should Be an Entity**

  

A general rule of thumb:

• An **entity set** is justified if it either:

1. Has more than a key attribute (i.e., at least one non-key attribute), **or**

2. Appears on the “many” side of a **many-to-one** or **many-to-many** relationship.

  

Otherwise, a simple **attribute** may suffice.

  

**6. Example Scenario (In-Class Activity)**

  

**Scenario Overview**: A corporation with the following structure and requirements:

1. **Entities**:

• **Employees** (attributes: employeeID [key], name, jobTitle, salary)

• **Departments** (attributes: departmentID [key], name, location)

• **Projects** (attributes: projectID [key], name, budget)

• **Tasks** (weak entity: taskID + projectID form the key, plus attributes like description, deadline)

2. **Relationships**:

• An **Employee** is **assigned** to exactly one **Department** (many employees to one department).

• A **Department** **oversees** multiple **Projects**, each Project belongs to exactly one Department (many-to-one).

• A **Project** **consists of** multiple **Tasks**, each **Task** is part of exactly one Project. Since **taskID** alone isn’t unique, **Task** is a **weak entity**; it uses projectID + taskID as its full key.

• **Employees** can be **assigned to** multiple **Tasks**, and each **Task** can have multiple **Employees** (a many-to-many relationship).

• Each **Department** is **managed by** exactly one **Employee**, and each Employee can manage at most one Department (could be a one-to-one or one-to-zero/one relationship).

• Each **Project** is **led by** exactly one **Employee**, and an Employee can lead only one Project at a time.

3. **Weak Entity Notation**:

• In the ER diagram, **Tasks** would be shown as a **double rectangle**.

• The relationship between **Tasks** and **Projects** (the supporting relationship) would be a **double diamond**.

  

This exercise demonstrated how to translate textual requirements into an ER diagram with correct entity sets, keys, relationships, and notation for weak entities.

  

**Quick Reference Diagram (Abstracted Example)**

  

   [EMPLOYEE] ------------------ (manages) ------------------ [DEPARTMENT]

     (employeeID)*                                       (departmentID)*     

       name,                                                    name, 

       jobTitle,                                                location

       salary

   [DEPARTMENT] ------------------ (oversees) ----------------- [PROJECT]

     (departmentID)*                                       (projectID)*

   [EMPLOYEE] ------------------ (assigned_to)  ------------------ [TASK] (weak)

     (employeeID)*                                            (taskID)*

                                                                description

                                                                deadline

                                                          <dependent on PROJECT> 

   [PROJECT] -------------- (consists_of: double diamond) ------ [TASK](double rectangle)

     (projectID)*                 (supporting relationship)

     name, 

     budget

  

* indicates key attributes.

The “(double rectangle)” and “(double diamond)” are not literal but illustrate the notation for weak entities and their supporting relationships.

  

**Conclusion**

  

This lecture focuses on **keys**, **weak entity sets**, and **sound design principles** in ER diagrams:

• Use **keys** and **weak entities** correctly to ensure each entity is uniquely identifiable.

• Follow design rules to **avoid redundancy** and maintain **data consistency**.

• Understand how to decide between treating something as an **attribute** vs. an **entity set**.

• Minimizing (but correctly using) weak entities leads to more robust database schemas.