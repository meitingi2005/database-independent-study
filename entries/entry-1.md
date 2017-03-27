# Entry 1: SQL Basic 
### Overview: 
<p>When I started to reserach about databases, I came across two types of probleming languages that help manage data in an organized way, SQL and Activerecord. I will learn about Activerecord next week, but bascially Activerecord allows user to write cleaner code without writing the long SQL syntax. However, I decided to learn the basic syntex for SQL because SQL is the foundation for Activerecord so that learning SQL will give me a better understaanding when I start learning Activerecord. </p>

### What is SQL?
SQL stands for Structured Query Language. It was created in the early 1970s by Donald D. Chamberlin and Raymond F. Boyce, who were part of the (IBM). Basically, SQL is a programming language that allows user to access, manipulate and store data in the database. Within the databases, the user can also create, delete and motify the data, which is commonly presented in a table form. 

### What is table?
<p>Have you ever wondered how the computer keep track of your data or how Facebook manage millions of user data? The answer is probably table. For most cases, we will be using Relational Databases for this unit because of its structure. Relational Databases is very simple, it consists of one or more table and each table is made out of row(s) and column(s). An example is the "Customers" table below.  </p>
<img src="../photo/sql2.jpg"/>

Table is such an important and helpful tool for programmer especially when you want to keep track of data using rows and columns. Personally, my goal for the final project is to be able to take in user's data and store in in the table so that the user itself can look at it at the end. 
### Common commands for SQL
Before begin explaining what each commands can do, below is a list of major SQL commands that you will use to access, motify and manage your databases. 

- SELECT
- UPDATE
- DELETE
- INSERT
- WHERE

When I was learning how to create a table, I decided to learn the basic SQL commands first because I wanted to know what kind of function does SQL provides. The result was that the syntax for SQL was fairly easy and powerful as long as you remember the key commands. 

##### SELECT: <br>
While I was going through different SQL tutorials, I realized that all tutorials always start with the SELECT command because that is how you can view your table. The SELECT command is by far the most important command for SQL because it is how you will get access to the data in the databases. In order to select an specific data from the databases, the code is 
`SELECT * FROM table_name;` <br><br>
Below is the result for the SELECT command:

<img src="../photo/sql3.jpg"/>


`SELECT` is very helpful if you want to take a look of your table to make sure everything is at where they supposed to be. 
##### UPDATE:
The UPDATE command is used when you want to replace old information in your data with new values. <br>
```
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```
##### DELETE:
The DELETE command is used to delete specific data from the existing table.
```
DELETE FROM table_name
WHERE condition;
```
##### INSERT: <br>
The INSERT command is used to add new information to your table. The way you have to do is to start with INSERT INTO and specify the name of your table and the column the information will be added, then use VALUES and specify the new informations you want to add. Remember, the column and new value need to be into the same order!
```
INSERT INTO table_name (column1, column2, column3, ...)
VALUES (value1, value2, value3, ...);
```
PS: The main difference between insert and update is that update will replace old information with new info, whereas insert will just add new information to the existing table. 
##### WHERE: <br>
If you want to select specific data in a particular table, you can use the WHERE command to fiter out certain information. It acts like a conditional statement. 
 
``` json
SELECT column1, column2, ...
FROM table_name
WHERE condition; 
```
In addition, you can use `AND` and `OR` if you want to include more conditions.
 
So at this point of learning, I personally feel like SQL is actually easier than I imagined. Similar to Ruby, the syntax for SQL does exactly what it looks like. If you want to delete something, you will have to the DELETE command. 
 

#### Takeaways:
1. The best way to learn SQL is to create a simple table on your terminal. I started by only reading the documentations and it was confusing because I could not picture the table on my head. So, make a table and add some rows and columns of anything you want. 
2. Learn the basic first before making something very complicated. Once you know how to make a simple table, the rest will be very easy. But if you don't even know how to create a table, you will never know how to add data into the table. Don't rush, be patient!
3. Go through at least 2 to 3 documentations first before sticking to one because some tutorials can be more complex than the others. 
4. All commands start with uppercase!
5. Always use `SELECT * FROM table_name;` to make sure you type in the correct comands. Treat it as a git status command to keep track of your data. 