[[]]<!--markdownlint-disable MD029-->
# QuestionBank

## Questions

### Justify the need of database Languages to interact with the DBMS Software by designing the scripts examples appropriately

- Imagine; large library system;
- use lib cards to manage books ; inneficient
- large scale its not possible;
- Here DBMS can come into effect;

Here we use DataBase Management languages to assist in our development

**1. DDL (DataDefinitionLanguage):**

```SQL
    CREATE TABLE Book(
        BookID PRIMARY KEY AUTO_INCREMENT,
        BookName VARCHAR(255),
        PublishingDate INT,
        AuthorID FOREIGN KEY REFERENCES Author(AuthorID) 
    );
```

Without DDL:

- Manually create Tables
- Lot of work + Errors can be found

**2. DML(DataManipulationLanguage):**

```SQL
    INSERT INTO Book(BookName,PublishingDate,AuthorID) VALUES ("test",1999,12);

    UPDATE Book SET BookName = "test2" WHERE AuthorID = 12;

    DELETE FROM Book WHERE AuthorID = 2;
    
```

Without DML:

- Modification and delition of entries and data is done by dml
- without it, it is a hassel to deal; can cause errors due to user

---

### Apply the concepts of Data Models, Schemas, and Instances for DB Design with examples

Going to use a movie theater booking as our example

**Data Models:**
They define the overall structure and the organisation of the data

- Entities: real world entities eg Movies, customers, tickets
- Attributes : qualities or properties of entities and relationships eg Movie_Name, Customer_Name, Ticket_ID
- Relationship:Defines how entities are connected eg : Customer may buy more than one movie

**Data Schema:** The schema is a blueprint that convets the data models into a database using languages like ddl and dml

Schema for the movie store

```SQL
    MOVIE TABLE:
        COLUMNS : MovieID (PRIMARY KEY), MovieName, DirectorName,Year;

    Customer TABLE :
        COLUMNS : CustomerID(PRIMARY KEY), CustomerName,CustomerContact;

    Ticket TABLE:
        COLUMNS: TicketID(PRIMARY KEY),CustomerID(FOREIGN KEY REFERENCES Customer(CustomerID),MovieID(FOREIGN KEY REFERENCES Movie(MovieID)))
```

**Instances:**
Instances are databases that contain real world data at a specific point in time.

Example:

|MovieID|MovieName|DirectorName|Year|
|---|---|---|---|
|1|A|a|1|
|2|B|b|2|
|3|C|c|3|

---

### Apply the Knowledge of Entity types, Entity sets, attributes, roles, and structural constraints for DB Design with examples

Let us apply the DB design for a library management system

**Entity Types**:

- Books : Represents a book in the library; attributes: Name, ID, AuthorName,Year
- Members : Represents a user of the library; attributes: Name, ID, Address
- Author : Represents an author of a book; attributes: Name, ID
- Loan : represents borrowing of a book; attributes : Loan date, due date

**Entity Sets**:

- Books : represents collection of all books
- Members : represents collection of all members
- Authors : represents collection of all Authors of books
- Loan : represents collection of all books that are loaned

**Attributes**:
Each entity has an attribute assiged to it.

- Books:
  - BookID(PRIMARY KEY) : distinct;universal
  - BookName: Title
  - AuthorID (FOREIGN KEY) : ID of the auth
  - AuthorName : name of author
  - Year: Year of publishing
- Member:
  - MemberID(PRIMARY KEY) : distinct; universal
  - MemberName : Name of user
  - MemberContact : Contact info of user
- Author:
  - AuthorID(PRIMARY KEY) : distinct; universal
  - AuthorName :Name of author
- Loan:
  - LoanID(PRIMARY KEY):distinct; universal
  - BookID(FOREIGN KEY):id of loaned book
  - MemberID(FOREIGN KEY): id of loaner
  - loan_date: Date at which book was loaned

**Roles**:
In a relationship, each entity plays a role.

- BOOK : book plays role of work, author plays the role of creator
- LOAN : book plays the role of the item being borrowed and the member plays the role of the borrowee
  
**StructuralConstraints**:

1. Cardinality Ratios:
    - One to One : entity only has a single relationship with another entity or attribute. eg: Book->BookID
    - One to Many : entity only has multiple relationships with other entities or attributes. eg Author->Books
    - Many to One : Many entities have relationships to one entity in another set eg : Books->Author
    - Many to Many : Many entites have relationship with many other entities in other sets eg: Members->Books
2. Participation Constraints: This is to check if all the entities are participating in a relationship

---

### Analyse the 3-schema Architechture and give your thoughts on every layer

The 3 layered schema provides us with a layered and separated aproach to a database

**InternalSchema**:

- Defines how data is physically stored
- Controls how data is managed into tables, datatypes and storage
- Offers flexibility for optimizing storage and performance
- Change in this level might have serious impact on other layers
  
**ConceptualSchema**:

- Reps the overall logical structure of the data
- Contains entities,relationships,attributes,constraints etc
- Acts as the middleman between the internalschema and the externalschema
- Does not deal with the physical storage

**ExternalSchema**:

- Represents the end user viewpoint
- Contains only the necessary info that needs to be displayed
- This increases security and data abstraction

**Overall**:

- Data Independence: 3LS allows us to make changes at different layers without drastically affecting the other layers
- Data Abstraction: Confidential Data can be hidden away at different layers prevent unauthorised access to them
- Conceptual Clarity : Gives the DBA a clarity on the management of the database

---

### Explain the following terms with suitable examples: i) Candidate Key ii) Super Key ii) Foreign Key iv) Prime attribute v) Key constraint

**Candidate Key**:

1. Mininal set of attributes that is assiged to a unique tuple in a table
2. Ensures no duplicates are made of the same set
3. ex : BookID

**Super Key**:

1. Any set of attributes that can uniquely identify a tuple
2. All SKs are CKs but not all CKs are SKs
3. Eg: BookName and PublishingYear are SKs but not CKs

**Foreign Key**:

1. FK is an attribute that references another table's PK
2. This establishes a link between tables
3. Eg :  in Loan, LoanID is the PK but AuthorID,BookID are FKs

**Prime Attributes**:

1. PA is an attribute that cannot be divided further for uniqueness
2. its a single attribute that contains the distinctness of a entity/attribute
3. Eg : BookID is a PA

**Key Constraint**:

1. rule enforced on the table to guarantee data integrity
2. PK Constraint : Enforces table has PK and value must not be null
3. Unique Constraint: Enforces uniqueness on a specific set of attributes
4. FK constraints:The values in the Foreign Key must either match existing values in the referenced Primary Key or be null

---

### Explain the characteristics of a Relations with examples

a relation refers to a structured table that holds data organized in rows and columns

1. Ordering of Tuples (Rows):

    Characteristic: Tuples (rows) in a relation do not necessarily have a specific order. This means the order in which rows are physically stored might not be significant. However, the order might be imposed when the data is retrieved for presentation.
    Example: In a "Customers" table, the order of customer records might not be important for querying purposes. You can retrieve data based on specific criteria regardless of the order they are stored in.

2. Ordering of Values within a Tuple (Row):

    Characteristic: The order of values within a tuple (row) is critical. The position of a value in a column determines its meaning.
    Example: In a "Customers" table with columns for "Name," "Address," and "Phone Number," the order is crucial. The first value corresponds to the customer's name, the second to their address, and the third to their phone number.

3. Domain Constraints:

    Characteristic: Domain constraints define the set of valid values that an attribute (column) can hold. This ensures data consistency and accuracy.
    Example: In a "Customers" table, the "Age" column might have a domain constraint that only allows values between 18 and 120. This ensures only valid age data is entered.

4. Atomicity:

    Characteristic: An atomic relation is indivisible. It represents a single unit of data, and all its elements (tuples and values) must be inserted, deleted, or modified together as a whole.
    Example: You cannot insert a customer record with a name but without an address. The entire record (tuple) needs to be complete and valid for insertion.

5. Keys:

    Characteristic: Keys are attributes (or sets of attributes) that uniquely identify rows within a relation. They are crucial for data retrieval and maintaining referential integrity between tables.
        Primary Key: A table can have one Primary Key, which is a minimal set of attributes that uniquely identifies each row.
        Candidate Key: Any set of attributes that can uniquely identify rows in a table is a Candidate Key. There can be multiple Candidate Keys, but only one is chosen as the Primary Key.
        Foreign Key: A Foreign Key references the Primary Key of another table, establishing a link between related data sets.
    Example: In a "Books" table, the "BookID" can be the Primary Key, uniquely identifying each book. Additionally, the combination of "ISBN" and "PublicationYear" might also be a Candidate Key. A "Loan" table might have a "BookID" as a Foreign Key referencing the "Books" table, ensuring loaned books exist in the collection.

6. Redundancy (Minimized):

    Characteristic: Ideally, a well-designed relational database minimizes data redundancy. This reduces storage requirements and the risk of inconsistencies when the same data needs to be updated in multiple places. Foreign Keys help achieve this by referencing existing data instead of storing duplicate information.
    Example: Instead of storing the author's name in every book record, you can have a separate "Authors" table with author information. The "Books" table can then have a Foreign Key referencing the "AuthorID" in the "Authors" table, eliminating redundant author names.

---

### What are the relational Integrity Constraints with examples?

Relational integrity constraints are a set of rules enforced within a relational database to ensure data consistency and accuracy.

1. Entity Integrity:
   1. Ensures that each tuple has aunique identifer and cannot be null
   2. Enforced by primary keys
   3. eg: in customer table, CustomerID cannot be empty
2. Referential Integrity:
   1. Maintains consistency between related tables by ensuring references between them are valid
   2. made through FKs
   3. eg: in lib man sys , Loans are connected to AuthorID and BookID hence connecting the tables
3. Domain Integrity:
   1. restricts values of an attribute to a specific set
   2. enforced through datatypes
   3. eg : Age must be an integer below 118 and greater than 0
4. Domain-Specific Constraints:
   1. add additional rules
   2. enforced through coded in triggers

---