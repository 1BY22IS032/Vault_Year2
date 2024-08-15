<!--markdownlint-disable MD025-->
<!--markdownlint-disable MD029-->
# Question Banks

## MODULE 1

1. What do you Mean by DBMS? explain the various advantages of using a DBMS [DONE]
2. Describe the 3 schema architecture with block diagram. Why do we need mappings between schema levels [DONE]
3. Explain DBMS component modules along with a neat diagram [DONE]
4. Define Entity ,Entity set , Attribute with respect to ER model. List different types of attributes along with their symbols [DONE]
5. What is Data Independence, explain the different  types of data independence [DONE]
6. ER diagram of BANK with atleast 4 entities[DONE]
7. Define the following terms [DONE]
   1. Database
   2. Entity
   3. Weak entity
   4. DBMS catalog
   5. Snapshot
   6. Value Sets
   7. Cardinality Ratio
   8. Degree of a relationship
   9. Program Data Independence
   10. Total Participation
   11. Data Model
   12. Schema
   13. Instance
   14. Canned transaction
   15. DML
8. Explain the different categories of data models [NOT_DONE]
9. ER diagram for employee database [DONE]
   1. employee works for a dept
   2. every dept is headed by a manager
   3. An emp works on one or more projects
   4. An employee has dependents
   5. A department controls the projects
10. Explain the types of End users with examples [NOT_DONE]
11. Write a ER diagram to represent CAR entity type with 2 key attributes, Registration and Vehicle ID [DONE]

# Answers

## What do you Mean by DBMS? explain the various advantages of using a DBMS

A Database is a collection of implicitly related information.
A database management system is a collection of programs that allow us to create and interact with a database.

**Advantages of using a DBMS**:

- **Data Integrity:**:
  - Consistency: Utilising rules and constraints to preserve consistency of data within a database
  - Accuracy: Using validation rules and datatypes to avoid invalid data to be stored
- **Data Security:**:
  - Access Control:DBMS allows admins to assign access to users to protect sensitive information
  - Authentication and Authorisation: Users are authenticated through creds
- **Redundency and inconsistency reduction**:
  - Using normalisation techniques to reduce redundency in database management systems
  - By centralising data storage, dbms prevents multiple copies of the same data to be processed
- **Data Independence**:
  - DBMS separates the logical view of the data with the physical view making it easier to change the database schema without affecting applications
- **Data Backup and Recovery**:
  - DBMS provides mechanisms for automatic data backup and recovery in case of data loss
  - DBMS uses transaction management techniques like ACID (Atomicity, Consistency, Isolation, Durability)
- **Efficient Data Access**:
  - DBMS uses sophisticated algorithms to optimize the execution of queries
  - uses indexes to quickly locate data
- **Data Sharing**:
  - DBMS allows multiple users and applications to share data resources efficiently
- **Improved Data Administration**:
  - DBMS provides tools for database administration, making it easier to manage, update, and maintain data centrally

## Describe the 3 schema architecture with block diagram. Why do we need mappings between schema levels

**Three Schema Architecture**:

- Divides the database into 3 Levels of data abstraction
  - Internal Level
  - Conceptual Level
  - External Level
- This aims to separate the user applications and the physical database making it easier to manage and modify without affecting the entire system

1. Internal Level (Physical Schema):
   1. how data is physically stored in the database
   2. Deals with storing structure, accessing methods and indexing
   3. is the lowest level
   4. concernes itself with efficiecy of storage and retrival
2. Conceptual Level (Logical Schema):
   1. provides a community user view of the entire database
   2. Describes data stored in the db and the relationships among the data
   3. hides the details of the physical storage and focuses on the logical structure
3. External View:
   1. Highest level of abstraction
   2. Defines how external users view the data
   3. Different users might have different views on the database

![3LvlSchema](https://cdn.imgchest.com/files/6yxkc69g537.png)

### Need for mapping between Schema levels

These mappings define the relationships and transformations between the different levels of schema

1. Internal-Conceptual mapping:
   1. This mapping translates the conceptural schema into the internal schema
   2. Ensures the changes in physical storage structures do not affect the Conceptual schema
   3. Ex: if the files in the physical database changes from one format to another, it shouldn't affect the conceptual schema
2. Conceptual-External Mapping:
   1. This mapping connects the conceptual schema to the external views.
   2. It allows differnet users to have different views without affecting the conceptual schema

### Importance of Mapping

1. Data Abstraction:
   1. Allows users to interact with the database without causing changes to the physical storage
2. Schema Independence:
   1. Allows you to change one Schema level without affecting the others
3. User Specific views:
   1. Differnt users can have differnt views depending on their requirements

## Define Entity ,Entity set , Attribute with respect to ER model. List different types of attributes along with their symbols

1. **Entity**

- An entity is a real world object or thing that is distinguishable from other objects.
- An Entity can be a physical object (like a car or a person) or a conceptual object (like a department or a course)

2. **Entity Set**

- An entity set is a collection of similar types of entities.
- All entities in a set share similar properties called attributes
- Example : Set of all students in a university, represented by  'Student' Entity Set

3. **Attribute**

- A property or characteristic of an entity
- they describe the properties of entities in an entity set
- each attribute has a specific value for an entity in an entity set

### Types of Attributes and their Symbols

![Attributes](https://cdn.imgchest.com/files/l4necp6m3z4.png)

1. **Simple Attribute**:
   1. Atomic attribute that cannot be divided into smaller parts
   2. Represented by OVAL shape
   3. ex Name,Age
2. **Composite Attribute**:
   1. Attribute that can be divided into smaller sub parts each representing a more basic attribute
   2. Oval Connected to further ovals
   3. Ex : Address can be set into Street, City,Country etc
3. **Derived Attribute**:
   1. Attribute whose value can be derived from toher attributes in the database
   2. Dashed Oval
   3. Age can be derived from Date Of Birth
4. **Multi Valued Attribute**:
   1. A multi valued attribute is an attribute that can have multiple values for a single entity
   2. Double Oval
   3. Multiple Phone numbers for a single person
5. **Key Attribute**:
   1. Attribute that uniquely describes an entity in a set
   2. Oval with attribute name underlined
   3. Student_ID for a student entity

## What is Data Independence, explain the different  types of data independence

Data Independence refers to the capacity to change the schema at one level of a database system without requiring changes to the schema at the next higher level

1. Logical Data Independence
   1. Logical data independence is the ability to change the conceptual schema without having to change the external schemas or application programs
   2. Logical data independence is essential for adapting the database structure to changing business requirements without needing to modify the end-user applications repeatedly
2. Physical Data Independence
   1. Physical data independence is the ability to change the internal schema (how data is physically stored) without having to change the conceptual schema
   2. Physical data independence is crucial for optimizing the performance of the database and taking advantage of new storage technologies without disrupting the logical structure or affecting the applications using the database

## Define the following terms

1. **Database**
   - **Definition**: An organized collection of structured data, stored electronically, for efficient access and management.

2. **Entity**
   - **Definition**: A distinct object or thing in the real world, identifiable within a database (e.g., a person, place).

3. **Weak Entity**
   - **Definition**: An entity that depends on another entity (strong entity) for its identification and has a partial key.

4. **DBMS Catalog**
   - **Definition**: A repository storing metadata about database objects, like tables and indexes.

5. **Snapshot**
   - **Definition**: A static copy of the data at a particular moment in time.

6. **Value Sets**
   - **Definition**: The set of all possible values an attribute can take (also known as a domain).

7. **Cardinality Ratio**
   - **Definition**: Defines the number of entities that can be associated with another entity in a relationship (e.g., 1:1, 1:N).

8. **Degree of a Relationship**
   - **Definition**: The number of entity sets that participate in a relationship (e.g., binary, ternary).

9. **Program Data Independence**
   - **Definition**: The ability to change data structure without altering application programs.

10. **Total Participation**
    - When every instance of an entity must participate in a relationship.

11. **Data Model**
    - An abstract representation of how data is structured, stored, and related within a database.

12. **Schema**
    - The logical structure of the database, including tables, fields, and relationships.

13. **Instance**
    - **Definition**: The specific data stored in the database at a particular time.

14. **Canned Transaction**
    - **Definition**: A pre-defined, frequently used query or transaction.

15. **DML (Data Manipulation Language)**
    - **Definition**: SQL commands used to manipulate data, like `SELECT`, `INSERT`, `UPDATE`, `DELETE`.

## Explain DBMS component modules along with a neat diagram

1. Query Processor
   1. Parser : analyzes and checks the syntax of the queries
   2. optimizer: Optimizes the quiery execution plan
   3. Executor:  Executes the query
2. Storage Manager:
   1. Buffer Manager: Manages memory buffer
   2. File Manager : Handles physical storage of data on disk
   3. Disk Space Manager : Manages the allocation and deallocation of disk space
3. Transaction Manager
   1. Concurrency Control: Allows multiple transactions to run concurrently without issues
   2. Recovery : Ensures DB can be recovered after abrubt failure
4. Authorization Manager:
   1. Auth Control : Manges user access
   2. Integrity Control : Ensures data integrity by enforcing constraints
5. Catalog
   1. Stores metadata about the DB
6. User Interface
   1. Software for the user to easily access the DB
  
```sql
      +---------------------------+
      |      User Interface        |
      +------------|---------------+
                   |
      +------------v---------------+
      |     Query Processor         |
      | +------------------------+ |
      | | Query Parser            | |
      | | Query Optimizer         | |
      | | Query Executor          | |
      +------------|---------------+
                   |
      +------------v---------------+
      |     Storage Manager         |
      | +------------------------+ |
      | | Buffer Manager          | |
      | | File Manager            | |
      | | Disk Space Manager      | |
      +------------|---------------+
                   |
      +------------v---------------+
      |   Transaction Manager       |
      | +------------------------+ |
      | | Concurrency Control     | |
      | | Recovery Manager        | |
      +------------|---------------+
                   |
      +------------v---------------+
      |Authorization & Integrity   |
      |      Manager               |
      +------------|---------------+
                   |
      +------------v---------------+
      |    Data Dictionary          |
      +-----------------------------+
```
