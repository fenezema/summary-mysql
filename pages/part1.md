# CRUD Operations

## Intro
CRUD is actually stands for Create, Read, Update, and Delete. This is the basic operations that happens every time in any app that involves databases. 

## How to - Create
We already cover this in the previous section. The query for this action would look like this<br>
`insert into <tablenames>(<a list of columns name>) values(<a list of values, respectively inline with the columns>)`<br>
See example below
```
insert into unique_simple_users(id, name, age) values(1, 'fabs', 25),(2, 'fabs', 24),(3, 'fabs', 25), (4, 'buzz', 24);
```
Note that based on this create query, the next example in sections below will be based on this example.

## How to - Read
Read, or should we say get data from a table can be done by<br>
`select * from <tablename>`<br>
Here's a bit explanation on the query above.
1. `select` is the clause or query to indicate that we want to get data.
2. `*` is actually indicates that we want all columns to be shown. A variation for this, we can specify spesific column, let's say we only want to get the name from table `simple_users`, the query will look like this `select name from simple_users`.

That pretty much it (sort of). Now, let's say we want to get a spesific data, and not all data, because, the real usage will be like this.<br>
This is where the `where` clause will be handy. The `where` clause basically tells us that we want to get data from a table, only if requirements are met.

So, from our `simple_users` example, let's say we want to get a user with name `fabs`, we can do something like this<br>
```
select * from simple_users where name='fabs';
```

And again, you can get creative with it. If you want to search for user with name `fabs`, with age is greater than 10, we can actually do it like this<br>
```
select * from simple_users where name='fabs' and age>10;
```

Pretty neat right?!

## How to - Update
Now, we already create, and get data. The next thing we're going to do is `update`. So, **IMAJEEN** that user `buzz`, wants to change his name into `buz`. We can do the following<br>
```
update unique_simple_users
    set name = 'buz'
    where name = 'buzz';
```

## How to - Delete
Delete is when we want to remove a certain data from the table. Just like `select` and `update`, we can chain this query with `where` clause, thus making the query specified into a few or one selected data. We can delete data by<br>
```
delete from unique_simple_users where id = 1;
```