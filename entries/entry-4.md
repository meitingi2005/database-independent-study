# Week 4: Cookie and Session

#### Overview:

This week I will be talking about security and user password. Have you ever wondered how the computer keep track of your data even after you log out of your account? Last week, I learned how to let user create an username and use that username to retrieve the data from the table. In week, I want to let the user be able to login and logout from its account. So, how do we do it? The answer is cookie and session. 

##### Difference between Cookie and Session

I bet everyone heard of cookie at least once in their life(not the cookie that you can eat) while browsing through the internet. So, what is the main difference between cookie and session? I honestly was very confused when I was reading the documentation because they both have very similar function, which is to store data. From my understanding, cookie is a hash that stores information and it lives on both the browser and it is used to help identify the user’s information that is on the server. The cookie sends information back and forth between the browser and the server. On the other side, session is also a hash that lives on the server and it only stores the information at contains the user interaction on the browser. 

There are two types of cookies:
Session cookies
Persistent cookies

#### Create account and Login

First, I learned that the way computer allows the user to login is using `session[:id]`. The way you get your id is by creating entering the information such as the username and password. The computer will then access that information through the `params hash`. The `session[:id]` essentially a special id that is generated for each user. The id is created when the user first register its account and it gets store in the databases along with other information.

One thing that I learned that stood out to me was the importance of the application controller. When we first create an account, it should be in the `'/registrations'` route because that is where the user will enters its email, name and create its password. In the same route, we need to write the code `session[:id] = @user.id` because that is how the computer keeps the user login without asking the user re-enter all the information. This is important if you want the website to remember the user information without asking the user to re enter the email and password. 

In addition to the application controller, forms are another important factor of this unit. Everything that requires the user to enter something should be type in a form because we have to link the information in the form back to the controller. For example, in the form of registration where the user creates a new account, it should link back to `method="post" action="/registrations"`. 

So, you may be asking how do other pages know who the user is. The answer is that the computer will find the user using the session id such as ` @user = User.find(session[:id])`. This code should be placed in every page if you want the user status to maintain the same. 

#### Logout

Actually logging out is way easier than signing in because ActiveRecord has a prewriteen code. All we need to do is in the `get '/sessions/logout'` route, put `session.clear`. This line of code will clean out all of the data from the session hash. It does not mean your data will be forever deleted, it only means the data is cleaned out at that particular moment.


#### Takeaways:
1.
2.
