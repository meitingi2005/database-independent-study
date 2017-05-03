# Entry 5: Starting the Final Project

### Overview:

My agenda for this week was to start my final project starting from the MVC. My to-do list was creating a migration to make the users table, creating forms for the user to type in and to set up the application controller. Before the week, I expected myself to finish up the table and create the migration and maybe some basic forms such as sign in and sign up. I knew from the beginning that this week was probably the most difficult week because I need to utilize all my knowledges from the past four weeks and it can be difficult to start from the scratch rather than following a tutorial with instruction. 

Personally, I had a relatively hard time starting off my project because the tutorials I used in the past has a different sandbox from the one I had for sinatra. For ActiveRecord, there are also new files such as the db and the Rakefile that I needed to create and connect to other files. In addition, different tutorials might have a different approach to the same solution and combining tutorials can annoying and messy.

My first two days were mainly installing gems, figuring out the best way to organize my files and let them connect to each other. I also created the users table and migrations that consist of the user’ name, email and password. Personally, setting up the migrations was not that hard once you get the hang of it and know the syntax and format just like memorizing the shotgun equation. Besides setting up the databases, I also did lots of trails and errors by testing my code along the way. I would create a form, then a table and access the table and make the column to show up on the front-end. The reason was because if I were to make a mistake in the first day without noticing it, my next couple of days to weeks might be a nightmare of debugging, which is something I want to prevent. 

One interesting thing I realized was how little Ruby code I have been writing so far. Back then in the Sinatra unit, the class mainly focused on controlling the backend using classes and instance variables. However, ActiveRecord truly saved me lots of time because it is meant to be a simplified languages. I did not have to use def initialize, or write instances variable such as @name=name or attr_acessor because ActiveRecord does all of them for you when you use databases. 

In terms of the front-end, I decided to use a simple bootstrap templet. So far, the only thing I put on the front-end is the title and the question display. 

Below is some codes that I have worked on this week: 

```
class CreateQuestions < ActiveRecord::Migration
  def up
  	create_table :questions do |t|
  	  t.string :username
  	  t.string :status
  	end
  end
  
  def down
    drop_table :questions
  end
end
```

```
class ApplicationController < Sinatra::Base
  
  
  configure do
    set :public_folder, 'public'
    set :views, 'app/views'
  end	
	
  get '/' do
    @questions = Question.all
    erb :index
  end
  
  get '/question' do
	  erb :question
	end
	
  
  post '/question' do
  question = Question.new(:username => params[:username], :status => params[:status])
  question.save
  redirect '/' 
end

end

```

```
class CreateUserTable < ActiveRecord::Migration
  def up
    create_table :users do |t|
      t.string :name
      t.string :email
      t.string :password
    end
  end

  def down
    drop_table :users
  end
end

```

This week was more about me trying to figure out the layout of the website and the relationship between each files. At this point, I am trying to learn how to let user to comment on a specfic post from a particular user. I have been reading documentations and some other articles to try to understand the concept. My goal for next week is to let user to click on a post and be able to comment on it. 

My thought process is that the user will click on the question that they want to answer, then the computer will bring it to a new page with the question and a form for it to put the answer. In order to do so, the computer will have to access to the information of that post through the owner of the post. Then the user's answer will be displayed underneath the question. My problem is how am I going to display that answer under the question. 



### Takeaways:

1. Trial and Error-Test your code along the way!!! Just like how chef should always taste their food before they move on to the same stage, a programmer should test its code after every other lines to make sure you have no mistakes. If you do this and find out you made a simple syntax error, you can fix it right away.
2. Be organize and don't be afaid to restart the project if the code is too messy. Personally, the entire table, databases, app controller and different erb files got me very confused because I am still learning the layout. I have written the wrong code in the wrong file once and the code was not working because I did not organize the files the way it supposed to be. I used the twiiter example as my sandbox and restarted the entire code with the correct structure. 



