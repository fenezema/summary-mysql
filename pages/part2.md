# CRUD Operations(More in SELECT and WHERE Clause)

## How to - Limit
Limit is the one we use when we want to, well, limit the search into n spesific number.<br>
Let's say that we want to query `unique_simple_users` data with name `fabs`.<br>
```
select * from unique_simple_users where name = 'fabs';
```

This query will show 3 data with name `fabs` respectively. But in this example, we only want to get one data, whatever the id is fine. So what do we do?<br>
First, because we don't care about the id, we can always get one by replacing the where clause with id instead
```
select * from unique_simple_users where id = 1;
```
Pretty simple? Yes, very simple

But the thing is, we don't know the id, and the only thing we can do is by using the first query and search by name.<br>
Again, because we don't care about the id, now we can use limit in action
```
select * from unique_simple_users where id = 1 limit 1;
```

This query is now ensure that we will only get one data regardless what the actual results are when we don't specify the limit.

## How to - Order
With `unique_simple_users`, let's say we want to show all the users we have, but ordered by name, ascending. We can simply achieve this by<br>
```
select * from unique_simple_users where id = 1 order by name asc;
```

As how the query written, it's pretty self explanatory. The clause for ordering data is `order by` followed by column name, and the order, ascending (asc) or descending (desc).

## How to - Search Based on Substring
Before we dive into search based on substring, first, add a few data beforehand.<br>
```
insert into unique_simple_users(id, name, age) values(5, 'Torz Fabs', 25),(6, 'Rena Fabs Lena', 24),(7, 'June Buzz', 25), (8, 'Buzz Overwatch', 24);
```

Now, let's dive into this. Let's say we want to search a user. We know that his/her name has `fabs` in it, but we don't which one.
So, based on previous section, if we<br>
```
select * from unique_simple_users where name = 'fabs';
```

This query will only show users with name `fabs`. This is not what we hope for, because we know there are other users, that let's say, have `fabs` as their middle name.

To tackle this, we can use like as the comparator, instead of `=` which basically run a match, instead of checking if the query substring is in the full string.
```
select * from unique_simple_users where name like '%fabs%';
```

Did you see that? Instead of just `fabs`, we pass in `%fabs%`. This is the key to find if a substring is inside a string. By adding `%` before and after the string query, we tells MySQL to search for user with name that contains string `fabs` instead of searching for user with name `fabs`.

Again, if the substring is actually prefix and we only look for users that has name that starts with `fabs`, like `fabslala`, or `fabsdudu`, the string query will be `fabs%` instead of `%fabs%`, because we know for. Vice versa if the fabs is postfix.

## How to - Aggregate
There are so many aggregates function is MySQL that are ready to use.<br>
For example, there is `COUNT()` that we definitely will use a lot in real world application, either it's just for counting, or even pagination (you see, the numbers in the buttom of a website that we see a lot)

```
select count(*) from unique_simple_users;

select max(age) from unique_simple_users;

select min(age) from unique_simple_users;

select avg(age) from unique_simple_users;
```

Of course the above example is the most basic example. But the idea is the same. Again, we can get creative with this.<br>

Let's say, we want to get all users that are older than the average age of all users. (this section will also introducing sub query)
```
select * from unique_simple_users where age > (
    select avg(age) from unique_simple_users
)
```

The query above also introduce the use of sub query. You can see that the where clause value was from another query. This is one of the example on how we can get creative with sql.