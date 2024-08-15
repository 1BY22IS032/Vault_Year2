<!--markdownlint-disable MD025-->
<!--markdownlint-disable MD029-->
<!--markdownlint-disable MD032-->
<!--markdownlint-disable MD022-->
<!--markdownlint-disable MD001-->
<!--markdownlint-disable MD031-->
# Questions

1. Briefly discuss the different types of update operations on relational database
   1. show a violation of the referential and entity integrity in each fo the update operation
2. Explain characteristics of Relations
3. Define the following
   1. Primary Key
   2. Super Key
   3. Foreign key
   4. Candidate key
4. All forms of ALTER Commands with examples
5. Write Queries for Examples [Refer_Paper]
6. Explain the concepts of specialization and generalization with the help of VEHICLE superclass
7. Explain the different Relation Model Constraints
8. Create a table for Works_IN Relationship [REFER_PAPER]
9. Explain Entity Integrity and Referential Integrity constraints. Why is each considered Important Give Examples
10. Discuss EquiJoin and Natural Join with suitable examples using relational algebra notation
11. Explain the ER to relational mapping algorithm with suitable example for each step
12. How is referential Integrity implemented in SQL
13. Explain the Relational Algebra operations from set theory with examples
14. explain Insert Command , Update command, ALTER
15. Basic datatypes available for attributes in SQL.

# Answers

### 1. **Types of Update Operations on Relational Database**
Relational databases support several update operations that allow for the manipulation of data within tables. The primary update operations include:

#### **a. Insert Operation**
- **Description**: The `INSERT` operation is used to add new rows (tuples) to a table. Each row must adhere to the table's schema, meaning it must contain the correct data types and satisfy all constraints (e.g., primary keys, foreign keys, etc.).
- **Example**:
  ```sql
  INSERT INTO Employees (Employee_ID, Name, Dept_ID) 
  VALUES (101, 'John Doe', 10);
  ```
- **Violation Example**:
  - **Referential Integrity**: If `Dept_ID` 10 does not exist in the `Departments` table, this insert operation would violate referential integrity.
  - **Entity Integrity**: Inserting a row with a `NULL` value in `Employee_ID` (which is a primary key) would violate entity integrity.

#### **b. Delete Operation**
- **Description**: The `DELETE` operation removes rows from a table based on a specified condition. Care must be taken to ensure that removing a row does not lead to inconsistencies, particularly with foreign key relationships.
- **Example**:
  ```sql
  DELETE FROM Employees 
  WHERE Employee_ID = 101;
  ```
- **Violation Example**:
  - **Referential Integrity**: If there are rows in another table that reference `Employee_ID` 101, deleting this row would violate referential integrity unless cascading delete is configured.
  
#### **c. Update Operation**
- **Description**: The `UPDATE` operation modifies existing data within a table. This operation can change one or more columns in one or more rows, depending on the condition provided.
- **Example**:
  ```sql
  UPDATE Employees 
  SET Dept_ID = 20 
  WHERE Employee_ID = 101;
  ```
- **Violation Example**:
  - **Referential Integrity**: Changing `Dept_ID` to a value that does not exist in the `Departments` table would violate referential integrity.
  - **Entity Integrity**: Setting `Employee_ID` to `NULL` in an update would violate entity integrity.

#### **d. Select Operation**
- **Description**: Though not an update operation, the `SELECT` operation retrieves data from one or more tables. It is important to understand this in conjunction with update operations as data retrieval is often followed by modifications.
- **Example**:
  ```sql
  SELECT * FROM Employees WHERE Dept_ID = 10;
  ```

### 2. **Characteristics of Relations**
In the context of a relational database, a **relation** is a table consisting of rows and columns. The characteristics of a relation are:

#### **a. Tuples**
- **Definition**: Rows in a relation are called tuples. Each tuple represents a unique record in the table.
- **Example**: In an `Employees` table, each row represents an individual employee.

#### **b. Attributes**
- **Definition**: Columns in a relation are called attributes. Each attribute corresponds to a property of the entity that the table represents.
- **Example**: `Employee_ID`, `Name`, and `Dept_ID` are attributes in the `Employees` table.

#### **c. Domain**
- **Definition**: A domain is the set of permissible values that an attribute can have.
- **Example**: The domain for the `Employee_ID` attribute might be positive integers.

#### **d. Degree**
- **Definition**: The degree of a relation is the number of attributes it contains.
- **Example**: A table with four attributes (`Employee_ID`, `Name`, `Dept_ID`, `Salary`) has a degree of 4.

#### **e. Cardinality**
- **Definition**: The cardinality of a relation is the number of tuples it contains.
- **Example**: If the `Employees` table has 100 rows, its cardinality is 100.

#### **f. Integrity Constraints**
- **Definition**: Rules enforced on data to ensure accuracy and consistency.
- **Example**: Primary keys must be unique and not `NULL`.

### 3. **Definitions**

#### **a. Primary Key**
- **Definition**: A primary key is an attribute or a set of attributes that uniquely identifies each tuple in a relation. It must contain unique values and cannot be `NULL`.
- **Example**: `Employee_ID` in the `Employees` table.

#### **b. Super Key**
- **Definition**: A super key is a set of one or more attributes that, when combined, can uniquely identify a tuple in a relation.
- **Example**: `{Employee_ID, Name}` is a super key if `Employee_ID` is unique.

#### **c. Foreign Key**
- **Definition**: A foreign key is an attribute or a set of attributes in one relation that refers to the primary key of another relation. It enforces referential integrity.
- **Example**: `Dept_ID` in the `Employees` table is a foreign key that references the `Dept_ID` in the `Departments` table.

#### **d. Candidate Key**
- **Definition**: A candidate key is a minimal super key, meaning it has no unnecessary attributes. Every candidate key can serve as a primary key.
- **Example**: Both `Employee_ID` and `{Employee_ID, Name}` might be candidate keys, but typically `Employee_ID` is chosen as the primary key because it's minimal.

### 4. **ALTER Commands**

The `ALTER TABLE` statement in SQL is used to modify the structure of an existing table.

#### **a. Add Column**
- **Description**: Adds a new column to a table.
- **Example**:
  ```sql
  ALTER TABLE Employees ADD Email VARCHAR(255);
  ```

#### **b. Drop Column**
- **Description**: Removes an existing column from a table.
- **Example**:
  ```sql
  ALTER TABLE Employees DROP COLUMN Email;
  ```

#### **c. Modify Column**
- **Description**: Changes the data type or constraints of an existing column.
- **Example**:
  ```sql
  ALTER TABLE Employees MODIFY Salary DECIMAL(10, 2);
  ```

#### **d. Rename Table**
- **Description**: Renames an existing table to a new name.
- **Example**:
  ```sql
  ALTER TABLE Employees RENAME TO Staff;
  ```

### 5. **Write Queries**
For writing specific SQL queries, please refer to the examples provided in your reference paper. Generally, SQL queries involve selecting, inserting, updating, or deleting data from tables.

### 6. **Specialization and Generalization**

#### **a. Specialization**
- **Description**: Specialization is the process of defining a set of sub-classes from a superclass. Each sub-class represents a more specific instance of the superclass.
- **Example**: Consider a `Vehicle` superclass. Specialization might result in sub-classes like `Car`, `Truck`, and `Motorcycle`.

#### **b. Generalization**
- **Description**: Generalization is the process of abstracting common features from multiple classes into a single superclass.
- **Example**: If `Car` and `Truck` are two specific classes, they might be generalized into a `Vehicle` superclass.

### 7. **Relational Model Constraints**

#### **a. Domain Constraints**
- **Definition**: These ensure that the values in an attribute column must come from a predefined domain.
- **Example**: An `Age` attribute may be constrained to only accept values between 0 and 120.

#### **b. Entity Integrity**
- **Definition**: This constraint ensures that the primary key of a table must contain unique values and cannot be `NULL`.
- **Example**: The `Employee_ID` in the `Employees` table must be unique and not `NULL`.

#### **c. Referential Integrity**
- **Definition**: This constraint ensures that a foreign key value must match an existing primary key value or be `NULL`.
- **Example**: The `Dept_ID` in the `Employees` table must refer to an existing `Dept_ID` in the `Departments` table.

#### **d. Key Constraints**
- **Definition**: This ensures that a primary key or unique key constraint enforces uniqueness in the respective columns.
- **Example**: The `Email` attribute in a `Users` table might be required to be unique.

### 8. **Create a Table for Works_IN Relationship**

When creating a table for the `Works_IN` relationship, you'll typically use foreign keys to reference the related entities.

```sql
CREATE TABLE Works_IN (
    Employee_ID INT,
    Dept_ID INT,
    PRIMARY KEY (Employee_ID, Dept_ID),
    FOREIGN KEY (Employee_ID) REFERENCES Employees(Employee_ID),
    FOREIGN KEY (Dept_ID) REFERENCES Departments(Dept_ID)
);
```

### 9. **Entity Integrity and Referential Integrity Constraints**

#### **a. Entity Integrity**
- **Importance**: Entity integrity ensures that each row in a table can be uniquely identified. This is crucial for maintaining the uniqueness of records and supporting operations like updates and deletes without ambiguity.
- **Example**: In a `Students` table, the `Student_ID` should be unique and not `NULL`.

#### **b. Referential Integrity**
- **Importance**: Referential integrity ensures that relationships between tables remain consistent. If a table contains a foreign key, it must refer to a valid primary key in another table, ensuring that there are no "orphaned" records.
- **Example**: If a row in the `Enrollments` table references a non-existent `Course_ID

` in the `Courses` table, this would violate referential integrity.

### 10. **EquiJoin and Natural Join**

#### **a. EquiJoin**
- **Description**: An equijoin joins two tables based on a condition that uses equality (`=`) between specified columns. It can involve any number of columns.
- **Example**:
  ```sql
  SELECT Employees.Name, Departments.Dept_Name 
  FROM Employees 
  JOIN Departments 
  ON Employees.Dept_ID = Departments.Dept_ID;
  ```
  - **Relational Algebra**: `σ(Employees.Dept_ID = Departments.Dept_ID) (Employees × Departments)`

#### **b. Natural Join**
- **Description**: A natural join automatically joins tables based on all columns with the same name and datatype. It eliminates duplicate columns in the result.
- **Example**:
  ```sql
  SELECT Name, Dept_Name 
  FROM Employees 
  NATURAL JOIN Departments;
  ```
  - **Relational Algebra**: `π(Employees.Name, Departments.Dept_Name) (σ(Employees.Dept_ID = Departments.Dept_ID) (Employees × Departments))`

### 11. **ER to Relational Mapping Algorithm**

#### **Step 1: Map Strong Entity Types**
- **Description**: For each strong entity in the ER diagram, create a table. The attributes of the entity become the columns of the table.
- **Example**: For a `Customer` entity with attributes `Customer_ID`, `Name`, and `Address`, create a `Customer` table.

#### **Step 2: Map Weak Entity Types**
- **Description**: Weak entities rely on strong entities for their identification. Create a table for the weak entity and include a foreign key from the strong entity's table.
- **Example**: If `Order` is a weak entity depending on `Customer`, include `Customer_ID` as a foreign key in the `Order` table.

#### **Step 3: Map Binary Relationships**
- **Description**: For 1:1 or 1:N relationships, include the primary key of one entity as a foreign key in the other. For M:N relationships, create a new table that includes the primary keys of the participating entities.
- **Example**: For an M:N relationship between `Students` and `Courses`, create an `Enrollments` table.

#### **Step 4: Map Multivalued Attributes**
- **Description**: For multivalued attributes, create a new table with a foreign key referencing the original entity, and include the multivalued attribute as a column.
- **Example**: If `PhoneNumbers` is a multivalued attribute for `Customer`, create a `CustomerPhoneNumbers` table.

#### **Step 5: Map N-ary Relationships**
- **Description**: For relationships involving more than two entities, create a new table that includes the primary keys of all participating entities.
- **Example**: For a relationship among `Employees`, `Projects`, and `Departments`, create a `Works_On` table.

### 12. **Implementing Referential Integrity in SQL**

Referential integrity is implemented using foreign keys, which ensure that values in a child table correspond to valid values in a parent table.

- **Example**:
  ```sql
  CREATE TABLE Orders (
      Order_ID INT PRIMARY KEY,
      Customer_ID INT,
      FOREIGN KEY (Customer_ID) REFERENCES Customers(Customer_ID)
  );
  ```

### 13. **Relational Algebra Operations from Set Theory**

Relational algebra includes several operations based on set theory principles:

#### **a. Union**
- **Description**: Combines the results of two queries into a single result set, including all distinct rows.
- **Example**:
  ```sql
  SELECT Name FROM Customers 
  UNION 
  SELECT Name FROM Suppliers;
  ```
  - **Relational Algebra**: `R ∪ S`

#### **b. Intersection**
- **Description**: Returns only the rows that are present in both result sets.
- **Example**:
  ```sql
  SELECT Name FROM Customers 
  INTERSECT 
  SELECT Name FROM Suppliers;
  ```
  - **Relational Algebra**: `R ∩ S`

#### **c. Difference**
- **Description**: Returns the rows from the first query that are not present in the second.
- **Example**:
  ```sql
  SELECT Name FROM Customers 
  EXCEPT 
  SELECT Name FROM Suppliers;
  ```
  - **Relational Algebra**: `R - S`

#### **d. Cartesian Product**
- **Description**: Combines each row from the first table with every row from the second table.
- **Example**:
  ```sql
  SELECT * FROM Customers, Orders;
  ```
  - **Relational Algebra**: `R × S`

### 14. **Insert, Update, and ALTER Commands**

#### **a. Insert Command**
- **Description**: Used to add a new record to a table.
- **Example**:
  ```sql
  INSERT INTO Employees (Employee_ID, Name, Dept_ID) 
  VALUES (101, 'John Doe', 10);
  ```

#### **b. Update Command**
- **Description**: Modifies existing records in a table.
- **Example**:
  ```sql
  UPDATE Employees 
  SET Name = 'Jane Doe' 
  WHERE Employee_ID = 101;
  ```

#### **c. ALTER Command**

- **Description**: Modifies the structure of an existing table.
- **Examples**:
  - Add a column:
  
```sql
    ALTER TABLE Employees ADD Email VARCHAR(255);
```

- Drop a column:

```sql
    ALTER TABLE Employees DROP COLUMN Email;
```

### 15. **Basic Data Types Available for Attributes in SQL**

SQL supports several basic data types:

#### **a. Integer Types**
- **INT**: A standard integer type.
- **SMALLINT**: A smaller range integer.
- **BIGINT**: A larger range integer.

#### **b. Character Types**
- **CHAR**: Fixed-length character string.
- **VARCHAR**: Variable-length character string.

#### **c. Date and Time Types**
- **DATE**: Stores date values (year, month, day).
- **TIME**: Stores time values (hour, minute, second).
- **TIMESTAMP**: Stores both date and time values.

#### **d. Numeric Types**
- **DECIMAL**: Stores exact numeric values with precision and scale.
- **FLOAT**: Stores approximate numeric values.

#### **e. Boolean**
- **BOOLEAN**: Stores TRUE, FALSE, or NULL values.

---
