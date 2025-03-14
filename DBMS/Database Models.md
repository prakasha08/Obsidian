https://www.studytonight.com/dbms/database-model.php
### **Types of Database Models 

A **Database Model** is like a **blueprint** that defines how data is **organized, stored, accessed, and updated** in a database. Different types of database models are used based on the **application's requirements**.

---

## **1. Hierarchical Model** 🏠🌳
![[Pasted image 20250305102454.png]]
This model arranges data in a **tree-like structure**, similar to a **family tree**.  
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

---

## **2. Network Model** 🌐🔗

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

---

## **3. Entity-Relationship (ER) Model** 📊👥
![[Pasted image 20250305102527.png]]

This model represents **real-world objects** as **entities** and their connections as **relationships**.  
It is mostly used in **database design** before implementing a relational database.

### **Example:**

A **hospital database** where:

- **Patients** (entity) have attributes like **name, age, contact**
- **Doctors** (entity) have attributes like **name, specialization**
- A **doctor-patient relationship** exists

### **Advantages:**

✅ **Easy to understand and design**  
✅ **Clear representation** of data relationships

### **Disadvantages:**

❌ Cannot be directly implemented as a database model  
❌ Needs conversion into a **Relational Model**

---

## **4. Relational Model** 🏢📄
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

### **Disadvantages:**

❌ Not suitable for **unstructured data**  
❌ Can be **slow** when handling **large-scale data**

---

## **5. Object-Oriented Model** 🏗️📦
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

❌ **Less mature** than relational models  
❌ Not widely adopted

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

### **Advantages:**

✅ **Scalable** and handles **big data**  
✅ Faster than relational databases for certain applications

### **Disadvantages:**

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

## **Which Model Should You Use?**

- **For structured data** → **Relational Model (SQL Databases like MySQL, Oracle)**
- **For flexible, big data storage** → **NoSQL Model (MongoDB, Firebase)**
- **For complex relationships (e.g., social networks)** → **Graph Model (Neo4j)**
- **For multimedia applications** → **Object-Oriented Model**
- **For organizational hierarchies** → **Hierarchical Model**
- **For older enterprise applications** → **Network Model**

---
