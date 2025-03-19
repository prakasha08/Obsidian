
A **Database Management System (DBMS)** is a software that helps store, manage, and retrieve data efficiently. However, users and applications do not always access the database directly. Instead, the architecture of a DBMS defines how data is stored, accessed, and managed.

### **Types of DBMS Architectures**

DBMS architecture can be:

1. **Centralized** – All data is stored at a single location.
2. **Decentralized** – Multiple copies of the database exist at different locations.
3. **Hierarchical** – Data is organized in a tree-like structure.

DBMS architecture is generally classified into **1-tier, 2-tier, and 3-tier architectures**.

---

## **1-Tier Architecture**
### **Overview:**

- In **1-tier architecture**, the **database and the user interface** are on the **same machine**.
- The user directly interacts with the database without an intermediary application.
- Mostly used for **local applications** and **database management tools**.
- The database is directly accessible by the user.
- Used for local application development (e.g., developers testing code on their computers).
- No security layer between user and database.

📌 **Example:**

- Microsoft **Access**
- Local **SQLite databases** in mobile apps
- A developer using **MySQL Workbench** to query a database

![[Pasted image 20250319221943.png]]
#### **Advantages:**

✅ Fast and simple, as everything runs on a single machine.  
✅ No network latency.  
✅ Ideal for small-scale applications.

#### **Disadvantages:**

❌ Not suitable for multi-user environments.  
❌ Security risks due to direct access to the database.  
❌ Poor scalability.

---

## **2-Tier Architecture**
### **Overview:**

- In **2-tier architecture**, the application (client) and database (server) are separate.
- The **client application** sends queries to the **database server**, which processes and returns results.
- Communication happens using **ODBC (Open Database Connectivity)** or **JDBC (Java Database Connectivity)**.

![[Pasted image 20250319222138.png]]
 ![[Pasted image 20250305095416.png]]
- Introduces an **Application Layer** between the user and the DBMS.
- The application acts as a bridge, sending user requests to the database and returning results.
- Provides **better security** since users do not access the database directly.
- Uses **ODBC (Open Database Connectivity)** or APIs to communicate between the application and database.
#### **Understanding ODBC (Open Database Connectivity)**

- **ODBC acts as a translator** between the application and the database.
- It provides a **universal way** to access **any database**, regardless of the database type (MySQL, SQL Server, Oracle, etc.).
- The application sends an SQL query to ODBC, and ODBC translates it into a form the specific database understands.

📌 **Example of ODBC Usage:**  
Imagine you have a **Microsoft Excel sheet** that needs to pull data from a **MySQL database**.

- Excel does not understand MySQL directly.
- Instead, it uses **ODBC drivers** to connect and fetch the data.
📌 **Example**:

- A banking application where the user requests their account balance, and the application fetches the data from the database.

🔹 **Components**:

1. **User Interface (Client-Side Application)** – Users interact with the application.
2. **Application Layer** – Processes requests and communicates with the DBMS.
3. **Database Server** – Stores and manages data.

---

#### **Understanding APIs (Application Programming Interfaces)**

- APIs are **specific to each database** and provide a **direct way** to interact with it.
- Instead of using a general connector like ODBC, APIs allow applications to talk **directly** with a database.
- APIs are typically **faster** than ODBC because they are optimized for a specific database system.

📌 **Example of Database API Usage:**

- **JDBC (Java Database Connectivity)** is an API used in Java applications to interact with databases.
- **PDO (PHP Data Objects)** is an API in PHP to connect to databases.
### **Example:**

- A **Java application** using JDBC to connect to a **MySQL database**.
- **Banking systems**, where the **ATM** (client) interacts with the **bank database** (server).

### **Structure:**

📌 **Client (User Interface & Business Logic)** ⟶ **Database Server**

### **Advantages:**

✅ Improved **security** (database is separate).  
✅ **Better performance** compared to 1-tier.  
✅ Can support **multiple users**.

### **Disadvantages:**

❌ Requires **network communication**, causing some latency.  
❌ Harder to scale than 3-tier architecture.
## **3-Tier Architecture (Most Common in Web Applications)**
### **Overview:**

- In **3-tier architecture**, there are **three separate layers**:
    1. **Presentation Layer (Client)** – User interacts through a **web browser or mobile app**.
    2. **Application Layer (Server)** – Processes business logic and communicates with the database.
    3. **Database Layer** – Stores data and processes queries.
- Commonly used in **web applications and enterprise systems**.

![[Pasted image 20250319222453.png]]
![[Pasted image 20250305095513.png]]

- Extends the **2-tier architecture** by adding a **Presentation Layer (GUI Layer)**.
- This makes applications **more scalable and secure** since users do not interact with the database or application layer directly.
- In 3-tier architecture, an additional Presentation or GUI Layer is added, which provides a graphical user interface for the End user to interact with the DBMS.
- For the end user, the GUI layer is the Database System, and the end user has no idea about the application layer and the DBMS system.
- If you have used **MySQL**, then you must have seen **PHPMyAdmin**, it is the best example of a 3-tier DBMS architecture.

📌 **Example**:

- **PHPMyAdmin** (a web-based tool for managing MySQL databases).
- **E-commerce websites** like Amazon, where users see a graphical interface (GUI), but the actual data processing happens in the background.

🔹 **Components**:

1. **Presentation Layer (GUI Layer)** – User interface (website, mobile app).
2. **Application Layer (Logic Layer)** – Handles business logic and communicates with the database.
3. **Database Layer** – Stores and retrieves data.
### **Example:**

- **E-commerce websites** like Amazon.
- **Social media platforms** like Facebook.
- A **React frontend** ⟶ **Node.js backend** ⟶ **MongoDB database**.

### **Structure:**

📌 **Client (User Interface - Browser/App)** ⟶ **Application Server (Processes requests, Business Logic)** ⟶ **Database Server**

### **Advantages:**

✅ **Highly scalable** (can handle many users).  
✅ **More secure** (database is not directly exposed).  
✅ **Easier to maintain and update**.

### **Disadvantages:**

❌ **More complex** than 1-tier and 2-tier.  
❌ Requires **networking and additional infrastructure**.

---

### **Comparison of DBMS Architectures**

|**Architecture**|**Security**|**User Access**|**Usage**|
|---|---|---|---|
|**1-Tier**|Low|Direct access|Local development|
|**2-Tier**|Medium|Through an application|Client-server apps|
|**3-Tier**|High|Through GUI|Web and enterprise apps|

### **Conclusion**

- **1-Tier** is used for local testing.
- **2-Tier** is used for applications requiring direct but controlled access.
- **3-Tier** is the most secure and commonly used in modern web applications.

