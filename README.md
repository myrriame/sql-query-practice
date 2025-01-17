# sql-query-practice


### Round 1

Connect to the LikeyPix database in Beekeeper, and answer the following questions:

1. Write a query that returns all Users

```
SELECT * 
FROM users
```
2. Write a query that returns all Posts

```
SELECT * 
FROM posts
```
3. Write a query that returns the count of all Posts

```
SELECT count(posts) 
FROM posts
```
4. Which Post had the most Comments?
``` 
select count(*) as num, post_id from comments
    group by post_id 
    order by num desc
    limit 1;

    post 1
```
5. Write a query that returns the Post which had the least Comments


Paste your query below:

```
select count(*) as num, post_id from comments
    group by post_id 
    order by num asc
    limit 1;
```
6. Which User has the most Comments?
```
select count(*) as comments, user_id from comments
    group by user_id 
    order by comments desc
    limit 1;

    user 1
```
7. Write a single query to get all of the Posts and their Comments (You'll see the same Post repeated in the results)

```
select * from comments
join posts
on comments.post_id = posts.id;
```

### Round 2

- Disconnect from the `likeypix` database connection
- Connect to the `classroom` database connection

1. Write a query to get the first name, last name, and github URL for every Student in the `students` table

```
select first_name, last_name, github_url from students
```

2. Write a query to get a list of Students who do not have a LinkedIn URL

```
SELECT first_name, last_name
FROM students
WHERE linkedin_url = '';
```

3. Write a query to get a list of Teachers with the "Teaching Assistant" Role

```
SELECT * from teachers
join teacher_roles
on teachers.teacher_role_id = teacher_roles.id
where name = 'Teaching Assistant';
```

4. Write a query to get a list of Students, and their Class' `slug`

```
SELECT first_name, slug from students
join classes
on students.class_id = classes.id
```

5. Write a query to get the length of every students First Name

```
select first_name, length(first_name) from students;
```

6. What is the ID of the Student with the longest Last Name?

```
select last_name, length(last_name), id from students
order by length desc 
limit 1;

id 8
```

7. Write a query to get a list of Students in reverse alphabetical order of First Name

```
select first_name from students
order by first_name desc;
```

### Round 3

- Disconnect from the `classroom` database connection
- Connect to the `food` database connection

This Round is going to require you to get curious about your surroundings. At some point in your path as a developer, you will work on a project that already has an existing database. That database may be quite old, or have been built on a different set of standards.

These questions will be focused on exploring an unknown database that does not follow the standards we have established in class. See if you can work out answers to the following questions:


1. What table contains information about individual food items? 

```
food_des
```
2. Using the table from the previous answer as your starting point - what table do you think contains Food Group information about individual foods?

```
fd_group
```

3. Write a query to get the name of a food, and its corresponding food group name 

```
select shrt_desc, fddrp_desc from food_des
join fd_group
on food_des.fdgrp_cd = fd_group.fdgrp_cd
limit 1;

```

4. Identify the table that has information about data sources


```
data_src

```
5. Using the table from your previous answer, write a query that will get the oldest data source

```
select datasrc_id, year from data_src
order by year asc;

```

6. How many foods contain "Egg" in their description?
```
select count(*) from food_des
where long_desc ilike '%egg%';

total: 101
```
7. Write a query that will return a count of foods in each food group

```
select count(fd_group.fddrp_desc), fd_group.fddrp_desc num from food_des
join fd_group
on food_des.fdgrp_cd = fd_group.fdgrp_cd
 group by fd_group.fddrp_desc;

```
