https://www.studytonight.com/dbms/database-model.php
### **Types of Database Models 

A **Database Model** is like a **blueprint** that defines how data is **organized, stored, accessed, and updated** in a database. Different types of database models are used based on the **application's requirements**.

---

## **1. Hierarchical Model** 🏠🌳
### **Concept:**

- Data is **organized in a tree-like structure** with a **parent-child relationship**.
- Each **parent node** can have **multiple child nodes**, but a **child has only one parent**.
- Uses **pointers/links** to connect records.
		
![[Pasted image 20250305102454.png]]This model arranges data in a **tree-like structure**, similar to a **family tree**.
Each record (data entry) has a **single parent** but can have **multiple children**.

### **Example:**

A **school database** where:

- A **school (parent node)** has multiple **departments (child nodes)**
- Each **department** has multiple **teachers**
- Each **teacher** has multiple **students**

### **Advantages:**

✅ Fast data retrieval for **one-to-many relationships**  
✅ Easy to understand for **structured data**

### **Disadvantages:**

❌ **Less flexible** (can’t easily add new relationships)  
❌ Doesn’t support **many-to-many** relationships
### **Example Database:**

IBM **IMS (Information Management System)**.

---

## **2. Network Model** 🌐🔗
### **Concept:**

- Similar to the **hierarchical model**, but allows **many-to-many relationships**.
- Uses **graph-like structures** where records are **connected using multiple links**.

![[Pasted image 20250305102502.png]]
An **extension** of the hierarchical model, but here **a child can have multiple parents**.  
It represents **many-to-many** relationships.

### **Example:**

A **university database** where:

- A **student** can be enrolled in multiple **courses**
- A **course** can have multiple **students**

### **Advantages:**

✅ Supports **complex relationships**  
✅ Faster **data access** than hierarchical models

### **Disadvantages:**

❌ **Difficult to manage and modify**  
❌ **Complicated structure** compared to relational models
❌ Uses **pointers**, making updates difficult.

### **Example Database:**

Integrated Data Store (**IDS**).

---

## **3. Entity-Relationship (ER) Model** 📊👥
### **Concept:**

- Represents **data using entities (objects), attributes, and relationships**.
- Entities are real-world objects, and relationships show how they are connected.
- Used in **database design** before converting to a relational schema.

![[Pasted image 20250305102527.png]]

This model represents **real-world objects** as **entities** and their connections as **relationships**.  
It is mostly used in **database design** before implementing a relational database.

### **Example:**

A **hospital database** where:

- **Patients** (entity) have attributes like **name, age, contact**
- **Doctors** (entity) have attributes like **name, specialization**
- A **doctor-patient relationship** exists
### **Example:**

📌 **University ER Diagram**

```scss
Student (Entity)
   ├── StudentID (Primary Key)
   ├── Name
   ├── Age
   ├── CourseID (Foreign Key)

Course (Entity)
   ├── CourseID (Primary Key)
   ├── CourseName
   ├── Credits

Relationship: "Enrolled_In" (Student ↔ Course)
```
### **Advantages:**

✅ **Visual Representation** makes database design easier.  
✅ Helps in **normalization** (avoiding redundancy).  
✅ Can be easily converted into **Relational Models**.

### **Disadvantages:**

❌ Not directly used for implementation (needs conversion to RDBMS).  
❌ Complex relationships can make diagrams difficult to understand.

### **Example Usage:**

- **Database Design** for Schools, Hospitals, Banking, etc.
- Used in **ER Diagrams** before creating relational tables.

### **Example ER Diagram Tool:**

- **Draw.io, Lucidchart, Microsoft Visio**.
---

## **4. Relational Model** 🏢📄
### **Concept:**

- Data is stored in **tables (relations)** with **rows (records) and columns (fields)**.
- Uses **primary keys** and **foreign keys** to establish relationships.

![[Pasted image 20250305102533.png]]

The most widely used database model, where **data is stored in tables (rows & columns)**.  
Each table has a **unique key** to relate data.

### **Example:**

A **bank database** where:

- A **Customers table** stores **ID, Name, Address**
- An **Accounts table** stores **Account Number, Balance, Customer ID**
- **Customer ID** is the key linking both tables

### **Advantages:**

✅ **Easy to understand and use**  
✅ Uses **SQL** for data management  
✅ Reduces **data redundancy** (through normalization)
✅ Supports **ACID properties** (Atomicity, Consistency, Isolation, Durability).
### **Disadvantages:**

❌ **Performance issues** with very large datasets.  
❌ **Normalization** can make complex queries slower.
❌ Not suitable for **unstructured data**  
❌ Can be **slow** when handling **large-scale data**
### **Example Databases:**

MySQL, PostgreSQL, Oracle, SQL Server.

---

## **5. Object-Oriented Model** 🏗️📦
### **Concept:**

- Data is stored as **objects** (similar to OOP in programming).
- Objects contain **attributes (data)** and **methods (functions)**.

![[Pasted image 20250305102538.png]]
Data is stored as **objects**, similar to **Object-Oriented Programming (OOP)**.  
Each object contains **data (attributes)** and **functions (methods)**.

### **Example:**

A **multimedia database** where:

- A **Video** object contains **title, duration, resolution**
- A **Song** object contains **artist, album, genre**

### **Advantages:**

✅ Supports **complex data types** like images, videos  
✅ Uses **OOP principles** like **Inheritance & Encapsulation**

### **Disadvantages:**

❌ Not as **widely used** as relational databases.  
❌ More **complex** than RDBMS.

---

## **6. NoSQL Model** 🗄️⚡
![[Pasted image 20250305102544.png]]
NoSQL databases store **unstructured or semi-structured** data.  
They don’t follow the **table structure** of relational models.  
Data is stored in **key-value pairs, documents, or graphs**.

### **Example:**

A **social media app database** where:

- **User profiles** are stored as JSON documents
- **Posts & comments** are linked using key-value pairs
### **Concept:**

- Designed for **big data, high scalability, and flexible schema**.
- Does not use traditional **tables and rows**.
- Types: **Key-Value, Document, Column-Family, Graph**.

### **Types & Examples:**

1. **Key-Value Store** (Amazon DynamoDB, Redis)
    - Stores data as **key-value pairs** (`{"username": "JohnDoe"}`)
2. **Document-Oriented** (MongoDB, CouchDB)
    - Stores data in **JSON/BSON documents** (`{name: "Alice", age: 25}`)
3. **Column-Family Store** (Cassandra, HBase)
    - Stores data in **columns** instead of rows (efficient for analytics).
4. **Graph Databases** (Neo4j)
    - Represents data as **nodes and edges** (useful for social networks).
### **Advantages:**

✅ **Scalable** and handles **big data**  
✅ Faster than relational databases for certain applications

### **Disadvantages:**

❌ Does not support **ACID properties** like RDBMS.
❌ **Limited querying capabilities**  
❌ Not ideal for **highly structured data**

---

## **7. Graph Model** 🛤️🔗
![[Pasted image 20250305102547.png]]
Best for representing **highly interconnected data** using **nodes (entities) and edges (relationships)**.

### **Example:**

A **social network database** where:

- **Users** are nodes
- **Friendship connections** are edges

### **Advantages:**

✅ **Handles complex relationships efficiently**  
✅ Best for **recommendation systems & social networks**

### **Disadvantages:**

❌ Not suitable for **simple data structures**  
❌ Can be **expensive to implement**

---

## **Summary Table of Database Models**

|Database Model|Structure|Best Use Case|Advantages|Disadvantages|
|---|---|---|---|---|
|**Hierarchical**|Tree|Organizational charts, File Systems|Fast data access|No many-to-many relationships|
|**Network**|Graph|Complex relationships (University, Banking)|Supports many-to-many|Hard to maintain|
|**ER Model**|Entities & Relationships|Designing databases|Easy to visualize|Needs conversion to relational|
|**Relational**|Tables|Banking, E-commerce|SQL support, easy to use|Slow for large-scale data|
|**Object-Oriented**|Objects|Multimedia, CAD systems|Supports complex data types|Not widely used|
|**NoSQL**|Documents/Key-Value|Big data, Real-time applications|Scalable, high performance|Limited querying|
|**Graph**|Nodes & Edges|Social Networks, Recommendations|Best for complex relationships|Expensive|

---
### **Comparison Table (Including ER Model)**

| **Model**           | **Structure**                       | **Use Case**                | **Example DB**               |
| ------------------- | ----------------------------------- | --------------------------- | ---------------------------- |
| **Hierarchical**    | Tree Structure                      | File systems, Org charts    | IBM IMS                      |
| **Network**         | Graph with Links                    | Many-to-Many relationships  | IDS                          |
| **Relational**      | Tables                              | Business apps, CRM, Banking | MySQL, Oracle                |
| **Object-Oriented** | Objects                             | CAD, Multimedia, AI Systems | ObjectDB                     |
| **NoSQL**           | JSON, Key-Value, Graphs             | Big Data, Social Networks   | MongoDB, Neo4j               |
| **ER Model**        | Entities, Attributes, Relationships | Database Design             | Used for designing databases |
## **Which Model Should You Use?**

- **For structured data** →**Relational Model (RDBMS)** is the most widely used (MySQL, Oracle).
- **For flexible, big data storage** →- **NoSQL Models** are best for **big data and scalability** (MongoDB, Cassandra).
- **For complex relationships (e.g., social networks)** → **Graph Model (Neo4j)**
- **For multimedia applications** → - **Object-Oriented Databases** are useful in **AI, CAD, and multimedia applications**.
- **For organizational hierarchies & older enterprise applications** → **Hierarchical and Network Models** are **legacy systems** still used in some industries.

---
