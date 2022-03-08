# MySQL Part 0 - The Database

## What is?
Database is basically a collection of databases. It is, again, of course a super simplification explanation, but we will stick to it. Maybe it won't be true for later when we learn NoSQL databases, but the idea is the same. It's a bunch of tables that might or maybe not related to one another.

## How to - Create Database

## How to - Delete Database

## How to - Use Database

## What is - Data Types

## How to - Create Table
Creating table is actually pretty straigtforward, just like how we crete database.<br>
The command for creating new table is<br>
`create table <tablename>`

With the data types in mind, and like we said earlier, that we need to define the data type beforehand, the create table would possibly looks like this<br>
```
create table simple_user (
	name varchar(100),
	age int
);
```
**NB: it is important to note that the consensus for table name would be the model/object in plural. So the example above should be `simple_users`.**

## How to - Delete Table
You probably already figure it out. We can use the `drop` for deleting table also. The query is pretty much the same<br>
`drop table <tablename>`

## How to - Inserting Data
Once we created the table, we can now move to on how we are going to add data to the table.<br>
The query for this action would look like this<br>
`insert into <tablenames>(<a list of columns name>) values(<a list of values, respectively inline with the columns>)`

Of course, if we want to add multiple data, we can do the above query multiple times, or<br>
```
insert into <tablenames>(<a list of columns name>) values(<a list of values, respectively inline with the columns>), (<a list of values, respectively inline with the columns>)
```

In this case, the example would be
```
insert into simple_users(name, age) 
    values
        ('fabs', 26), 
        ('buzz', 25);
```

## How to - Primary Key
By using primary key, we guarentee that our data, that almost identical (lets say, simple_users has 3 data with 3 same name, but different age for 1 data only <bas, 29>, <bas, 30>, <bas, 30>. If we want to get <bas, 30>, we will ended up getting 2 data instead of one)

To tackle this, we use, or we add another column, that will be the ID, or Primary Key for every data. The example would be like this
```
CREATE TABLE unique_simple_users
(
    id INT NOT NULL,
    name VARCHAR(100),
    age INT,
    PRIMARY KEY (id)
);
```