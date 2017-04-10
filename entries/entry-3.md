# Week 3: Create User Account

#### App idea:

In this week, I began to brainstorm ideas of apps I will be making for this unit. I have always wanted to an app that will benefit students so I was browsing through different websites for inspiration. One website that I think would be helpful is a college office version of answer.com. Even though students can always email the college counselor for answers, I still think it would be helpful if other students could see each other questions since most likely the questions are going to repeat. My app idea is that students and counselors will create an account and students can post questions and counselors or students can answer them online. This is helpful for even lowerclassmen because it allows them to learn about the college process before entering their junior years. 

#### Overview:

What I learned in this week was how to setup an user account user ActiveRecord. A huge functionality of ActiveRecord is store information using a table. By using a table, we will be able to store user’s name and password on a table. 
The way I learned how to create a user account was through the "Sinatra-Fwitter", which is basically a fake twitter that allows user to create account and post tweets. 

#### Rake:

Before writing actual code, we need to install certain gem in order to use ActiveRecord. Gems such as `"activerecord"`, `"sinatra-activerecord"` and `"rake"`.
Remember how we talked about Migration last week, in order to execute the different methods or to create tables, we need to create a `Rakefile`. Rakefile stands for "Ruby Make" and it helps create the database and tables. Within the Rakefile, there will be prewritten code that we can run to complete certain tasks. The way I describe Rake is like git command. So like git touch, we would use `rake db:create_migration` to start a new migtation. Basically, the git get replaced by the rake! <br><br>
Below is a list of tasks that you might use during database.

```
rake db:create              # Creates the database from DATABASE_URL or con...
rake db:create_migration    # Create a migration (parameters: NAME, VERSION)
rake db:drop                # Drops the database from DATABASE_URL or confi...
rake db:fixtures:load       # Load fixtures into the current environment's ...
rake db:migrate             # Migrate the database (options: VERSION=x, VER...
rake db:migrate:status      # Display status of migrations
rake db:rollback            # Rolls the schema back to the previous version...
```
#### Relationship between the Model and Migration: 

In order to set up the user's table, we need to use iteration in the up method that we created in the Migration file. What needs to be interated is up to you such as username, email, passowrd and etc. When a new instance is created, the information will show up in the table. But, how do we connect the migration with the class? The answer is that the computer will do it if you name the two files correctly. The name of the class should always be singular whereas the name of the migration should be pural. For example, if the class name is User, then the name of the migration will need to be users.<br><br>

Below is the code of a users migration:
```
class CreateUsers < ActiveRecord::Migration

  def up
    create_table :users do |t|
      t.string :username
      t.string :email
    end
  end
  
  def down
    drop_table :users
  end

end
```

Below is the code for the User class:
```
class User < ActiveRecord::Base
end
```
Another important feature of ActiveRecord is that there are many build in methods we can use to replace Ruby code. For example, when we only use ruby, we need to use attr_accessor to allow access to motify the mode, create a method called initialize and to use array to store information. The most useful and convient part of ActiveRecord is that we can use the table we created in Migration to get all access to information and the new instance will get initialized in the migration stage. Magical right!

So, how do you make the text or user show up on the front-end? This is exactly same as what we need for sinatra. We need to iterate the column and print out the one that belongs to that particular user on the sceen. 

#### Takeaways:

1. Never rush learning something because if you don't understand one part, we will likely to not understand the entire program. For example, when I was doing the user account setup, I had to go back to migration because it is closely connected to the models. So, be patient and refer back to your old notes if nesscary.
2. Once you finish a new lesson, try to start from the beginning to see if you can explain how each part work with other parts. What I did was start from the gem install part because that was the first part in the backend to making the text show up on the frontend. That way I can move to the next stage without getting all confused. 
