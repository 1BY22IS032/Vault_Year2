# ADV SQL Queries

## Nested Queries

```SQL
SELECT DISTINCT PNUMBER 
FROM PROJECT
WHERE PNUMBER IN (SELECT PNUMBER FROM PROJECT ,DEPARTMENT,EMPLOYEE WHERE Dnum = Dnumber AND Mgrssn = ssn AND Lname = 'Smith')
OR 
PNUMBER IN (SELECT PNo FROM EMPLOYEE,WOrksOn WHERE Essn = ssn AND Lname = 'Smith');
```

```SQL
SELECT Lname , Fname FROM EMPLOYEE AS E and DEPARTMENT AS D WHERE E.ssn=D.ssn AND E.Sex = D.Sex AND E.Fname = D.DependentName
```

## Exists And Unique Keywords

```SQL
SELECT E.Fname , E.Lname FROM EMPLOYEE WHERE EXISTS (SELECT * FROM DEPENDENT AS D WHERE D.Essn = E.ssn AND D.sex = E.Sex AND E.Fname = D.DependentName)
```

```SQL
SELECT E.Fname FROM EMPLOYEE AS E WHERE EXISTS()
```

## Assertions and Triggers

- We use CREATE ASSERTION keyword
- to add additional constraints outside the scope of built in functions
- Can be specified in the CREATE TABLE statement of SQL

```SQL
CREATE ASSERTION SALARYVIO CHECK(NOT EXISTS (SELECT * FROM EMPLOYEE E AND EMPLOYEE M AND DEPARTMENT D WHERE M.SALARY > E.SALARY AND E.Dno = D.DNUMBER AND D.Mgrssn = M.ssn))
```

- Constraint name can be used to modify or drop later
- whenver the constraint is deemed to be false, it is violated.
- to create an assertion, create a tuple that violates the constraint and put it inside a NOT EXISTS clause.

### Triggers

- Triggers are used to execute or determine the actions to be taken after a perticular event or conditions are satisfied
  
```SQL
CREATE TRIGGER <NAME>
(AFTER/BEFORE) <EVENT> ON <TABLENAME> [FOR EACH ROW]
[WHEN <CONDITION>]
<TRIGGER ACTION>
```
