---
title: "Database and DBMS Day-2 | 100DaysofDataScience"
datePublished: Sun Jan 07 2024 09:17:13 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xtfi5000402jsbv04eequ
slug: database-and-dbms-day-2-100daysofdatascience-72af5b6e78c2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752608444803/2d383f97-ab6f-4c61-a2ff-3c59ba875e31.png

---

### What is a DBMS

A database management system (DBMS) is a software system that provides the interfaces and tools needed to store, organize, and manage data in a database. A DBMS acts as an intermediary between the database and the applications or users that access the data stored in the database.

Hardware → OS → DB → DBMS → Backend → User

### Functions of DBMS

**Data Management** — Store, retrieve and modify data  
 **Integrity** — Maintain accuracy of data  
**Concurrency** — Simultaneous data access for multiple users  
**Transaction** — Modification to database must either be successful or must not happen at all  
 **Security** — Access to authorized users only  
**Utilities** — Data import/export, user management, backup, logging

***Data Management:-*** Involves storing, retrieving, and modifying data within a database system. This encompasses creating databases, tables, managing records, updating information, and executing queries to retrieve specific data sets.

***Integrity***: Ensuring the accuracy, consistency, and reliability of data by enforcing integrity constraints and validation rules. This involves maintaining data correctness through mechanisms like entity integrity, referential integrity, and data validation rules.

*Concurrency:* Allowing multiple users or processes to access and modify the database simultaneously while ensuring data consistency. Concurrency control mechanisms, such as locking, are implemented to prevent conflicts and maintain data integrity during simultaneous access.

***Transaction Management:*** Ensuring that database transactions follow the ACID properties (Atomicity, Consistency, Isolation, Durability). Transactions are treated as a single unit of work, ensuring that modifications either occur entirely (committed) or not at all (rolled back) to maintain data consistency.

*Security:* Protecting the database from unauthorized access, data breaches, or malicious activities. This involves implementing authentication mechanisms, authorization controls, encryption, and other security measures to ensure that only authorized users have access to the data.

***Utilities:*** Providing tools and functionalities for various administrative tasks, including data import/export, user management (user creation, permissions), backup and recovery, logging (tracking changes and activities within the database), and other administrative functions necessary for database maintenance and management.

These functionalities collectively contribute to the efficient, secure, and reliable management of data within a database system, ensuring data accuracy, availability, and security while enabling essential operations and administrative tasks.

### Database Keys

A key in a database is an attribute or a set of attributes that uniquely identifies a tuple (row) in a table. Keys play a crucial role in ensuring the integrity and reliability of a database by enforcing unique constraints on the data and establishing relationships between tables.

**Super Key** — A Super key is a combination of columns that uniquely identifies any row within a relational database management system (RDBMS) table  
 **Candidate key** — A candidate key is a minimal Super key, meaning it has no redundant attributes. In other words, it’s the smallest set of attributes that can be used to uniquely identify a tuple (row) in the table  
 **Primary Key** — A primary key is a unique identifier for each tuple in a table. There can only be one primary key in a table, and it cannot contain null values.  
 **Alternate Key** — An alternate key is a candidate key that is not used as the primary key.  
 **Composite Key** — A composite key is a primary key that is made up of two or more attributes. Composite keys are used when a single attribute is not sufficient to uniquely identify a tuple in a table.  
 Surrogate Key -  
 **Foreign Key** — A foreign key is a primary key from one table that is used to establish a relationship with another table.

Certainly, you’ve provided a comprehensive overview of different types of keys in a database:

**Super Key:** A super key is a set of one or more attributes (columns) that uniquely identifies tuples within a table. It can potentially have more attributes than required to uniquely identify rows.

**Candidate Key:** A candidate key is a minimal super key, meaning it’s a super key with the fewest possible attributes, making it unique and without any redundancy. Each candidate key uniquely identifies rows in a table.

**Primary Key:** A primary key is a candidate key chosen as the main method to uniquely identify tuples within a table. It must be unique for each row and cannot contain null values. There can only be one primary key in a table.

**Alternate Key:** An alternate key is a candidate key that is not selected as the primary key. While it’s unique, it’s not used as the primary method of identification.

**Composite Key:** A composite key is a primary key composed of two or more attributes (columns). It’s used when a single attribute cannot uniquely identify rows, requiring a combination of attributes to ensure uniqueness.

**Surrogate Key:** A surrogate key is a unique identifier introduced within a database table to serve as the primary key. It’s often an artificial or system-generated key, not derived from application data, and is used to uniquely identify rows, especially when no natural key exists or when natural keys are unsuitable for various reasons.

**Foreign Key:** A foreign key is a column or set of columns in a table that references the primary key in another table. It establishes a relationship between the two tables, ensuring referential integrity by enforcing constraints that the values in the foreign key must match values in the primary key of another table or be null.

Understanding and utilizing these key concepts is fundamental in designing databases, establishing relationships between tables, ensuring data integrity, and optimizing database performance.  
Cardinality of Relationships

Cardinality in database relationships refers to the number of occurrences of an entity in a relationship with another entity. Cardinality defines the number of instances of one entity that can be associated with a single instance of the related entity.

Person -> Driving License Number  
 Student -> college branch  
 Restaurants -> orders  
 Restaurants -> menu  
 Students -> courses

### Drawbacks of Databases

Complexity: Setting up and maintaining a database can be complex and time- consuming, especially for large and complex systems.

Cost: The cost of setting up and maintaining a database, including hardware, software, and personnel, can be high.

Scalability: As the amount of data stored in a database grows, it can become more difficult to manage, leading to performance and scalability issues.

Data Integrity: Ensuring the accuracy and consistency of data stored in a database can be a challenge, especially when multiple users are updating the data simultaneously.

Security: Securing a database from unauthorized access and protecting sensitive information can be difficult, especially with the increasing threat of cyber attacks.

Data Migration: Moving data from one database to another or upgrading to a new database can be a complex and time-consuming process.

Flexibility: The structure of a database is often rigid and inflexible, making it difficult to adapt to changing requirements or to accommodate new types of data.