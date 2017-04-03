# Week 2: ActiveRecord and Migration
#### Overview:
Last week I learned the basic of SQL and the syntax to manage a table. This week, I decided to learn about the basic of ActiveRecord and the setup of it. Similar to sinatra, ActiveRecord requires a specific setup in order to work on both the front and backends. 

##### So, what is ActiveRecord?

In a professional definition, ActiveRecord is Object-Relational Mapper (ORM) that is written in Ruby. It allows us to interact with the databases using simple ruby code. ORM basically means each class is organized using rows and each instance of the class is represented in a row. ActiveRecord mostly has four main functions: CRUD(Create, Read, Update, and Delete).From what I’ve learned this week, ActiveRecord is a simplified version of SQL. <br><br>
Below is some basic conversion from SQL to ActiveRecord that I took from a github repo:<br>

| SQL | ActiveRecord |
|----	|----- |
|SELECT * FROM cats;| Cat.all|  
|SELECT name FROM cats;| Cat.pluck(:name)| 
|SELECT * FROM cats <br> WHERE name = "Maru";| Cat.where(name: 'Maru')|
|SELECT * FROM cats <br> WHERE age > 2;| Cat.where('age > 2')|
|UPDATE cats SET name = "Hana" <br> WHERE name = "Hannah";| hannah = Cat.where(name: 'Hana') <br> hannah.name = "Hannah" |
|DELETE * FROM cats <br> WHERE id = 3;| Cat.destroy(3)|

<br>
As you can see, the SQL and ActiveRecord can do the same job as for creating or manipulating tables. But ActiveRecord is just shorter and more convient to write. 
<br>
##### what is Migration?

The first thing I learned from ActiveRecord is the importance of setting up “Migration”. So, I was first confused about what migration is because the term migration means moving on. On one of the documentation, it says migration is a way to keep track of all the changes that is being made. The way migration is structured is using the up and down methods. The way the documentation called that helped me alot was “do” and “undo”. In other words, you will create a table in the “up” method and if there is a time you want to go back to the preview changes, you call the “down” method. Think of migration as git commit and uncommit.
<br>
To setup Migration, you will need to create a new file and it will consists of the up and down file. Also, you will need to add `< ActiveRecord::Migration` as an extention to your class(the one that creates the table)<br>

```
class CreateAnimals < ActiveRecord::Migration
  def up
  end

  def down
  end
end
```
So, the tricky thing about Migration from I've known so far is that there need to be mutiple migration files because each file is responsible for a specific change. So, a tip that I learned is to use number to keep track of your migration files. 
Migration is helpfil because if one day you want to get rid of all the new changes you made to the databases, you just need to execute the down method and everything will turn back to the orginial form. 
<br>

Another feature that ActiveRecord provides that is extremely helpful is the command called “rake -T” where the computer will list all the commands you have called in the command line. 


<br>
##### Takeaways:

1. Naming is super important because it will tell you the chronological process of the code. When naming a file, you should create a name that will tell you what the file inside is without even opening it. In ActiveRecord, there are lots of files or classes that will responsible for differnt parts of your progam. As a result, do name them wisely!
2. The beginning part of a new unit can be very boring, but just keep in mind that you can't make anything complicated without the basic/setup. 


Here is a naming conversion that I found on GitHub that I think is helpful for organization:

| Type            | Example                   |
|-------          | ----                      |
| Class file      | `Animal.rb`               |
| Class           | `class Animal`            |
| Table           | `create_table :animals `  | 
| Migration       | `01_create_animals.rb`    |
| Migration Class | `class CreateAnimals`     |


##### Credits:
https://github.com/learn-co-students/activerecord-migrations-pc-jastor-120215/blob/master/README.md
https://github.com/learn-co-students/activerecord-intro-pc-jastor-120215/blob/master/README.md