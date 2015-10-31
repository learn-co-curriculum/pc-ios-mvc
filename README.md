# Model-View-Controller

### Motivation / Why Should You Care?
+ All along, we've been doing something pretty special, and its important that we don't take it for granted.  Let's talk about the difference between a website, and an application.  An application allows for meaningful, dynamic interaction between user and app.  In other words, in a website, the data is generally static (think of a pizzaria website), whereas in an application, data is can be updated on a daily basis, or even a second-to-second basis (think Instagram or Twitter).  

In order to build an application, you need three components:
1. The visual design of your application — the frontend, or view.
2. Where your data and logic live — the backend, or model.
3. A way for your frontend to talk to your backend, so it can change dynamically accoridng to what the user wants — your controller.


+ 
+ From Apple Docs: 
+ Model Objects Encapsulate Data and Basic Behaviors
`Model objects represent special knowledge and expertise. They hold an application’s data and define the logic that manipulates that data. A well-designed MVC application has all its important data encapsulated in model objects.`
+ View Objects Present Information to the User
`A view object knows how to display, and might allow users to edit, the data from the application’s model. `
+ Controller Objects Tie the Model to the View
`A controller object acts as the intermediary between the application's view objects and its model objects. Controllers are often in charge of making sure the views have access to the model objects they need to display and act as the conduit through which views learn about changes to the model.`


### Lesson Plan
**HOW WEB APPLICATIONS WORK**
+ The front-end and back-end of websites are connected by a structural system known as MVC.
+ XCode provides a built-in way for us to use create an MVC app when we create a project.  
+ MVC stands for Model View Controller
+ Models
  * The logic or code that goes into storing and maintaining the data in an application - like adding a tweet to your list of tweets - is the M in an MVC framework - the models.
  * The models are responsible for pulling data from database.
+ Views
  * The V in MVC stands for views and this directory is what is on our Main Storyboard.
+ Controller
  * The C stands for Controller and the application controller file in our project will hold all the code that is in charge of making the back end - the Swift logic - talk to the front end - the objects that live in our Main Storyboard.
+ This MVC - model view controller - framework is the way that most modern web applications are organized.
  * Keeping the functionality of our application in these separate directories helps us stay organized as our apps become more and more complex.



  * We need to create an ViewController class that inherits from Sinatra base. This gives us useful methods to help us navigate our application.
  * We make all instances of our classes from our models in this file to be able to display them in the view.

+ **Models**
    * This holds our backend code - it's where you would find a Swift class. All logic about how an object should look or act goes here. You don't make instances of your class here.
    * We will set up a `Task.swift` file.

+ **Views**
  * We will create a  `main.storyboard` file here
 

**CONNECTING THE MVC COMPONENTS**
  * The controller is like a waiter that goes between the chef cooking up the meal (Model) and the customers receiving the food (Views)


### Conclusion / So What?
+ Now is your chance to combine your creative and technical skills to fully express yourself with code. You have all the tools you need to make your own web application. Now you have to figure out what exactly it is you want to build. This can be one of the toughest parts, coming up with an idea that people can get excited about.

+ Have students walk through the code and explain to a partner the flow of MVC applications.
