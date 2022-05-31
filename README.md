# Create a table

```sql
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
```

# Filter String

```sql
-- only want values
SELECT right('Linestring ZM(-84.44 33.634 800 1642028771463, -84.44 33.63508 1200 1642028794402)',-14)

-- remove brackets
SELECT btrim(right('Linestring ZM(-84.44 33.634 800 1642028771463, -84.44 33.63508 1200 1642028794402)',-14),'()')

-- get individual values
SELECT split_part(btrim(right('Linestring ZM(-84.44 33.634 800 1642028771463, -84.44 33.63508 1200 1642028794402)',-15),'()'),',',1) as data_1
```
