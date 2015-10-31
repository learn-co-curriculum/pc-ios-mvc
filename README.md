# Model-View-Controller

### SWBATs
+ MODEL - Understand what a model is
+ MODELS - Build a model with attributes and actions
+ XCODE - Understand why we use the SV XCODE file structure and how models fit into it
+ CONTROLLERS - Understand why we need controllers (to set up routes and connect data from models to views)
+ CONTROLLERS - Connect information from models to views via controller and instance variables
+ VIEWS - Understand why we  use instance variables in our views
+ VIEW - Understand how to use erb tags and instance variables to display dynamic information in views

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
+ In Ruby, Rails and Sinatra are two web application frameworks developers use. We'll be using Sinatra.
+ Have students clone [Interactive Simple Lab](https://GitHub.com/learn-co-curriculum/hs-mvc-interactive-practice)
  * Solution can be found [here](https://GitHub.com/learn-co-curriculum/hs-mvc-interactive-practice/tree/solution) 
+ MVC stands for Model View Controller
+ Models
  * <a href="https://www.youtube.com/watch?v=W7HNfMozWq8"> White Board MVC Resource Video</a>
  * The logic or code that goes into storing and maintaining the data in an application - like adding a tweet to your list of tweets - is the M in an MVC framework - the models.
  * The models are responsible for pulling data from database.
+ Views
  * The V in MVC stands for views and this directory is where we will store all of the HTML (and embedded Ruby) that gets displayed in the browser.
+ Controller
  * The C stands for Controller and the application controller file in our project will hold all the code that is in charge of making the back end - the Ruby logic - talk to the front end - the HTML in the browser that users interact with.
+ This MVC - model view controller - framework is the way that most modern web applications are organized.
  * Keeping the functionality of our application in these separate directories helps us stay organized as our apps become more and more complex.
+ We will be using a gem called Sinatra to set up our MVC framework and create our applications.

+ **Gemfile:** This is where we bring in Gems (open source code) that we can use in our project.
  * Create a development group - for working locally on our computer.
  * Look at the code snippet for Gemfile
  * In terminal in the directory of the project, run `bundle install` once you save the changes to your gemfile

+ **Config.ru:** This file controls the instructions that actually run our app
  * To run our application we'll need to start up a server with a tool like the `rackup` gem.
  * This file tells the server where to find an run the application

+ **Public Directory:** This holds all of the front end assets for our program. Assets include javascript, css and images.

+ **Config.ru** contains the configurations for running different parts of your app. We'll be adding the bundler gem here which makes sure that all parts of your application have access to the gems in your Gemfile.

+ `application_controller.rb`: connects your application to the Sinatra gem.
  * We need to create an ApplicationController class that inherits from Sinatra base. This gives us useful methods to help us navigate our application.
  * We need to configure our app to find our views and the public folder
  * This file controls all the routes. 
  * We make all instances of our classes from our models in this file to be able to display them in the view.

+ **Models**
    * This holds our backend code - it's where you would find a ruby class. All logic about how an object should look or act goes here. You don't make instances of your class here.
    * We will set up a `dog.rb` file.

+ **Views**
  * We will create a  `dog.erb` file here
  * All your HTML goes here.
  * To continue the dog example - you would display the dog here (like it's an online pet store) or form for user to list a new dog to sell. You don't create the dogs here.

**CONNECTING THE MVC COMPONENTS**
+ <a href="https://www.youtube.com/watch?v=vtuR74enuzY"> Get Request Resource Video</a>
+ Setting up a route in the application controller
  * The controller is like a waiter that goes between the chef cooking up the meal (Model) and the customers receiving the food (Views)
  * Routes are set up to match the URL in the navigation bar of the browser.
  * Using http://www.audiomydarling.com/ as an example.
    * When users go this URL with their browser they are triggering the '/' route
    * When they go to http://www.audiomydarling.com/fiddle they are triggering the '/fiddle' route
    * When they go to http://www.audiomydarling.com/contact they are triggering the '/contact' route

+ Demo creating GET request with a plain text response in controller (no view).
```ruby
  get '/' do
    "HEY!!!"
  end
```
+ Demo using shotgun gem to create a local server to run our application locally. In terminal, enter `shotgun -o 0.0.0.0 -p 9393` and then in browser, go to `localhost:9393`
+ Have students practice creating a new route like '/dog' and have it display texts.

+ Demo adding a view by creating an ERB file with HTML in it. Create dog.erb file in views folder and link to the controller with `erb :dog`.
```ruby
get '/dog' do
  erb :dog
end
```
+ Have students create their own views and connect them to the controller.
+ Add CSS file to the public directory and link it to ERB file.
  * In Sinatra, you don't have to link to the public directory. Any CSS file will be linked by `<link rel="stylesheet" type="text/css" href="css/style.css"> It's weird because you don't need a relative path with Sinatra.
+ Add a photo to the site through the public directory. - same rule applies as the CSS directory, you just start the path from immediately inside the public directory.
+ Add a model called `dog.rb` that has a few attributes like breed, age, and name. Explain purpose of having the model layer.
  + It allows us to create new instances of the dog class from the controller.
+ Add instance of the dog class in the `'/dog'` response and assign it to an instance variable so it can be used in the view.
```ruby
get '/dog' do 
  @dog1 = Dog.new("Fido", "Lab", 5)
  erb :dog
end
```
+ Show how attributes of the dog can be displayed in the view using ERB.
```erb
<p> I have a dog named <%= @dog1.name %>. He is a <%= @dog1.breed %>. He is <%= @dog1.age %> years old.</p>
```
+ You can add view related logic to your erb files using erb tags. Let's say you wanted to display all the dogs you created.
You could store all the dogs you created in your controller like this:
```ruby
get '/dog' do 
  @dog1 = Dog.new("Fido", "Lab", 5)
  @dog2 = Dog.new("Beth", "Golden Retrieve", 2)
  @dog3 = Dog.new("Carl", "Dalmation", 7)
  @dogs = [@dog1, @dog2, @dog3]
  erb :dog
end
```
And in your views:
```erb
<% @dogs.each do |dog| %>
  <p> <%=dog.name %> <%= dog.age %> <%=dog.breed%></p>
<% end %>
```
+ erb tags without the `=` won't be displayed. 
+ You could also use an if-statement to display only dogs who are five and older.
+ Review all the steps:
  + When we make a GET request, our controller creates a new dog object from the model. Then the controller takes that instance that has been created and passes it to our view so that we can show the data to our users in HTML.
+ Have students create another dog in the same request and have its attributes be displayed in the view.
+ Have students discuss in small groups the entire process, then create a new route, model, and view for something else, like a cat or a musician.
+ What if we have a bunch of different instances we want to display on a page? Prompt students.
+ Explain that we can have an array that stores all the dog instances, then iterate through them in the view to display each of them. 
+ Today we're going to start by working on building our final projects. We're going to start with static pages (controller and views) and then build out from there.

### Conclusion / So What?
+ Now is your chance to combine your creative and technical skills to fully express yourself with code. You have all the tools you need to make your own web application. Now you have to figure out what exactly it is you want to build. This can be one of the toughest parts, coming up with an idea that people can get excited about.

### Hints and Hurdles
<a href="https://drive.google.com/file/d/0B17rUuqpJ8atX084clB4WHM5OGM/view"> MVC Code Visual</a>
+ To use Shotgun with Nitrous enter `shotgun -o 0.0.0.0 -p 9393` to start the server of Port 9393.
+ Object orientation review will be necessary before launching into MVC.
+ If students want to know the mechanics of Sinatra, explain that it is beyond the scope of this lesson, but they can dive in further on their own. Sometimes you have to take these things for granted in the short term.
+ Have students walk through the code and explain to a partner the flow of MVC applications.
