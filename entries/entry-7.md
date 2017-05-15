# Entry 7: Working on the project

### Overview: 

In week 7, I started to work on the actual book-o-mmender by linking the signup and signin pages to the website. As I stated previously, I already wrote the code for the forms and the migration for them. All I need to do at this point was to link them on the website and make sure they work with other parts of the program. Throughout the process of adding onto my old project, I faced mutiple difficulties because some of the ActiveRecord code did not work well with my previous Ruby code. Even though they are both using ruby as the primary language, I had to make a lot of changes to fit in ActiveRecord. It could be my own problem that it took me so long to just merge the two codes together but I guess I will work in a faster pace as I become more familar with the code.

#### Tinkering: Linking files together to make the signin and signup forms to work

Overall, the process of writing migration and making forms was not that difficult becasue they are pretty straight forward. I did successfully make the signup and signin links appear on the website and I tested them out and they worked. However, when it comes to linking the files together I had lots of troubles because I could not rely on existed code. Before doing anything, I find it very helpful to duplicate your project and use the duplicated version as your sandbox before altering your actual project. This is because if I mess up with something on the previous code, then I will have to debug that and that will take extra time.

#### Tinkering: Adding books into the wishlist

What I learned in the process of tinkering was that each user will have its user session id, which is generated in the table, and each new book will have its own book id. Therefore, there will be two different migrations (create users and books). The users table should consists of username, email and password. The books table should consists of book_title, author, image link and everything that is in my class Book initialize method becasue migration will take care of that without you writing it again in the class. One problem that I came across was figuring out where to put my api key and secret because `def initialize` will not exist anymore. My thought process was that the api key and secret should belong in the user class because the user needs the key to access to goodreads books.  

My tinkering work in the User class:
```
class User < ActiveRecord::Base
  validates_presence_of :name, :email, :password
  has_many :books
  
  def create_client 
      self.client = Goodreads::Client.new(api_key: "apl03Pv1Wh1qnhUF6iuwQ", api_secret: "m7bx1HSNHdMD36wUP7jhIyucmgt1gGpAnQJGkh7erY") 
  end
end

```
I decided to use `self` to represent the current user because I thought each user should be a new client of goodreads and owns it set of book. I'm not completely sure whether this is correct or not so that is going to be the next step of my project. 
<br>
Book class
```
class Book < ActiveRecord::Base
    belongs_to :user
```
The `has_many` and `belongs_to` are how we connect the two classes together.


Another problem that I came across was that after the making the migration for the books and starting to add columns such as book_title using `t.string`, I realized that some of my columns aren't string and that they are empty array. What did I do? GOOGLE! I learned that in your migration, you will still use `t.string` but in your model, you will use 
`serialize :similar_books` to represent an empty array. 


Some possible solutions that I thought about this week:
1. when the user clicks the add button, a new instance of the book will get generated which means it will have its own book id and then I can grab the book id and push it into an empty array that will later get displayed in the wishlist page. 
- Issue: If I do this then I will have to change my entire model.rb because I included the part of making a new instance of each similar book in one of the method. I will have to move that part into the controller and I have to make a relationship between the book and the user. 

2. Another way that I thought of but have not tested was simply pushing the title, image and author name of the book into an empty array when the user clicks the button. 
- Issue: I personally don't think this will work because even if we push the book into the array, the array will not belongs to anyone because it is not connected to the user id.

My conclusion is that in order to make this work, I will have to somehow link the user id with the book id. 

### Takeaways:
1. **It's okay for your code to be messy in the beginning.** This week has honestly been the most confusing week in this unit because I was still trying to merge the code and tons of error messages pop out. Since ActiveRecord is reponsible for the backend, I can really see the result on the website until it is finish which can be annoying. However, debugging is a process that every engineer goes through when creating a new project so don't be afraid. My suggestion to you all is to always make a backup of your project(especially if you are adding on to your previous project like me) and write your new code there so even if you mess up on the new one, you still have a backup. 
2. **Do ask for help if you need do!** There are still lots of things I haven't learned about my topic so if you don't understand something on your project, ask someone or google yourself. But asking for help will never hurt you and I personally find it helpful when someone explain a concept to me and that I can ask questions back. 