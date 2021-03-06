#AngularJS
In this lesson we're going to be looking into AngularJS (commonly referred to as just "Angular"), an open-source framework that was released in 2009. It is currently being mainly maintained by Google as well as a massive community of developers.

It aims to solve the problems faced when creating single page applications - we'll talk all about them shortly.

Ever wondered how Facebook can have a different timeline for millions of users? How Twitter can display tweets for 300 million people? How Gmail can let you send and receive emails, chat with your friends and view your contacts without having to even refresh the page? That's where frontend frameworks come in.

Frontend frameworks have grown massively in the last 3 years. They help developers structure their applications and create interactive, super quick applications.

Before we had the pleasure of using frontend frameworks, code would be written very procedurally. JavaScript code would become unwieldy as there was no easy way to structure code for each page that the client would see.
  
You'd be limited to just simple JavaScript interactions, such as submitting a form via AJAX. Anything more wouldn't have been scalable, resulting in a hard to debug/manage codebase.

You might be wondering what we're talking about when it comes to scaling your application. Imagine we have a simple To-do application -- the user can add/remove to-dos from a list. We'd take the initial data (previously saved to-dos) and display them in a list. Then, when the user adds another to-do, we just append another list element to our list.
 
What if we change the HTML structure of our list? Well you'd better make sure that you update both the code that displays the previously saved to-dos and the code that adds our new to-do to the list - else things could become out of sync quickly. Now imagine you had a lot of code, not necessarily structured correctly, that does similar things that our to-do app does. Not only are we repeating ourselves twice, but just by forgetting to update our code in one place would result in a bad user experience and an out-of-sync UI.

That's where frontend frameworks save the day! Imagine being able to write complex JavaScript applications, having a framework deal with scaling your code, splitting it out into logical chunks and not have to worry about one part breaking another... Sounds like a dream! Oh wait... Angular does that for us!

What else does Angular give us? Components! Using a simplistic API (more about that soon!) we can quickly create components that can be reused throughout our whole application -- this allows us to code both faster and smarter!

### Traditional Rendering
Before mainstream JavaScript usage, the server would do everything for us. When we'd go to a website, everything we needed on that page would be given to us there and then. For instance, if you go to http://wikipedia.org, the server loads the content and sends it back to us.

The problem with this is that data displayed on the page could only be updated when the user refreshes. This also meant no smooth transitions between pages (every page the user navigated to would be reloaded in the web browser).

We'd also then have all of our frontend logic mixed in with the backend logic -- possibly resulting in a horrible mess of spaghetti code!

### The role of Angular
Angular brings power to the frontend, handling routing as well as all of our pretty, interactive views. This allows frontend developers and backend developers to focus on their areas -- there's no need to mix code between the two.

### Code Architecture

Angular promotes correct and consistent code architecture by splitting our code up for us into logical chunks. By then having different folders and files for these chunks, it enforces clean and structured code.

### Dynamic Views
Angular allows us to write powerful applications straight out of the box. It attaches onto the disadvantages that static web pages have, giving us the ability to write dynamic views that are constantly updating. 

How does it do this? By implementing more features into HTML! With the use of Angular, we can have dynamic lists repeating, elements hidden and shown dynamically and much much more -- just by writing our HTML (with a few, simple modifications that we will come onto soon!).

### Back in the Stone Age
Before Angular, we'd generally use jQuery to make all of our AJAX requests, as it gave us a cross-browser implementation (there used to be no standard way of making AJAX requests!). This was great, but you were left to fend for yourself to do stuff (like update your view, or display error messages, etc.) after the request had been completed.

However, with Angular, we're given the tools to easily make AJAX requests and keep our pages updating in real-time without having to refresh. Awesome!

### Awesome! But why is it popular?
Not only does it have a massive development community with thousands of plugins, it's also a "one-stop-shop." We can depend on Angular and Angular alone to render and control our whole application. This means there are fewer technologies to learn as we're only dependent on Angular! 

## MVVM and Data Binding in Angular
In this lesson, we are going to look at the core concepts that we will use in every Angular application. Some will be familiar to you, however some may seem a bit strange. Don't worry if they take time to sink in!

Angular allows us to create single page applications (SPAs). This means that the user goes to one page and very rarely will have to refresh/leave that page to go to other parts of the website. Ever wondered how we can go to Twitter and never have to actually refresh the page? Yet all of our notifications, tweets, etc are all real-time and constantly up-to-date? You guessed it - Twitter is a single page application!

Single page applications handle all the routing, calling different parts of your codebase depending on what URL the user is currently at. If we look back at Twitter, you'll notice how the URL does change yet the page doesn't refresh. This is because we have now handed all routing over to the client side instead of the server. The client can see where the user has intended to go, and select the specific code for that page - magical!

Traditionally, server-side rendering would be like the following -

![Server-side rendering](http://www.michaelgallego.fr/images/posts/2012-11-26-client-side-1.png)

The user requests the page from the server, and the server will return all the HTML to display on that page. The data would not be updated until the user refreshes. This puts overhead on the server, as it will have to render the page on every page load. If you head over to the [BBC News](http://bbc.co.uk/news) you'll see how the content is already there - no waiting whatsoever.

With Angular, the flow will go like this instead -

![Client-side rendering](http://branchandbound.net/pics/client-side-rendering-only.png)

This looks a lot more complicated, but it isn't! Instead of returning rendered HTML for each user, the server would return the same page for every user. The client will then make a request to the server, requesting what's necessary for that page to render (such as a list of products). The client will then render this page for the user.

This has massive advantages - if 1000 users are on the website, instead of one server rendering 1000 pages, 1000 clients are rendering one page, reducing strain on the server. We can also re-use backend endpoints - our mobile website and our desktop website can both request the same data from the server but display it differently.

One example of this that you can check out for yourself is if you go to Facebook. You might notice how you don't actually see anything until the content very quickly loads and then the client renders this - saving so many resources in the meantime!

## MVC/MVVM

You might have seen the terms MVC and MVVM being thrown around. These stand for Model-View-Controller and Model-View-ViewModel respectively. 

These are concepts for how we architect our software. We do this to promote separation of concerns. Separation of concerns is dividing our code into logical chunks, with each chunk addressing a separate concern. This allows us to create testable, reusable and scalable well designed code.

They are both quite similar, however there are a few differences -

### MVC (Model-View-Controller)

Three parts to MVC; model, view, controller. The model manages the fundamental behaviours and data of the application. This could be retrieved from a database or any other sort of data store.

The view is the user interface. This takes data from the model and displays it nicely for the user. Any user interaction in the view is then handed over to the controller.

The controller receives user input and makes calls to the model and view to update/modify either. This keeps the main aspects of our application separate.

An easy way to visualize this is if we imagine we are ordering a coffee. The Model is the information about the drink we've ordered, the Controller is the barista and the View is the finished drink. The barista would make the drink from our order (the Model), and serve it to us (the View).

So for example, if you walked into a coffee bar and ordered a hot chocolate, you'd get a hot chocolate. If you then wanted marshmallows, you'd ask the barista, who would go back to the till and modify your order to add on marshmallows. They would also then put marshmallows in your drink, and return you the updated drink (the View).

If we weren't using a single page application and instead the server was rendering the page for us, the barista would have simply thrown out the drink and remade it with marshmallows - what a waste!  

If you've touched on MVC before, you might have learnt it a little differently. Not to worry! MVC in the frontend is slightly different, but the main concepts still apply!

### MVVM (Model-View-ViewModel)

Similar to MVC, however the controller is replaced with a ViewModel.

Let's take a trip back to the coffee shop. You'll notice there is a new member of staff - a cashier. The barista was too overloaded as a controller, and has stepped down to just being a helper. The cashier has been brought in as a ViewModel, in order to make the coffee shop more efficient.

Like before, we order a hot chocolate. The cashier takes your order, updating the Model. They then shout to the barista that they need a hot chocolate. The barista makes the hot chocolate, and returns it to the cashier. The cashier then writes your name on the lid, and returns it to you.

The differences here is that we no longer have one person taking your order and delivering your drink. Instead, the cashier (ViewModel) uses a helper (business logic) to get your drink order (Model) completed and only modifies the lid with your name (view logic) and returns it to you (the View).

This is the preferred architecture for Angular applications. Why? We no longer have a controller doing everything for us. Instead, we can simplify the application down massively by having helpers that we can use everywhere.

The ViewModel is responsible for all view logic - changing the model data appropriately for use in the view. (For example, our model might contain a UNIX timestamp for a date but we need it in human readable format). Your model will contain all of your business logic, and your view is there to display your model (modified by the ViewModel).

## Data-binding

Data-binding is the concept that allows us to easily keep our view and model synchronised without having to write excessive amounts of code whenever we would like to update either. This comes in two formats - one-way and two-way data-binding.

### One-way data-binding

Imagine you have a form input, asking for the user's name. You've also got a `<h2>` tag below, that you want to populate to say "Hey, {name}!". Wouldn't it be neat if this `<h2>` tag could update as the user types in their name? This is called one-way data-binding. The model (our user's name) is updated and our view is updated to reflect the change to our model.

For example, you'd use one-way data-binding when you've got a search box - the user can type in their search query and the title can change to "Results for: {searchQuery}" - pretty cool!

[Here's an example of one-way data-binding.](https://jsfiddle.net/6z6d5b7x/)
 
An easy way to visualize this is to go back to when we were receiving our drink from the barista. If the drink was one-way bound from the barista, the drink would always be updated and correct. However, the barista wouldn't be able to see the drink. If it got knocked over or was mouldy, the barista wouldn't have any idea!

### Two-way data-binding 

Two-way data-binding occurs when you bind your model value to an element that can both change and display the value of the model (such as an input).

You aren't restricted to updating your model value just in the `<input />` however - you can update this Model value elsewhere (such as a "reset" button to reset the model) and it will be automatically reflected in the input (it will go blank).

[Checkout this example of two-way data-binding](https://jsfiddle.net/6z6d5b7x/1/)

You can see the flow of this here -

![Two-way data-binding](https://docs.angularjs.org/img/Two_Way_Data_Binding.png)

Going back to our barista - with two-way data-binding, our barista can now see everything! If our drink was to get knocked over after given to us, the barista would notice and be able to act upon that wild change of events!

Two-way data-binding has a one-directional flow of data which ensures that the View and the Model data is always synchronized.

In the above example our template compiles to become our View, which is a representation of the Model data. The View can then change our Model (for instance, an `<input />` being updated), which then updates our View. Model changes drive View changes and View changes drive Model changes. This keeps everything always synchronized. 

## Resources

- [AngularJS Dependency Injection Manual](https://docs.angularjs.org/guide/di)
- [AngularJS Databinding Documentation](https://docs.angularjs.org/guide/databinding)

# Angular Setup + directory structure

## Overview

We need to ensure that we have a level-headed way of structuring our applications from the beginning, otherwise we could end up with files everywhere, which means it's hard to know exactly what you are editing and where.

## Objectives

- Define the core structure of an Angular application
- Create a feature based file structure

## Core Structure

There are plenty of other ways to structure your application. One popular way is to just have folders for controllers, directives etc without having folders for each module, as follows - 

```
├── js/
│   ├── directives/
│   │   ├── TodoEscape.js
│   │   ├── TodoFocus.js
│   │   ├── LoginForm.js
│   ├── controllers/
│   │   ├── TodoController.js
│   │   ├── LoginController.js
│   ├── services/
│   │   ├── TodoService.js
│   │   ├── LoginService.js
│   ├── templates/
│   │   ├── partials/
│   │   │	├── TodoForm.html
│   │   │	├── LoginForm.html
│   │   ├── views/
│   │   │	├── Todo.html
│   │   │	├── Login.html
│   ├── app.js
│   ├── angular.js
├── img/
├── css/
├── index.html
```

This works, but as your application gets bigger, the folders will end up with loads of files in them, without us knowing what part of the application they are responsible for.

This is why we separate our app into "modules". We can then immediately know what file is used in what part of the application just by looking at what folder it is in. Each module will have directives, templates, controllers and services.

Like a normal application, we'll have separate folders for our JavaScript, CSS and images. However, inside our JavaScript folder we'll have individual folders for each module in our Angular application. Angular needs at least one module to kick things off, and we're going to call our main module "app".

This means that you'll end up with a directory structure like this:

```
├── js/
│   ├── todos/
│   │   ├── directives/
│   │   │   ├── TodoEscape.js
│   │   │   ├── TodoFocus.js
│   │   ├── controllers/
│   │   │   ├── TodoController.js
│   │   ├── services/
│   │   │   ├── TodoService.js
│   │   ├── templates/
│   │   │   ├── partials/
│   │   │   │   ├── TodoForm.html
│   │   │   ├── views/
│   │   │   │   ├── Todo.html
│   ├── login/
│   │   ├── directives/
│   │   │   ├── LoginForm.js
│   │   ├── controllers/
│   │   │   ├── LoginController.js
│   │   ├── services/
│   │   │   ├── LoginService.js
│   │   ├── templates/
│   │   │   ├── partials/
│   │   │   │   ├── LoginForm.html
│   │   │   ├── views/
│   │   │   │   ├── Login.html
│   ├── app.js
│   ├── angular.js
├── img/
├── css/
├── index.html
```

This is a feature based file structure, as we're splitting off into individual modules instead of having all of our controllers/directives/etc. in one folder. Don't be scared - we will be touching on controllers/directives/modules/etc very soon!

# Modules

## Overview

In this lesson we're going to go into modules and how to create and load our own. You'll recognize the syntax from our previous module!

## Objectives

- Describe the setter/getter syntax
- Create a module using a setter
- Fetch the module using a getter
- Import a submodule

## What is a module?

Think of a module as a container for specific parts of your application. Each module should provide a set of functionality (for instance you might have a "login" module that handles everything to do with user authentication and logging the user in). Modules can contain views, components, routes, etc, but that's not important right now (you'll learn all about these very shortly).
 
It's important that we have at least one module - otherwise we couldn't do anything!

Why do we split our application into modules? Modules allow us to separate our application into logical chunks (much like MVC/MVVM that we touched on earlier) that can be reused. It's recommended that you create modules for 

- Each feature in your application
- Each reusable component in your application
- An application module that our application uses as a base

Angular comes with a lot of plugins available on the web. Each one of these will be its own module - meaning that you can just slot it into your application and not have to worry about it interfering with any other aspects of your app!

## Setter/getter syntax

### Modules

Angular is magical, but it isn't *that* magical. We need to tell Angular about all of our modules, controllers, etc, when we create them - otherwise, it would have absolutely no idea what is used for what.

The way we tell Angular about our modules is:

```js
angular
  .module('exampleModule', [])
```

The `angular` object we're using there is the Angular core. This is the core API - this allows us to create and load modules (using `angular.module`).

You might be wondering why we have a second parameter with an empty array in it. This is very important - it tells Angular that we need to *create* a new module. If we omit the second parameter, it would tell Angular that we'd like to *retrieve* a module with the name `exampleModule`.

The empty array is very important for our module too. This is an array of modules that our module depends on. If you were to download a plugin online, you can't just drop the code in and expect Angular to know that it needs to be a part of your application. This is where this array comes in - you can tell Angular that your module depends on the plugin's module that you just downloaded, and it will include it into your application and allow you to use it - amazing!

The number of parameters is true for everything we set/get in Angular. If we only have one parameter, we are telling Angular to `get`. If we have two parameters, we are telling Angular to `set`.


If we were to be doing routing in our app, we'd include Angular's `ngRoute` module. First of all, we'd download the files from the web and make sure we include them via script tags in our HTML file. Then, we'd tell Angular that our module relies on `ngRoute` - otherwise Angular wouldn't know that we actually would like to use the module, even though it exists:

```js
angular
  .module('exampleModule', ['ngRoute'])
```

Simple! That is the `setter` syntax for modules.

### Controllers, directives and everything else
 
Now, we can't just call `angular.controller` for our controllers. Controllers, directives, services, etc, must be attached to our modules. This is done as so:
```js
function ExampleController() {
}

// We assume that the module "exampleModule" has already been created
angular
  .module('exampleModule') // fetch the module
  .controller('ExampleController', ExampleController); // create the controller
  
// both of these do exactly the same thing
var module = angular.module('exampleModule'); // fetch the module
module.controller('ExampleController', ExampleController); // create the controller
```

This is similar to our module setter/getter. Much like `angular` having `angular.module`, all of our modules have the method `.controller`, allowing us to get (or set) the controller.

Why are we fetching the module? Well, we could possibly be in a completely different file. How would Angular know what module our controller belongs to unless we tell it?

We can then retrieve the controller we've created by omitting the second paramater.

```js
// We assume that the module "exampleModule" has already been created
angular
  .module('exampleModule') // fetch the module
  .controller('ExampleController'); // fetch the controller
  
// both of these do exactly the same thing
var module = angular.module('exampleModule'); // fetch the module
module.controller('ExampleController'); // fetch the controller
```

## Using our module in our application

Now we've got Angular aware of our module, we need to tell it where our module actually needs to be used.

### ng-app

We can do this via the `ng-app` HTML attribute Angular makes available for us. All we need to do is find the HTML element where we want Angular to start rendering, and add `ng-app="exampleModule"`.

```html
<div class="app" ng-app="exampleModule">
</div>
```

## Resources
- [Todd Motto's guide for Angular Modules, Setters & Getters](https://toddmotto.com/angular-modules-setters-getters/)
- [Angular Documentation for Modules](https://docs.angularjs.org/guide/module)


# Very small [hello world](https://github.com/BrunoBoehm/angular-modules-lab-v-000/blob/cf12223f82ea2fc1143e50f58fe9f53cdf71cc86/index.html) app
Let's create the html
```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">

    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Angular Application</title>
</head>
<body>

    <div ng-app="app">
        <div ng-controller="MainController">
            Hello, {{ name }}!
        </div>
    </div>

    <script src="js/angular.js"></script>
    <script src="js/angular-route.js"></script>
    <script src="js/app/app.js"></script>
    <script src="js/app/controllers/MainController.js"></script>

</body>
</html>
```

In our js/app/app.js
```js
angular
	.module('app', [
		'ngRoute'
	])

// python -m SimpleHTTPServer 3000 
// to run server
```

And we create the MainController function we need
```js
function MainController($scope){
	$scope.name = 'Bill';
}

angular
	.module('app')
	.controller('MainController', MainController);
```

## $scope

You might've noticed the magic of `$scope` in the last lesson - an object that we can assign values to and they appear in our view. `$scope` is named by Angular - we can't change the name of it, so make sure you refer to it as `$scope`! 

Angular introduces scopes into our application. Whenever we have a new instance of a controller, that controller has a `$scope`. Everything inside our controller can access this scope, however anything outside cannot. `$scope`s can access their parent scope.

## Using $scope in our views

We can access every property of `$scope` that we set in the controller inside our views. This is done using the `{{ }}` syntax that we used in our first lab. All we need to do is put the property key inside of the double curlys - such as for `$scope.name`, we use `{{ name }}`. We can also use `.` to access properties inside properties (for example, an object).

For example:

```js
function MainController($scope) {
  $scope.contact = {
    name: 'Bill Gates',
    phone: '01234567890'
  };
  
  $scope.year = '2016';
}
```

```html
<div ng-controller="MainController">

  <h2>{{ contact.name }}</h2>
  <h4>{{ contact.phone }}</h4>

  <div>
    Copyright {{ year }}.
  </div>
</div>
```

This would render out:

```html
<div ng-controller="MainController">

  <h2>Bill Gates</h2>
  <h4>01234567890</h4>

  <div>
    Copyright 2016.
  </div>
</div>
```

Neat, huh? 

However, if we tried to access items outside of our controller, such as:

```html
<div ng-controller="MainController">

  <h2>{{ contact.name }}</h2>
  <h4>{{ contact.phone }}</h4>

  <div>
    Copyright {{ year }}.
  </div>
</div>

{{ year }} {{ name }}
```

All we'd get rendered is:
 
 
```html
<div ng-controller="MainController">

  <h2>Bill Gates</h2>
  <h4>01234567890</h4>

  <div>
    Copyright 2016.
  </div>
</div>

{{ year }} {{ name }}
```

![Angular Scopes](https://docs.angularjs.org/img/guide/concepts-scope.png)

Look at the example above - each red rectangle is a scope. If we look at the first rectangle for the HTML element with `ng-controller` - this is currently what we have in our application. From this `$scope`, we'd be able to access the parent `$scope` (the big rectangle around the whole image), but not the `$scope` of the second HTML element with `ng-controller`.

### $rootScope

We also have the `$rootScope` - this is the first scope in our application. All of our `$scope`'s will end up linking to this scope eventually. Not to worry about this yet, you'll come to see it a lot more later on.

# Data-binding
We've talked about data-binding before, but if it's not on the top of your memory you don't need to worry. Data-binding is the term for keeping our model values in sync with our view. Whenever the model changes, our view needs to change too to reflect the change. Whenever our view changes (such as a user typing into an input), we need to update our model with the latest value. This is done via data-binding.

### One-way

The curly braces syntax (`{{ }}`) binds our model value into our view in the form of text. This is one-way bound - the model can update the view, but our view cannot update the model (you can't type into text - only an input!).

We can also bind text into the DOM using a `ng-bind` attribute on the HTML element instead. If we use `ng-bind`, the whole text content of the element is replaced with the value, whereas with the curly braces only the curly braces is replaced. Either can be used, but curly braces are simpler. 

```js
{{ name }}
<span ng-bind="name"></span>
```

These will both display the same thing!

### Two-way

We can two-way bind our data into certain HTML elements - ones that accept input. For example, you guessed it - an `<input />`. This is done with the `ng-model` attribute (more on `ng-model` and `ng-bind` later on).

```js
<input type="text" ng-model="name" />
```

Whenever we type in our `<input />`, our `$scope.name` gets updated, they will both reflect the changes to the value. 

## Watching for updates

We can also watch for updates - how neat! The `$scope` object exposes a few APIs, one of them is `$watch`. `$watch` allows us to pass one of our `$scope` object's keys through, and fires off a callback whenever it updates.

For example:

```js
$scope.$watch('name', function (newValue, oldValue) {
  console.log('name changed from %s to %s', newValue, oldValue);
});
```

We could use this with the two-way data-binding example above. This would fire a `console.log` statement every time the user types in the input!

When would we actually need to use this? For example, in a game we could watch for changes to our name value and broadcast it to everyone else - 

```js
$scope.$watch('name', function (newValue, oldValue) {
  socket.emit('Player ' + oldValue + ' has changed their name to ' + newValue);
});
```

## Overview

We've learned already what `$scope` is and the magic it provides with our view. However, before we start going `$scope` mad, it's important we learn about the best practices when it comes to controllers and our views.

## What is controllerAs?

As you've learned, controllers revolve around the mysterious `$scope` object. However, there is a much cleaner approach to writing our controllers.

Instead of injecting `$scope` into every controller, we can simply just use the `this` keyword and assign items to that instead.
 
There's a slight change in our `ng-controller` syntax too:

```html
<div ng-controller="MainController as main">
</div>
```

Here we tell Angular we'd like to use our controller *as* a variable named `main`. This then creates a new instance of our controller (with all of our values bound to the controller's instance, rather than `$scope`) and assigns the instance to a variable named `main`. This then allows us to access our properties with `{{ main.propertyName }}`.

## Oh no, nested scopes

This helps us when we have nested scopes. If we had a controller inside a controller, and both added the variable `name` to `$scope` - which one would we see?

```html
<div ng-controller="MainController">
  {{ name }} <!-- This is from MainController -->
  <div ng-controller="AnotherController">
    {{ name }} <!-- Where's this from? -->
  </div>
</div>
```

We wouldn't be sure where `name` was coming from in this example. What if we wanted to use `name` from `MainController` instead of `AnotherController` both times? We wouldn't be able to!

That's where controllerAs saves the day - we can assign each controller to different variables and we'd know where `name` is from.

We'd take this:

```js
function MainController($scope) {
  $scope.name = 'Bill Gates';
}
```

And convert it into:

```js
function MainController() {
  this.name = 'Bill Gates';
}
```

Done! That's all it takes. The HTML markup would then look like:
 
```html
<div ng-controller="MainController as main">
  {{ main.name }}
  <div ng-controller="AnotherController as another">
    {{ another.name }} and {{ main.name }}
  </div>
</div>
```

This would render out to be:

```html
<div ng-controller="MainController as main">
  Bill Gates
  <div ng-controller="AnotherController as another">
    Steve Jobs and Bill Gates
  </div>
</div>
```

No more issues with nested scopes!

## What about the rest of $scope

So does this mean we can use `this.$watch` instead of `$scope.$watch`? Unfortunately not - the API for watching value changes still sits with `$scope`, so we still have to use that.

Think of it this way - when we use controllerAs, we're allowing our controllers to assign anything they want our view to access to the `this` keyword. Everything else is as it was before!

# Testing Controllers with Test Driven Development (TDD)

If you haven't done any testing before, your normal coding cycle would be churning out code like there's no tomorrow. However, with Test Driven Development (TDD), you've guessed it - every part of the development we do is driven by tests.

Instead of writing code, fixing bugs, writing more code, blah blah, we start off by writing a unit test. This test will initially fail, as we haven't written any code.

Let's create a function that adds two values together. Instead of going straight into the deep end and writing the function, we write the test first:

```js
describe('Basic Functionality', function () {
  it('should add two numbers', function () {
    expect(addNumbers(1, 3)).toBe(4);
  });
});
```

What's this crazy syntax? When we run our tests, we use syntax that is provided to us by a framework called Jasmine. Jasmine gives us a set of predefined functions (such as `it`, `expect`, etc) that allow us to describe, quite simply, what we want the test to achieve.

Above, we're telling our test runner that in our `Basic Functionality` block, we have a test that expects our number adding function to output `4` when we add `1` and `3` together.

The test will then run, notice we haven't *actually* defined our number adding function, and fail. Right. Let's create the number adding function then!

```js
function addNumbers(numberOne, numberTwo) {
}
```

Great - now we're getting started. Let's run our test again - doh! Failed. We haven't actually done any logic, so the function still won't output `4`, which is what our test is looking for.

Simple - let's just return `4`! Then it passes all of our tests!

```js
function addNumbers(numberOne, numberTwo) {
  return 4;
}
```

Perfect, our tests now pass. Wait! Hold on a minute - when we try and use that function with any other numbers, we're going to always get `4` back! 

How can we test for this? Test it again! Realistically, our tests should always test our functions with many different parameters, expecting correct answers from our functions. That way, if we have a test adding `1` and `3` (to equal `4`), and also adding `50` and `24329` (to equal `24379`), we can, with some confidence, know that our number adding function actually works as we expect.

Let's modify our first test:

```js
describe('Basic Functionality', function () {
  it('should add two numbers', function () {
    expect(addNumbers(1, 3)).toBe(4);
    expect(addNumbers(343, 9283)).toBe(9626);
    expect(addNumbers(1223, 21)).toBe(1244);
    expect(addNumbers(10, 653)).toBe(663);
  });
});
```

Okay, now we've got multiple test cases, let's run our tests again. As expected, our first one passed (as our number adding function is only returning `4`), but the others have failed. Now we need to head back to our number adder and actually implement it correctly.

```js
function addNumbers(numberOne, numberTwo) {
  return numberOne + numberTwo;
}
```

We run our tests again and they all pass - happy days! The code goes into production, but two days later we receive a bug report saying that when people are adding `2` and `2` together, they get `22` instead of `4`. Oh no, what could've gone wrong?

Our function doesn't support strings! In JavaScript, if we were to do `"2" + 2`, we'd get `22` as the result because the `+` operator adds two strings together, as well as actually doing addition between two numbers.

Let's head back to our tests, and add some use-cases for when the function gets called with parameters that don't match what it expects.

```js
describe('Basic Functionality', function () {
  it('should add two numbers', function () {
    expect(addNumbers(1, 3)).toBe(4);
    expect(addNumbers(343, 9283)).toBe(9626);
    expect(addNumbers(1223, 21)).toBe(1244);
    expect(addNumbers(10, 653)).toBe(663);
    expect(addNumbers('99', 1)).toBe(100);
    expect(addNumbers('23', '59')).toBe(82);
  });
});
```

If we run our tests again, they will fail (as we expect). Now, we can head back to our code and make amendments to handle these use cases.
 
```js
function addNumbers(numberOne, numberTwo) {
  return parseFloat(numberOne, 10) + parseFloat(numberTwo, 10);
}
```

Brilliant. Our tests run and pass and we have a well coded, tested piece of code. We can then make changes to this code further, running our tests against it along the way, ensuring no previous expected functionality has been broken.

## Jasmine and Karma

To do TDD, we need to install Jasmine and Karma. Clone this repo completely.

Open your terminal, and run

```bash
sudo npm install -g karma-cli
```

This will install the Karma command line interface tool, so we can run tests using `karma`.

We also need a copy of Karma for our project, as well as Jasmine too.

Karma command line interface starts up the karma server for us, and the local copy for our project allows us to access the API's that karma offers.

```bash
npm install karma --save-dev
npm install jasmine-core --save-dev
npm install karma-spec-reporter --save-dev
npm install karma-jasmine --save-dev
npm install karma-chrome-launcher --save-dev
```

Sorted! Run `karma start` on your command line to see it run (and pass!) our basic test (expecting `'foo'` to equal `'foo'`).

## ngMock - ngWhat?

When we test our code, we need to be able to get deep inside it and see what everything is doing. However, in normal day-to-day coding, we cannot do that - that's where ngMock saves the day.

ngMock is a module that Angular provides us to embed into our tests in order to inject and mock our controllers, directives etc into our tests. ngMock also extends some core services that Angular provides, in order for us to inspect them and control them differently to how they would run in the browser.

To embed this into our tests, all we need to do is tell karma to include it when we specify what files we'd like to test. Take a look at `karma.conf.js` inside this repo - we've done that for you.

## Writing our own unit test

This is where all of the above come in. In this repo (that you should've already cloned!), we've got an example controller called `MainController` inside `js/app/controllers`. We've also got an example test at `tests/MainController.spec.js`. Let's modify this test to inject our example controller.

Let's change the `describe` block to match our controller's name. This way, when we look at the results in the console, we can tell what is actually being tested. (Change "example test" to MainController).

Now, we need to know what app we're using before each test, much like us using `ng-app` in our HTML. To do this, we use `ngMock`'s `module` function.

We can do this like so:

```js
describe('MainController', function() {
  beforeEach(module('app'));
});
```

This tells Jasmine to use the `app` module for every test for our `MainController`.

Now, we need to inject the controller service given to us by `ngMock`. This allows us to call a function with the name of the controller we'd like, as well as specify a custom `$scope` object for the controller to play with.

```js
describe('MainController', function() {
  beforeEach(module('app'));

  var $controller;

  beforeEach(inject(function(_$controller_){
    $controller = _$controller_;
  }));
});
```

Now, inside each of our tests (the `it` should blocks), we can call the `$controller` function, asking for it to return `MainController`.

Let's create a test to check if the name is set correctly inside the controller.

```js
describe('MainController', function() {
  beforeEach(module('app'));

  var $controller;

  beforeEach(inject(function(_$controller_){
    $controller = _$controller_;
  }));

  it('should have Steve Jobs name', function() {
    var $scope = {};

    var controller = $controller('MainController', { $scope: $scope });
    expect(controller.name).toEqual('Steve Jobs');
  });
});
```

If we run `karma start` now, you'll notice our test fails. Go into the `MainController.js` file inside `js/app/controllers` and see if you can figure out why, and see if you can get our unit test to pass (Steve Jobs)!


# What is a Service? Our little helpers

Services are helpers. They're JavaScript functions and are responsible for doing specific tasks only. For example, we might have a `UserService` that communicates with our API for everything user based. Or a `NotificationService` to deal with showing notifications to the user.

Services can be used anywhere and everywhere. It's what makes Angular so useful - we can reuse our code over and over so we don't have to repeat ourselves.

## Where do they come from?

It's all great being able to create services, but how do we get them when we need them? Introducing another piece of Angular magic - Dependency Injection.

Dependency Injection is something you never knew you wanted until it's been given to you - now you won't be able to live without it. Dependency Injection allows us to define *what* we want our controllers to have access to and Angular gives them it!

For instance, we could have 123 different services in our Angular application, but our controller only wants to use three of them. It's important to only include the services we need to use otherwise we may have a massive impact on performance. To do this, all we need to do is specify the three services names as parameters for our controller:

```js
function ContactController(NotificationService, UserService, AuthService) {
  NotificationService.notify('Hello!');
}
```

Angular then, before initiating our controller, looks at what parameters we require and takes a note of them. They are all identified using their names. Then when we initiate our controller, Angular knows exactly what services we need to be "injected".

You'll notice that we've actually done something like this already with `$scope`. We don't have to use `$scope`, but as we specify it as a parameter to our controller, Angular injects it for us. We could have put `$scope` as the second or fifth parameter - it wouldn't matter. 

Our `NotificationService` could look like this: 

```js
function NotificationService() {
  this.notify = function (message) {
    alert(message);
  };
}

angular
  .module('app')
  .service('NotificationService', NotificationService);
```

Notice how we tell Angular about our service in a similar way that we notify it about our controllers - we use `.service` on our modules. We attach all our methods to the `this` keyword as they're properties. Then, we can access all created properties in our controllers. What is important here is the first parameter - this is the name of our service and will be used when we need to inject it elsewhere. The function doesn't need to have the same name, but for debugging purposes, we keep it the same (as it'll be printed in the console if we ever get errors.)


# Injecting a Service

Let's inject one of Angular's built in services into our controller.

For this lab, we're going to make use of `$timeout`. `$timeout` allows us to create timeouts (similar to `setTimeout`) in our applications whilst ensuring that any changes to our model done inside a timeout gets reflected in the view.

`$timeout` accepts the same parameters as `setTimeout` - a function and an integer for how many milliseconds delay.

```js
$timeout(function () {
	// this would be fired after 2 seconds!
}, 2000);
```

Fork and clone this repository to get started. 

Let's create our controller inside `ContactController.js`, this should have two parameters - `$scope` and `$timeout` (it doesn't matter what order you put them in, if you don't believe me - try it!).

Attach the controller to our `app` module.

Now, inside our controller, set `$scope.name` to your name. We previously touched on using controllerAs, but as we need to use two simple services for this lab, we will be using `$scope`.

Below that, set a $timeout for 5 seconds. Inside the function, set `$scope.name` to something else.

Open up `index.html` and wait 5 seconds - you'll see the view get updated with our new name!

# Minification safe Dependency Injection

Minification is great - it reduces our code's file size and allows us to code wonderful things without impacting load times. It strips out all unneeded whitespace and punctuation in order to make our files as small as they can possibly be.

For instance, a minifier might take this:

```js
function add(numberOne, numberTwo) {
	return numberOne + numberTwo;
}
```

And change it into:

```js
function add(a,b){return a+b;}
```

Much smaller! However, it can cause a bit of an issue when mixed with dependency injection.

Most minify-ers change our variable names to single letters - it isn't important what our variables are called, only that they all still refer to the same object/method/function/etc. For example:

```js
function ContactController($scope, $timeout) {
}

angular
  .module('app')
  .controller('ContactController', ContactController);
```

Would become:

```js
function a(b, c) {
}

angular
  .module('app')
  .controller('ContactController', a);
```

Oh no - we don't have services named `b` and `c`. Therefore, when Angular looks at our controller and notices that we require `b` and `c`, it'll throw an error as they don't exist.

How do we overcome this? Well, it's important to know how dependency injection works under the hood first.

## Under the hood

When Angular looks at our function, it takes our parameters and creates an array of what we require. For instance, our controller above would generate the array `['$scope', '$timeout']`. Angular then attaches this array onto a property named `$inject` on our function.
 
```js
function ContactController($scope, $timeout) {
}

angular
  .module('app')
  .controller('ContactController', ContactController);
  
// ContactController.$inject = ['$scope', '$timeout'];
```

Can you see how we can resolve the issues when it comes to minification? We can take over from Angular and specify this `$inject` property ourselves. When the `$inject` property exists, Angular trusts us to know what we want and doesn't look at the controller's parameters - meaning we can name our parameters whatever we want.
 
```js
function ContactController(whatever, weWant) {
  // whatever === $scope
  // weWant === $timeout
}

ContactController.$inject = ['$scope', '$timeout'];

angular
  .module('app')
  .controller('ContactController', ContactController);
``` 

In our example above, the variable `whatever` is still equal to the value of `$scope` - just named differently! The same applies to the variable `weWant`. This means that our minification process will have no side effects to our code.

Another example
```js
function ContactController(a, b) {
	a.name = 'Bill Gates';

	b(function () {
		a.name = 'Steve Jobs';
	}, 5000);
}

ContactController.$inject = ['$scope', '$timeout'];

angular
	.module('app')
	.controller('ContactController', ContactController);
```

# What is a Directive?

Directives are essentially "markers" on a HTML element that tell Angular to attach a specific behavior to the HTML element - either something small like a click event, or actually completely transforming the DOM node to display a list of data.

Directives can be either an actual HTML element or an attribute on a HTML element.

```html
<my-directive></my-directive>

<!-- these are the same -->

<div my-directive></div>
```

However, not all directives can be used in both ways - some are restricted to being just an attribute or just an element. All of the built-in directives from Angular are restricted to being used as attributes. For any other ones (such as custom directives you download online) you will have to check the documentation on how to use it.

## Types of directives

There are two types of directives - event and behavioral. Event directives handle all of the events on a HTML element we might need - for example, `click`, `mouseover`, `keydown`, etc. These are the same as normal JavaScript events that we would add event listeners for.

Behavioral directives are directives that manipulate the DOM. For example, we might have a list that repeats our DOM node for every item in a list. We could even have a directive for hiding and showing content depending on one of our variables' value.

We'll have more on these in the next couple of lessons.

## Built-in directives

Luckily for us, Angular comes with a ton of built-in directives that do what we mentioned above and more. We'll be looking into the built-in ones in the other sections of this unit. Angular's built-in directives are prefixed with `ng-` (you might have noticed we're already using `ng-app` and `ng-controller` - these are just directives!) `ng-app` tells Angular what DOM node to put our application inside of. `ng-controller` tells Angular to attach our controller to that DOM node so we can access the controller inside of the element. In case you hadn't guessed, the `ng-` stands for Angular and it's best practice NOT to use this prefix on our own directives. 

# Event based directives

If you've ever done a lot of JavaScript before, you would have come into contact with event listeners. These are functions that get called whenever a specific behaviour happens that we are looking out for. Either of the following might be familiar to you:

```js
input.addEventListener('click', function (e) {
});

// or

input.onclick = function (e) {
};
```
```html
<!-- or this -->

<input onclick="myFunction()" />
```

These would all fire off of a function when a key was pressed inside of our input.

## Angular's equivalent

Instead, in Angular, we use the built-in `ng-click` directive, and pass in the function we want to be called.

```html
<input ng-click="vm.myFunction()" />
```

## Why do we do this?

We already have a way to do events in JavaScript without any plugins. Why do we have to do things differently inside Angular?

Angular allows us to pass all the event handling over to them. We don't have to worry about browser compatibility or even unbinding our events at the sacrifice of using the built-in directives for event handling instead. A small price to pay for consistent event handling in all browsers. 

Angular also has the concept of a "digest cycle". This, at a high level, is a function that keeps all of our view and model in sync with each other (we will be going into this in a lot more detail later on). The built-in directives ensure that the digest cycle is ran, keeping our view and model synchronized if we were to update our model in response to an event.

## Calling our own functions

As you can see in our example above, we are calling `vm.myFunction()`. An example setup of the controller might look like this:

```js
function ExampleController() {
  this.myFunction = function () {
    console.log('Hey!');
  };
}
```

Which would result in `Hey!` being printed to the console whenever the user types in the input.

As the function is defined in the controller, we also have complete access to all services/model items, allowing us to manipulate them. For example, we might want a button that increments a counter every time it's clicked.

First of all, we'd use the `ng-click` directive provided to us by Angular.

Our HTML would look like this:

```html
<button ng-click="vm.incrementCounter()">Increment the counter!</button>

{{ vm.counter }}
```

And our controller would look like this:

```js
function CounterController() {
  this.counter = 0;
  
  this.incrementCounter = function () {
    this.counter++;
  };
}
```

What's happening here? Well, whenever the user clicks on our button, our `incrementCounter` function gets called. We can then access our model value (`this.counter`) inside that function, and update it itself plus one. Angular then notices that the model has changed, and will update our view to reflect this.

# Behavioral Directives

Behavioral directives are directives that allow us to manipulate the DOM. For example, we could have a repeating list of items or we could hide/show a DOM node depending on a variables value.

Behavioral directives are commonly just used as attributes, and quite a lot are provided by Angular itself.

Imagine we're not using Angular. If we wanted to loop through an array of objects and display them, we'd have to do something like this:


```js
var todos = [{
  title: 'Learn Angular',
  complete: false,
},{
  title: 'Create GitHub profile',
  complete: false
},{
  title: 'Brush teeth',
  complete: true
}];

var list = document.querySelector('ul.todos');

todos.forEach(function (todo) {
  var item = document.createElement('li');
  
  var wording = todo.complete ? 'Completed!' : 'Not completed :(';
  
  item.innerHTML = '<h4>' + todo.title + '</h4> ' + wording;
  
  list.appendChild(item);
});
```

This worked fine but what if our `todos` array was to get updated? We'd have to make sure to only insert the new items into our list, and only remove the correct elements when an item was removed from our array. This could get extremely messy and out of sync with our data if we were not really careful.

## Angular saves the day!

Try and contain your excitement when you see how this is done in Angular.

The HTML:

```html
<ul>
  <li ng-repeat="todo in vm.todos">
    <h4>{{ todo.title }}</h4>
    
    {{ todo.complete && 'Completed!' || 'Not completed :(' }}
  </li>
</ul>
```

Our controller: 

```js
function TodosController() {
  this.todos = [{
     title: 'Learn Angular',
     complete: false,
   },{
     title: 'Create GitHub profile',
     complete: false
   },{
     title: 'Brush teeth',
     complete: true
   }];
}
```

That's everything that we need. Not even joking.

This handles everything - whenever our `todos` array is updated, Angular will update our view to match, removing and adding only the relevant nodes.

## ng-model

Along with `ng-repeat`, `ng-model` is one of the most commonly used directives provided by Angular. `ng-model` works its magic by setting an input's value to a variable set in the controller, as well as updating said variable whenever the user updates the `<input />`'s value.

```html
<input ng-model="vm.username" />
```

This will populate our `<input />` with the value of `vm.username` (which could be empty), and then when the user types in the input, updates `vm.username` to match.

[Check out this JSFiddle](https://jsfiddle.net/pjrfbkku/) showing the power of `ng-model`.

## ng-class

Another task that's quite common in modern applications is dynamically adding and removing classes depending on different variables. For example, we might want to add a complete class on our example above if the todo is complete.

We can do this using the power of `ng-class`. `ng-class` takes an object, with the keys being the class you want to dynamically add, and the value being an expression - when the expression evaluates to `true`, the class is added. When it's `false`, the class will be removed.

For example:

```html
<div ng-class="{'classNameHere': true, 'otherClassName': false}">
</div>
```

In the example above, `classNameHere` would be added to our `<div />` (as the object's value is equal to true), whereas `otherClassName` wouldn't be added as the value is equal to false.

We can swap out `true` and `false` for different values, such as a variable's value. Let' do this for the todo items above.

```html
<ul>
  <li ng-repeat="todo in vm.todos" ng-class="{'complete': todo.complete}">
    <h4>{{ todo.title }}</h4>
    
    {{ todo.complete && 'Completed!' || 'Not completed :(' }}
  </li>
</ul>
```

What is `ng-repeat="todo in vm.todos"` doing for us? We tell Angular what we want to loop over (`vm.todos`) and what variable to put each items properties in (`todo`). We could do `ng-repeat="item in vm.todos"` for example.

`{{ todo.complete && 'Completed!' || 'Not completed :(' }}` looks a bit complicated too, but this is just similar to an expression that we would do in regular JavaScript. This checks the truthy value of `todo.complete`, and if `true` it will display "Completed!". If it's false, it will show "Not completed :(".

Notice that all we have added there is `ng-class="{'complete': todo.complete}"` - this checks our todo item and adds the `complete` class if `todo.complete` is equal to true. It is really that simple!

## Angular Controller and ng Directives Video 

In this video we are going to build a simple CRUD app using controller and built-in `ng` directives.

<iframe width="100%" height="720" src="https://www.youtube.com/embed/2YtGsacxiXE" frameborder="0" allowfullscreen></iframe>

Setting up a dev environment with a live server we're now able to launch the server by `npm run live`.
```
{
  "name": "todo-list-angular",
  "version": "1.0.0",
  "description": "simple todo list with angular",
  "scripts": {
    "live": "live-server",
    "start": "npm run live"
  },
  "author": "",
  "license": "ISC",
  "dependencies": {
  	"angular": "^1.5.8"
  },
  "devDependencies": {
  	"live-server": "^0.9.2"
  }
}
```

Our main html file looks like
```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="UTF-8">
	<title>ToDO App</title>
</head>

<body ng-app="todoApp">
	<h1>Welcome</h1>
	<div ng-controller="ListController as vm">
		<h2>{{ vm.list.name }}</h2>

		<!-- add a task -->

		<button ng-click="vm.startAdd()"
			ng-show="!vm.isInAddMode()">
			Add a Task
		</button>

		<div ng-show="vm.isInAddMode()">
			
			<input placeholder="Task Name"
				ng-model="vm.currentTask.name">
			<button ng-click="vm.add()">Add</button>
			<button ng-click="vm.cancel()">Cancel</button>	

		</div>

		<!-- list of tasks -->

		<div ng-repeat="task in vm.list.tasks | orderBy: '$index' ">

			<!-- normal -read mode version of the task -->

			<div ng-show="vm.isInReadMode(task.id)">
				<p>
					{{ $index +1 }}: {{ task.name }} - completed: {{ task.complete }}
				</p>
				<!-- task options -->
				<button ng-click="vm.startEdit(task.id)">Edit</button>
				<button ng-click="vm.startRemove(task.id)">Delete</button>				
			</div>

			<!-- edit view of the task -->
			
			<div ng-show="vm.isInEditMode(task.id)">
				<input placeholder="task name"
					ng-model="vm.currentTask.name">
				<input type="checkbox" 
					ng-true-value="true"
					ng-false-value="false"
					ng-model="vm.currentTask.complete">
				<button ng-click="vm.save()">Save</button>
				<button ng-click="vm.cancel()">Cancel</button>	
			</div>

			<!-- delete task -->

			<div ng-show="vm.isInRemoveMode(task.id)">
				<p>
					{{ task.name }} - completed: {{ task.complete }}
				</p>
				<button ng-click="vm.remove(task.id)">Remove</button>
				<button ng-click="vm.cancel()">Cancel</button>
			</div>

		</div>

	</div>

	<script src="./js/angular/angular.js"></script>
	<script src="./js/app/app.js"></script>
	<script src="./js/app/list/list_controller.js"></script>
</body>

</html>
```

And our **js/app/app.js**
```js
angular
	.module('todoApp', [])
```

And our controller **js/app/list/list_controller.js**
```js
angular
	.module('todoApp')
	.controller('ListController', ListController);
	// setter, getter

// constructor function
function ListController() {

	// controllerAs syntax
	var vm = this;
	var selectedId = -1; // none of the list tasks
	var addFlag = false;
	var editFlag = false;
	var removeFlag = false;

	vm.currentTask = {};
	vm.startAdd = startAdd;
	vm.startEdit = startEdit;
	vm.isInReadMode = isInReadMode;
	vm.isInEditMode = isInEditMode;
	vm.isInRemoveMode = isInRemoveMode;
	vm.save = save;
	vm.isInAddMode = isInAddMode;
	vm.add = add;
	vm.startRemove = startRemove;
	vm.cancel = cancel;
	vm.remove = remove;
	// we call our protected function

	// kindda like a ruby class method
	vm.list = {
		name: "Main Todo List",
		tasks: [

			{
				id: 1,
				name: "Finish flatiron school",
				complete: false
			},
			{
				id: 2,
				name: "Watch JS tuts",
				complete: false
			},
			{
				id: 3,
				name: "Take some holidays",
				complete: false
			}	

		]		
	};

	// make sure no one is selected and we're in default state
	function reset() {
		selectedId = -1;
		addFlag = false;
		editFlag = false;
		removeFlag = false;		
	}

	function startAdd() {
		reset();
		addFlag = true; // switched on 'isInAddMode' and the div appears
		vm.currentTask = {}; // instantiates a new object
	}

	// shows the form, hides the button
	function isInAddMode() {
		return addFlag;
	}


	// function gets called when 'create task button' is clicked
	// creates the task with the name and complete as false
	function add() {
		// vm.currentTask.name = ... thanks to ng-model
		vm.currentTask.complete = false;
		vm.list.tasks.push(vm.currentTask);
		reset(); // makes the add form disappear
	}

	// tells each task if it is in read (or then in edit mode)
	function isInReadMode(id) {
		return selectedId < 0 || selectedId != id;
	}

	// not in read mode anymore: editmode!
	function isInEditMode(id) {
		return selectedId == id && editFlag
	}	

	function startEdit(id) {
		reset();
		selectedId = id;
		editFlag = true;

		// we search for the current task to populate name and complete
		// like find(id) in ruby
		for ( var i = 0; i < vm.list.tasks.length; i++) {
			var task = vm.list.tasks[i];
			if (task.id == id) {
				vm.currentTask.name = task.name
				vm.currentTask.complete = task.complete
			}
		}
	}

	// will show the delete view template
	function startRemove(id) {
		reset();
		selectedId = id;
		removeFlag = true;
	}

	function save() {
		for (var i = 0; i < vm.list.tasks.length; i++) {
			if (vm.list.tasks[i].id == selectedId) {
				vm.list.tasks[i].name = vm.currentTask.name;
				vm.list.tasks[i].complete = vm.currentTask.complete;
				reset();
			};
		}
	}

	function isInRemoveMode(id) {
		return selectedId == id && removeFlag
	}

	function cancel() {
		reset()
	}

	function remove(id) {
		for (var i = 0; i < vm.list.tasks.length; i++) {
			if (vm.list.tasks[i].id == id) {
				vm.list.tasks.splice(i, 1);
				reset();
			};
		};
	}

}	
```

## Building a simple add button
HTML like
```html
<!doctype html>
<html>
<head>
    <meta charset="utf-8">

    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <title>Angular Application</title>
</head>
<body>

    <h1>Welcome</h1>
    <div ng-app="app">
        <div ng-controller="ContactController as vm">
            <div>
                <input ng-model="vm.currentTask.name" placeholder="Name">
                <input ng-model="vm.currentTask.phone" placeholder="Phone">
                <button ng-click="vm.addContact()">Add</button>
            </div>            
            <ul>
                <li>
                    <h4>{{ vm.currentTask.name }}</h4>
                    <h6>{{ vm.currentTask.phone }}</h6>
                </li>
                <li ng-repeat="contact in vm.contacts">
                    <h4>{{ contact.name }}</h4>
                    <h6>{{ contact.phone }}</h6>
                </li>
            </ul>
        </div>
    </div>

    <script src="js/angular.js"></script>
    <script src="js/app/app.js"></script>
    <script src="js/app/controllers/ContactController.js"></script>

</body>
</html>

```

And controller
```js
function ContactController() {
    var vm = this;

    vm.currentTask = {};

    vm.contacts = [
        {
            name: 'Bob',
            phone: '0123458690'
        },{
            name: 'Tim',
            phone: '3934203242'
        },{
            name: 'Ross',
            phone: '0684059433'
        }
    ];

    vm.addContact = function () {
        vm.contacts.push(vm.currentTask);
        vm.currentTask = {}; // reinit the currentTask    
    }
}

angular
    .module('app')
    .controller('ContactController', ContactController);
```

# Testing with Protractor

First, let's install Protractor, a library for end-to-end feature testing in Angular. As opposed to Karma and Jasmine, we use Protractor to actually test the HTML side of things. Jasmine only let's us test what's happening programatically. With Protractor, we can click on buttons and enter text into inputs, etc. This way, we're interacting with our site the same way our users will and testing the results that they'll get back.

 To install Protractor, go into your command line and enter:

```bash
npm install -g protractor
```

Make sure this is working by entering:

```bash
protractor --version
```

We then need to update `webdriver`, which is provided to us when we install protractor.

```bash
webdriver-manager update
```

Now, we need to start the Selenium Server. This is a webserver that protractor will communicate with to run our tests.

```bash
webdriver-manager start
```

### Writing a test

Let's write a protractor test.

Protractor lets us grab web pages and interact with elements on the page.

To start, we need to load a page to interact with. For this example, we're going to grab Angular's website. To do this, we'll call the `get` method on our `browser` object and pass in a URL. 

```js
describe('Angular Website', function() {
	it('should add a todo', function() {
		browser.get('https://angularjs.org');
	});
});
```

Now, we can select an element on the page using the `element` function. We can select it via multiple different ways. One way to grab an element is using the `ng-model` selector.

Now, the Angular website features a todo example. The `ng-model` value for the input to add a new todo is `todoList.todoText`. Let's grab the element.

```js
describe('angularjs homepage todo list', function() {
	it('should add a todo', function() {
		browser.get('https://angularjs.org');

		element(by.model('todoList.todoText'))
	});
});
```

Now that we've got the element we can actually write inside it, using `.sendKeys`.

```js
describe('angularjs homepage todo list', function() {
	it('should add a todo', function() {
		browser.get('https://angularjs.org');

		element(by.model('todoList.todoText')).sendKeys('Writing tests!!');
	});
});
```

This will type in the element just as if a user was typing!

Now, we need to actually press the `add` button.

```js
describe('angularjs homepage todo list', function() {
	it('should add a todo', function() {
		browser.get('https://angularjs.org');

		element(by.model('todoList.todoText')).sendKeys('Writing tests!!');
		element(by.css('[value="add"]')).click();
	});
});
```

Here, we're grabbing the add button by its CSS selector and then clicking it - so simple!

Now, that was completely useless unless we can check that the todo actually gets added.

Much like the model selector we used above, we can select elements by their `ng-repeat` value.

```js
describe('angularjs homepage todo list', function() {
	it('should add a todo', function() {
		browser.get('https://angularjs.org');

		element(by.model('todoList.todoText')).sendKeys('Writing tests!!');
		element(by.css('[value="add"]')).click();

		var todoList = element.all(by.repeater('todo in todoList.todos'));
	});
});
```

Simple! As multiple items have the `ng-repeat` on them, we need to use `element.all()` instead of `element()` so we get an array of all of the elements.

If you take a look at the todo list, we originally had two todos and now we should have three. We can test the count of items much like our previous tests, by using `expect`.

```js
describe('angularjs homepage todo list', function() {
	it('should add a todo', function() {
		browser.get('https://angularjs.org');

		element(by.model('todoList.todoText')).sendKeys('Writing tests!!');
		element(by.css('[value="add"]')).click();

		var todoList = element.all(by.repeater('todo in todoList.todos'));
		expect(todoList.count()).toEqual(3);
	});
});
```

Sorted! We are now checking that there are three elements. Let's make sure that the new todo matches the text we put into the input.

```js
describe('angularjs homepage todo list', function() {
	it('should add a todo', function() {
		browser.get('https://angularjs.org');

		element(by.model('todoList.todoText')).sendKeys('Writing tests!!');
		element(by.css('[value="add"]')).click();

		var todoList = element.all(by.repeater('todo in todoList.todos'));
		expect(todoList.count()).toEqual(3);
		expect(todoList.get(2).getText()).toEqual('Writing tests!!');
	});
});
```

We can run this test by running `protractor conf.js`. It will then launch a Chrome instance, go to the Angular website and run our tests.

This simplistic API allows us to click and interact with a lot of different items on our pages, so we can test all of our directives functionality.

Another example
```js
describe('angularjs homepage todo list', function() {
	it('should add a new contact', function() {
		browser.get('http://localhost:8080');

		element(by.model('contact.name')).sendKeys('Tim');
		element(by.model('contact.phone')).sendKeys('3934203242');

		element(by.css('[class="button"]')).click();

		var contacts = element.all(by.repeater('contact in vm.contacts'));
		
		expect(contacts.count()).toEqual(4);
		expect(contacts.get(1).element(by.model('contact.name')).getAttribute('value')).toEqual('Tim');
		expect(contacts.get(1).element(by.model('contact.phone')).getAttribute('value')).toEqual('3934203242');

	});
});
```

# Filtering our datasets

Filters are simple functions that we can use to manipulate (or filter) data in Angular.

We've touched on the `ng-repeat` directive for repeating a list of data - wouldn't it be neat if we could filter on that data too? This comes in handy when we have a large dataset and would like to quickly search through it to find the relevant data.

We can do this using the pipe operator (`|`) after the ng-repeat. The syntax for this is `| filterName: value`. We can use different filters (by changing the `filterName` part) and change what the filter criteria is by changing the `value` part.

The filter that we'd use to filter an ng-repeat by a value is simply named `filter`! We can pass a variable to this filter and it will search the whole dataset for us.

```html
<input ng-model="ctrl.search" />

<ul>
	<li ng-repeat="data in ctrl.data | filter: ctrl.search">
	</li>
</ul>
```

This will filter our dataset by the value of the input data - providing us with a really simple yet powerful search filter! As we type in the input, `ctrl.search` gets updated. Angular notices that we're using `ctrl.search` as a filter and filters the repeat by the value. This means that if we type in "bob", only results containing "bob" will be displayed!

## Display values

There are a few other filters that Angular provides us with, that we don't necessarily use for `ng-repeat`s.

Another powerful filter is `date`. This can take a unix timestamp and returns it nicely formatted for us. We use this with the same syntax as above, passing through a string as the value. The string will change how the date is displayed. Check out the docs to see all the ways we can display a date - there's loads!

```html
<abbr>
	{{ ctrl.date | date:'medium' }} <!-- Dec 25, 2016 2:23:56 PM -->
</abbr>
```

## Filtering in Controllers

We can also filter in our controllers, using the `$filter` service. This is the preferred method for filtering on big sets of data as it helps increase performance.

The syntax to use `$filter` is close to what we used above:

```js
$filter('filterName')(data, 'value');
```

This will then return the filtered data.

If we were to use this instead of the filter in an `ng-repeat`, it would look like the following:

```js
function SomeController($filter) {
	this.list = [{
		name: 'Bob'
	}, {
		name: 'Tom'
	}];

	this.search = 'B';

	this.filteredList = $filter('filter')(this.list, this.search);
}
```

We would then use `filteredList` like normal in our `ng-repeat`:

```html
<ul>
	<li ng-repeat="item in ctrl.filteredList">
		{{ item.name }}
	</li>
</ul>
```

# Testing filters

As we learned earlier, we can use either filters in the DOM or in our controllers.

We're going to be writing our filter's tests using Karma and Jasmine - this means we will have to be using the filters in our controllers as we cannot test our DOM. We do this because our filters directly manipulate data, and that's all we need to test. If they manipulated the DOM, we'd test the DOM.

The tests we are about to write are quite similar to tests we've done before. We will be using a controller that filters a list, and we'll be ensuring that filtered list is correct.

Let's take our basic controller. We've got a list of people, a search term and our filtered list. We've got a function to call to re-filter our list when the search term changes (this could be called when a user presses search or by using `ng-change` on the input to fire it whenever the input changes).

```js
function ContactController($filter) {
    this.list = [{
        name: 'Bob'
    }, {
        name: 'Tom'
    }];

    this.search = 'B';

    this.filteredList = $filter('filter')(this.list, this.search);

    this.changeFilter = function () {
        this.filteredList = $filter('filter')(this.list, this.search);
    };
}

angular
    .module('app')
    .controller('ContactController', ContactController);
```

We can now inject this into our tests and checkout the result of `this.filteredList`.

```js
describe('ContactController', function () {
    var $controller;

    beforeEach(module('app'));

    beforeEach(inject(function (_$controller_) {
        $controller = _$controller_;
    }));


    it('should filter the results correctly', function () {
        var $scope = {};
        $controller('ContactController as vm', {$scope: $scope});

        // $scope.vm holds all of our values
    });
});
```

We can access the filtered list via `$scope.vm.filteredList`. Now, our search term is simply `"B"` - meaning we should only receive an array with Bob in it back from the filter. Let's test this out:

```js
describe('ContactController', function () {
    var $controller;

    beforeEach(module('app'));

    beforeEach(inject(function (_$controller_) {
        $controller = _$controller_;
    }));


    it('should filter the results correctly', function () {
        var $scope = {};
        $controller('ContactController as vm', {$scope: $scope});

        expect($scope.vm.filteredList[0]).toEqual({name: 'Bob'});
    });
});
```

If you run the tests now, they will pass!

Now, we need to test that we can change our filter too. To do this, we're going to change `$scope.vm.search` (our search critera) to `"T"`. We can then call our function to re-filter our list, and check the first result again.

```js
it('should re-filter the results correctly when changing search term', function () {
    var $scope = {};
    $controller('ContactController as vm', {$scope: $scope});

    $scope.vm.search = 'T';

    $scope.vm.changeFilter();

    expect($scope.vm.filteredList[0]).toEqual({name: 'Tom'});
});
```

Another example 
```js
describe('ContactController', function () {
    var $controller;

    beforeEach(module('app'));

    beforeEach(inject(function (_$controller_) {
        $controller = _$controller_;
    }));


    it('should filter by gender', function () {
        var $scope = {};
        $controller('ContactController as vm', {$scope: $scope});

        $scope.vm.search = 'female';
        $scope.vm.changeFilter();

        expect($scope.vm.filteredList.length).toBe(71);
    });

    it('should filter by geography', function() {
    	var $scope = {};
    	$controller('ContactController as vm', {$scope: $scope});

    	$scope.vm.search = 'Manchester';
    	$scope.vm.changeFilter();

    	expect($scope.vm.filteredList.length).toEqual(8);
    });

});
```

# Expressions

Anything in between the `{{}}` braces we've been using in our templates is an "expression". We've only been doing *simple* expressions up to this point, just referencing a variable.

However, expressions can be a lot more powerful. We can add, look up indexes/properties in arrays/objects or even use ternary operators (or do most of what we can do in JavaScript, such as `{{ 1 + 1 }}` outputting 2).

### How long?

One common expression that we may use on a day-to-day basis is the length of an array. For instance, we might want to display how many notifications a user has or how many emails they've got. We can do this purely with the `.length` property - much like how we do it in JavaScript!

```html
{{ someArray.length }}
```

It's as simple as that!

### If this.. or that

We can also use a ternary expression. This takes a boolean value and switches what it displays depending if the boolean is true or false.

```html
{{ someArray.length === 0 && 'No emails!' || 'Lots of emails' }}

<h6>You have {{ ctrl.emails.length == 0 && 'no' || ctrl.emails.length }} emails</h6>
```

`No emails!` will be displayed if `someArray.length === 0`. If it isn't equal to zero, `Lots of emails` will be displayed

# Custom Services

Angular allows us, much like controllers, to create custom services. These are very powerful and can do a lot for us, such as communicating with APIs or manipulating data. We can inject these into any controller we'd like to, meaning we won't be repeating ourselves.

This fits perfectly into our "MVVM" pattern. We can create services (our helpers) to do all the "dirty" work for us (communicate with APIs, etc), and we can then utilise them in our controllers. This keeps our controllers thin and all the business logic inside our services.

## .service()

Our services follow the same setup as our custom controllers. We use `.service` to create them! This is the basic setup of a service:

```js
function SomeService() {
	this.someFunction = function () {

	};
}

angular
	.module('app')
	.service('SomeService', SomeService);
```

Very easy! With services, much like our controllers (when using controllerAs), we attach all of our functions to `this`. These will be publicly accessible by anyone who injects the service. We can also create private functions by using normal functions, as such:

```js
function SomeService() {
	function privateMethod() {

	}

	this.publicMethod = function () {
		privateMethod();
	};
}

angular
	.module('app')
	.service('SomeService', SomeService);
```

## Injecting our services

Much like when we used `$timeout`, we can inject our custom services into our controllers by using their name. To inject our `SomeService` above, we just add `SomeService` as an argument to our controller:

```js
function SomeController(SomeService) {
	SomeService.publicMethod();
}

angular
	.module('app')
	.controller('SomeController', SomeController);
```

# Making HTTP requests

In JavaScript, if we need to make HTTP requests, we'd use `XMLHTTPRequest`. This is quite an outdated aspect of JavaScript, and it didn't provide the most simplistic API:

```js
var request = new XMLHttpRequest();

request.onreadystatechange = function() {
	if (request.readyState === 4 && request.status === 200) {
	  console.log('data loaded!');
	}
};

request.open('GET', 'http://api.com/api/method', true);
request.send();
```
That's a lot of work just to make one HTTP request. Luckily, Angular gives us a better way - enter `$http`.  

## What is $http?

$http is a core Angular service that provides a simplistic API to allow us to communicate with HTTP endpoints with ease. It is a wrapper for `XMLHTTPRequest` to allow us to use a simplistic, easy API.

There are a few ways to do requests - let's take a look at them

### $http()

We can use `$http` as a function, passing through a configuration object with it, as such:

```js
$http({
	method: 'GET',
	url: '/someURL'
});

$http({
	method: 'POST',
	data: {
		username: 'Bill'
	},
	url: '/someOtherURL'
});
```

This will return a promise with the data - we call the `.then` function that the function call returns - passing through a callback function that will get called when the request has finished.

A "promise" is just a specification on implementing certain methods. The $http function returns an object of methods, one of them being `then`. We use `then` to execute a callback whenever the "promise" is resolved (the request has finished loading).

```js
$http({
	method: 'GET',
	url: '/someURL'
})
	.then(function (data) {
		console.log(data);
	});
```

This will load the response from our URL, and allow us to consume the data somewhere after it's returned the response.

### $http.get() and $http.post();

$http also gives us helper functions instead of calling it as a function itself.

They act similar to the example above, but as we already have the method in the name we can just pass through the URL we would like as a string.

```js
$http.get('/someURL');

$http.post('/someOtherURL', { username: 'Bill' });
```

### Using these in our services

Now, any usage of `$http` should be done in a custom service that we create. This makes our controllers nice a thin, and allows us to call our API from anywhere in the application. If we didn't abstract our API calls out into a service, we might end up having two calls to the same endpoint somewhere in our application. If that endpoint then changed, we'd have to look around the application for any usage of the endpoint, instead of just changing it once in one file.

This fits into our `MVVM` architecture - thin controllers and all the logic being done by helpers. It means we have code that can be shared between the whole application.

Let's have a look at how we'd put our `$http` usage into our services.

```js
function UserService($http) {
	this.getLoggedInUser = function () {
		return $http.get('/rest/user');
	}
}

angular
	.module('app')
	.service('UserService', UserService);
```

Here we have a function that we can call in our controllers to get information on the currently logged in user. We're returning the `$http` call so we can then use the `.then` method in our controllers to then update our data. You'd consume this data in a controller as follows:

```js
function HeaderController(UserService) {
	var ctrl = this;

	ctrl.user = '';

	UserService
		.getLoggedInUser()
		.then(function (res) {
			ctrl.user = res.data.username;
		});
}

angular
	.module('app')
	.controller('HeaderController', HeaderController);
```

We call our `UserService.getLoggedInUser()` function and then update our controller's values with the response that's returned. Awesome!

Now, we might have a form to update the user's email address. We'd then use `$http.post()` in our service:

```js
function UserService($http) {
	this.getLoggedInUser = function () {
		return $http.get('/rest/user');
	};

	this.updateEmail = function (emailAddress) {
		return $http.post('/rest/user/email', {email: emailAddress});
	};
}

angular
	.module('app')
	.service('UserService', UserService);
```

We could then call this in our controller, after a button is clicked for example:

```js
function SettingsController(UserService) {

	this.emailAddress = ''; // this is bound to an input via `ng-model`

	this.submitForm = function () {
		UserService
	        .updateEmail(this.emailAddress)
	        .then(function () {
	            alert('Email updated!');
	        });
	};
}

angular
	.module('app')
	.controller('SettingsController', SettingsController);
```

# What is $resource?

$resource is a service that creates a resource object for us to communicate with APIs. We pass through a URL and it gives us an object back that looks like this:

```js
var User = $resource('/user/:userId');

/**
 * User = { get: function (),
 *          save: function (),
 *          remove: function ()
 *        }
 */
```

Here, we've defined our URL. Let's break that down:

`/user/:userId`

We're defining our URL as `/user/:userId` - but hold on, we can't have colons in our URLs!?

Well, with $resource, using a colon in a URL means that section is *actually* a variable. `:userId` means that we aren't actually going to put `:userId` into our URL, rather that we will be replacing `:userId` with an actual user ID. This allows us to put our data into our URL - for instance, we would end up querying `/user/1` or `/user/1231938`. All requests will go to the same URL, unless we don't specify a userId. If we don't specify a userId, it will just go to `/rest/user`.

Now, our `User` variable is equal to an object containing multiple functions. We can call these to make the appropriate requests.

### Usage in a service

To use this in our service, we'd define our `$resource` at the top, and then different methods will use that resource.

```js
function UserService($resource) {
	var User = $resource('/user/:userId');

	this.getUser = function (userId, callback) {
		User.get({userId: userId}, callback);
	};
}
```

And then we can use that as follows in our controllers:

```js
function MyController(UserService) {
	UserService.getUser(3, function (user) {
		console.log(user);
	});
}
```

### Reading

When we call `.get()`, you've guessed it - it makes a GET request for us. As the first argument, we pass in an object with the data we need for request. In the case of our endpoint above, we need to pass in an object with a `userId` property, in order for Angular to replace `:userId` with the actual user's ID.

```js
User.get({userId: 3}, function (user) {
	console.log(user);
});
```

Our second argument is a callback that gets fired when the request completes. This will make a GET request to `/user/3` (as we've passed in 3 as the `userId`).

If we were to still be using `$http`, it would look like this:

```js
$http
	.get('/rest/user/3')
	.then(function (user) {
		console.log(user)
	});
```

### Updating and Creating

Now, we can create new users and also update previous users using the `.$save()` function. This will issue a POST request to the same URL as above.

#### Updating
For existing users, we'd do any modifications inside the `.get` callback, as we already have received the user. Note: we use `$save()` inside the `.get` callback as we may have a property named `save` on the user.

```js
User.get({userId: 3}, function (user) {
	console.log(user);

	user.email = newEmailAddress;

	user.$save();
});
```

#### Creating
When we want to create a new user, we just simply create a new instance of `User`, and then call `.$save()` again.

```js
var user = new User();

user.name = 'Bill Gates';
user.email = 'bill@microsoft.com';

user.$save();
```

This will issue a POST request again, with details about our new user.

The `$http` equivalent is:

```js
$http
	.post('/rest/user', {name: 'Bill Gates', email: 'bill@microsoft.com'})
	.then(function (user) {
		console.log(user)
	});
```

### Removing

We can also delete users, using `.$delete()`.

```js
User.get({userId: 3}, function (user) {
	console.log(user);

	user.email = newEmailAddress;

	user.$delete();
});
```

```js
$http
	.delete('/rest/user/3')
	.then(function (user) {
		console.log(user)
	});
```

# What is a HTTP interceptor?

Now, using `$http` or `$resource` means we're going to end up doing a lot of HTTP requests in our applications.

Eventually, we may need to manipulate all of the requests, or even take a wide-look at all the responses and handle any errors globally instead of on an individual case - we can do this with HTTP interceptors.

We might also want to retry requests if they fail. We can do this with HTTP interceptors!

HTTP interceptors allow us to define functionality that will happen before every request is made, or just after every request has come back from the server. This means we can append things to every request we make, or handle errors that may arise from the backend (it's better to do this in an interceptor and have application-wide error handling, rather than doing it for every possible request we make).

HTTP interceptors are just simple services that we then push into an interceptors array in the `$httpProvider` service.

First, let's look at how we'd make the service:

```
function MyInterceptor() {

}

angular
	.module('app')
	.service('MyInterceptor', MyInterceptor)
	.config(function ($httpProvider) {
		$httpProvider.interceptors.push('MyInterceptor');
	});
	// This last call pushes our new interceptor into the $httpProvider interceptor array
```

If this looks familiar - it is! Now you might be wondering how we actually intercept things.

There are certain functions we can attach to our interceptor service - Angular will look if they exist, and then run them if they do.

### Before a request

Now, to intercept the request before it is actually made, we need to define the function `request` on `this`.

```
function MyInterceptor() {
	this.request = function (config) {
		// this will be fired before each request!
	};
}

angular
	.module('app')
	.service('MyInterceptor', MyInterceptor)
	.config(function ($httpProvider) {
		$httpProvider.interceptors.push('MyInterceptor');
	});
```

We can now manipulate our request by editing the `config` variable passed through. For instance, if we want to add another header to our request, we just modify `config.headers`.

```
function MyInterceptor() {
	this.request = function (config) {
		config.headers['X-Requested-From'] = 'Angular';
		return config;
	};
}

angular
	.module('app')
	.service('MyInterceptor', MyInterceptor)
	.config(function ($httpProvider) {
		$httpProvider.interceptors.push('MyInterceptor');
	});
```

This will append the `X-Requested-From` header to every single request going through `$http`!

### After a request

We can also intercept after a request has been completed (but before we return the results to our controllers/services) by attaching the function `response`.

We might want to log what time the request came back:

```
function MyInterceptor() {
	this.response = function (config) {
		config.config.responseTime = Date.now();
		return config;
	};
}

angular
	.module('app')
	.service('MyInterceptor', MyInterceptor)
	.config(function ($httpProvider) {
		$httpProvider.interceptors.push('MyInterceptor');
	});
```

We can then check when the request was completed in our services!

### After an error

We can just purely kick in our interceptor after an error too. We could have some service to display notifications to the user, and we can invoke this service in our interceptor if there was an error. We can do this by the `responseError` function.

```
function MyInterceptor(NotificationService) {
	this.responseError = function (config) {
		NotificationService
			.showError(config);
	};
}

angular
	.module('app')
	.service('MyInterceptor', MyInterceptor)
	.config(function ($httpProvider) {
		$httpProvider.interceptors.push('MyInterceptor');
	});
```

(NotificationService will be a custom service that we have made, alerting the user when we call `.showError`)

# Testing Services

Our services are grabbing and manipulating data all over the place, and as we may be using them all over our application, it is important that we test our services to ensure that when we change them, we don't break our application.

## Grabbing our services

Previously, we've been using `$controller` to get our controllers, so logically we should be using `$service` to grab our services. Unfortunately, it's not that simple. We use `$controller` to both grab and instantiate our controllers. We don't need to instantiate our services, so we use a nice service named `$injector`!

Let's take a look at how we'd grab our service:

```js
describe('OurService', function () {
    beforeEach(module('app'));

    var OurService;

    beforeEach(inject(function ($injector) {
        OurService = $injector.get('OurService');
    }));


    it('should test our service', function () {
        // We can use OurService here
    });

});
```

It's a little bit different from before, but not an issue! Still really simple.

We can now access all of our public methods our service gives us, and then test the results.

For instance, for our `MathService` that we used earlier on in the series, we can test it as follows -

```js
describe('MathService', function () {
    beforeEach(module('app'));

    var MathService;

    beforeEach(inject(function ($injector) {
        MathService = $injector.get('MathService');
    }));


    it('should add up correctly', function () {
        expect(MathService.sum([1,23]).toEqual(24);
    });
});
```

Yes, it's that simple!

## Testing $http calls

Now, our services are also going to be calling `$http` a lot, and it would be a lot of effort to mock an entire backend. Luckily, ngMocks provides us with a nice little tool called `$httpBackend`. This allows us to mock our API calls.

There are three parts to `$httpBackend`:

### $httpBackend.when

We use `$httpBackend` to setup the responses to our HTTP calls. It accepts a method and a URL, and allows us to define the response that we'd get back.

If we have a backend endpoint at `/rest/user` that responds with the current user's information, we can mock it as follows:

```js
describe('UserService', function () {
    beforeEach(module('app'));

    var UserService, $httpBackend;

    beforeEach(inject(function ($injector) {
        UserService = $injector.get('UserService');
        $httpBackend = $injector.get('$httpBackend');

        $httpBackend.when('GET', '/rest/user').respond({user: 'Bill Gates', email: 'bill@microsoft.com'});
    }));
});
```

### $httpBackend.expectGET

Now, when we actually test the service's function that calls that endpoint, we need to tell ngMocks that we're expecting the request to occur. We do this by calling `$httpBackend.expectGET` with the endpoint we're expecting to have a request to.

```js
describe('UserService', function () {
    beforeEach(module('app'));

    var UserService, $httpBackend;

    beforeEach(inject(function ($injector) {
        UserService = $injector.get('UserService');
        $httpBackend = $injector.get('$httpBackend');

        $httpBackend.when('GET', '/rest/user').respond({user: 'Bill Gates', email: 'bill@microsoft.com'});
    }));

    it('should get the current users information', function (done) {
        $httpBackend.expectGET('/rest/user');
    });
});
```

We're now setup to receive the mocked backend response. Our response will have several properties, with the `data` property referring to the body of our response. In this case, It'll be an object with `name` equal to `Bill Gates` and his email too.

```js
describe('UserService', function () {
    beforeEach(module('app'));

    var UserService, $httpBackend;

    beforeEach(inject(function ($injector) {
        UserService = $injector.get('UserService');
        $httpBackend = $injector.get('$httpBackend');

        $httpBackend.when('GET', '/rest/user').respond({user: 'Bill Gates', email: 'bill@microsoft.com'});
    }));

    it('should get the current users information', function (done) {
        $httpBackend.expectGET('/rest/user');

        UserService
          .getUserInfo()
          .then(function (res) {
            var data = res.data;
            if (data.email === 'bill@microsoft.com' && data.user === 'Bill Gates') {
              done();
            }
          });
	});
});
```

Here, instead of using `expect().toBe()`, we call a function named `done()` if our response is correct. This means that we can do asynchronous tests in Jasmine. An important item to note here is that we must pass the `done` function in as a argument to this test for this feature to work. 

### $httpBackend.flush()

We then need to call `$httpBackend.flush()` to immediately execute all pending requests (which then fires off our request, calling our callback with the returned data and runs the test). If we don't call `$httpBackend.flush()` we'll get a timeout on Karma's test page, the tests waiting to be launched.

```js
describe('UserService', function () {
    beforeEach(module('app'));

    var UserService, $httpBackend;

    beforeEach(inject(function ($injector) {
        UserService = $injector.get('UserService');
        $httpBackend = $injector.get('$httpBackend');

        $httpBackend.when('GET', '/rest/user').respond({user: 'Bill Gates', email: 'bill@microsoft.com'});
    }));

    it('should get the current users information', function (done) {
        $httpBackend.expectGET('/rest/user');

        UserService
          .getUserInfo()
          .then(function (res) {
            if (res.email === 'bill@microsoft.com' && res.user === 'Bill Gates') {
              done();
            }
          });

        $httpBackend.flush();
	});
});
```

All done! We've now got a fully tested `UserService`, including mocked HTTP requests.

Another Example with a UserService
```js
function UserService($http) {
	this.getUser = function () {
		return $http.get('/rest/user');
	};

	this.createFullName = function (user) {
		return user.first_name + ' ' + user.last_name
	};
}

angular
	.module('app')
	.service('UserService', UserService);
```

and the test
```js
describe('UserService', function () {

	beforeEach(module('app'));

	var UserService, $httpBackend;

	beforeEach(inject( function($injector){
		UserService = $injector.get('UserService');
		$httpBackend = $injector.get('$httpBackend');

		$httpBackend.when('GET', '/rest/user').respond({first_name: 'Bill', last_name: 'Gates'});
	}));

	it('Should get the user first and last names', function(done) {
		$httpBackend.expectGET('/rest/user');

		UserService
			.getUser()
			.then(function(res){
				var user = res.data;
				if (user.first_name === 'Bill' && user.last_name === 'Gates') {
					done();
				}
			});

		$httpBackend.flush();	
	});

	it('should add name and last name together', function(){
		var user = {first_name: 'Bill', last_name: 'Gates'};
		expect(UserService.createFullName(user)).toEqual('Bill Gates');
	});
});
```

# Custom Directives

Nowadays, most frontend applications are made up of small, reusable components. If we imagine a car, it would be made up with components such as wheels, windows, engine, etc. In our case, the components that make up our website would be a header, footer, dropdown menu, toggles, etc.

We can create these components using directives. We've already used directives that Angular gives us, but we can also make our own.

Directives can both be HTML attributes and HTML elements. Most of our directives will be HTML elements, as they will have their own template inside of themselves instead of modifying the behaviour of existing elements.

We might create a custom directive called "dropdown". This dropdown directive will have it's own template that will get put into the DOM, so we create it as a HTML element instead.

In plain JavaScript, our dropdown might look [something like this](https://jsfiddle.net/ogyzmx7r). There's a lot of code here that will be common to other elements, such as selecting and replacing elements from the page. Now let's check out [what it is like in Angular](https://jsfiddle.net/ogyzmx7r/1/). You'll notice how we use a custom HTML element (`<dropdown>`) and the code we need is a lot simpler and easier to read! Let's learn all about them.

## Creating a custom directive

Much like services and controllers, we can use the `.directive` function to create our directives.

Our directive names are what we then use to reference them in the DOM. However, as the DOM is case-insensitive, we change the capital letters in our name to hypens. For instance, the directive name `myDirective` becomes `<my-directive></my-directive>`. `userDropdownList` will become `<user-dropdown-list></user-dropdown-list>`.

Let's look at a custom directive:

```js
function MyDirective() {
	return {
		template: '<div>Hello world!</div>'
	};
}

angular
	.module('app')
	.directive('myDirective', MyDirective);
```

You'll notice that in our directive function we return an object - this describes all the functionality and configuration of our directive. The function name is a capital letter but the directive name is always camel case - this is to keep function names consistent when compared to our custom services, filters, etc.

We can then use `myDirective` in the DOM, and it will be replaced by the template you see above.

```
<my-directive></my-directive>
```

Would then be transformed into

```
<my-directive>
	<div>
		Hello world!
	</div>
</my-directive>
```

When rendered by Angular! This is an extremely basic directive, we're going to look into making them much more advanced in the next few readmes!

# Restricting Directive usage

Angular allows us to set a property named `restrict` on the object we return on our directive definition. We can pass through a string with certain letters letting Angular know how our directive can be used.

```js
function MyDirective() {
	return {
		restrict: 'E',
		template: '<div>Hello world!</div>'
	};
}

angular
	.module('app')
	.directive('myDirective', MyDirective);
```

Above, we've got `restrict` set to `E`. This stands for element, meaning our directive can only be used as an element.

The letters available are:

`A` - used as an attribute
`E` - used as an element
`C` - used as a class name
`M` - used as a comment

They would be used as the following:

```html
Attribute - <div my-directive></div>
Element - <my-directive></my-directive>
Class: <div class="my-directive"></div>
Comment - <!-- directive: my-directive -->
```

You might've noticed that we can use directives in class names and comments too. This isn't recommended however, as it is unclear if we're just doing a normal HTML comment or invoking a directive. It also isn't clear if we're adding a class to an element or invoking a directive too.

You can use the individual letters or put them together - `'EA'` will allow the directive to be used as an element and an attribute.

By default, restrict is set to 'EA'.

# Template and templateUrl

## Overview

We've created a directive with a template - let's take a deeper look into that. You might've noticed that we've created a template item in our directive's object. This will be put into the DOM where the directive is invoked. Templates can only contain one root element! If we use more, Angular will error because it can't keep track of the elements properly.

This is okay:
```html
<div>
	Woo our directive goes here!
</div>
```

This will not work:

```html
<div>
	Woo our directive goes here!
</div>
<span>What about here - oh no!</span>
```
## templateUrl

As our templates get more complex, they can become difficult to read inside of our controller function. In the example below, we're saving each line of our template as a seperate element in an array, then joining the elements together. 

```js
function MyDirective() {
	return {
		template: [
        '<div class="dropdown">',
			'<button class="dropdown__title">',
				'Options',
			'</button>',
			'<ul class="dropdown__list">',
				'<li class="dropdown__item">',
					'<a class="dropdown__link" href="#">',
						'Edit',
					'</a>',
				'</li>',
				'<li class="dropdown__item">',
					'<a class="dropdown__link" href="#">',
						'Transfer',
					'</a>',
				'</li>',
				'<li class="dropdown__item">',
					'<a class="dropdown__link dropdown__link--delete" href="#">',
						'Delete',
					'</a>',
				'</li>',
			'</ul>',
        '</div>'
      ].join('')
	};
}

angular
	.module('app')
	.directive('myDirective', MyDirective);
```

To avoid our directives getting too big like above, we can also use `templateUrl` instead, pointing to a HTML file instead. This can be incredibly useful for any large directives.

```js
function MyDirective() {
	return {
		templateUrl: 'directive.html'
	};
}

angular
	.module('app')
	.directive('myDirective', MyDirective);
```

directive.html:

```html
<div>
	Wow, our directive in another file!
</div>
```

This would work the same as if we had it as a string in our directive - neat! 

Normally we'd store our views in a folder inside our module folder `js/moduleName` inside a folder named `views`. This keeps everything all together!

# Replacing base markup

When we put our directive into the DOM, you'll notice that what will happen is this:

```html
<our-directive>
	<div>
		Directive contents here!
	</div>
</our-directive>
```

However, you may not want the `our-directive` HTML element to be there - you might prefer only semantic, proper DOM nodes to be in the DOM. It's completely your choice - there's no benefit to either way.

To get rid of this, we can set the replace property on our object to `true`.

```js
function OurDirective() {
	return {
		replace: true,
		template: '<div>Hello world!</div>'
	};
}

angular
	.module('app')
	.directive('ourDirective', OurDirective);
```

When this is rendered, we won't see `our-directive` in the HTML!


# Inheriting or isolating scope
Now, one cool thing about our directives is that they can display dynamic data. For instance, we might want to have a Twitter card to display a users Twitter handle, along with a link to follow said user.

We can do this exactly like we've done in our views so far - using `{{}}`.

Note: now that we've started using more HTML in our directives, instead of just passing a string, we pass in a multi-line array, joined by an empty string. This means we can have a multi-lined template without having to worry about string concatenation. This is great for small templates, but as our templates get larger we should move out into a separate file.

Lets create the Twitter card.

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/">Follow @username on twitter!</a>',
			'</div>'
		].join(''),
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

Now that's cool, but how do we *actually* get our data? Well, we can actually inherit it from the scope above.

Let's assume we've got a controller, that has a property on it's scope named `twitter`. We would display this in our view as follows:

```html
<div ng-controller="SomeController">
	{{ twitter }}
</div>
```

If we were to use our Twitter card directive instead of displaying `{{ twitter }}`, we could actually use `{{ twitter }}` in our directives template.

```html
<div ng-controller="SomeController">
	<twitter-card></twitter-card>
</div>
```

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/{{ twitter }}">Follow @{{ twitter }} on Twitter!</a>',
			'</div>'
		].join(''),
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

This will result in this HTML being put into the DOM (we're assuming `$scope.twitter` equals `billgates`.)

```html
<div ng-controller="SomeController">
	<twitter-card>
		<div class="twitter">
			<a href="https://twitter.com/billgates">Follow @billgates on Twitter!</a>
		</div>
	</twitter-card>
</div>
```

This is awesome, but what if we want to use our Twitter card twice? Isn't that the point of directives, the ability to reuse them again and again?

One ridiculous way of doing this is to create a new controller for every Twitter card we want to show, assigning all of the different usernames we want to display to their own controller - surely there must be a better way?

## Isolate Scope

Aha! There is! It's called isolate scope. What this does is creates a new scope for our directive - it can either be a completely brand new one or copied from our parent.

In our directive's object, we can attach a property named `scope` to it. This can have a few different values:

### scope: false

If `scope` is equal to `false`, then no new scope is created. This is the same as not having `scope` set (like in our examples above).

### scope: true

If `scope` is equal to `true`, we create a new scope for our directive. This is copied over from the parent scope. If we put `scope` as `true` in our examples above, nothing would change *visually*. However, if we changed the twitter handle, it would update in the controller's scope, but not the directive's.

If we imagine this:

```html
<div ng-controller="SomeController">
	{{ twitter }}
	<twitter-card></twitter-card>
</div>
```

We'd end up with this being rendered:

```html
<div ng-controller="SomeController">
	billgates
	<twitter-card>
		<div class="twitter">
			<a href="https://twitter.com/billgates">Follow @billgates on Twitter!</a>
		</div>
	</twitter-card>
</div>
```

If we were to then update `$scope.twitter` in `SomeController`, we'd end up with:

```html
<div ng-controller="SomeController">
	new value!
	<twitter-card>
		<div class="twitter">
			<a href="https://twitter.com/billgates">Follow @billgates on Twitter!</a>
		</div>
	</twitter-card>
</div>
```

The Twitter handle inside `<twitter-card>` hasn't changed. This is because we've created a new scope (initially based off of the parent scope) - they are no longer linked!

### scope: {}

Now, this is where things get funky. We can pass through an object to our scope object - but why?

When we use normal HTML elements, such as `<input />`, we configure it via attributes. For instance, we might give it a name - we'd do this like such:

```html
<input name="ourInputName" />
```

Hold on a minute.. Can we configure our directives by passing through attributes?

Yes we can!

To do this, we need to specify *what* attributes we want to be configured by. Using our Twitter card above, the only thing we need to configure it is the Twitter handle.

To grab this value out of the attributes, we can specify the attribute name in the object. For instance, if we wanted to utilise the Twitter card as such:

```html
<twitter-card handle="billgates"></twitter-card>
<twitter-card handle="bob"></twitter-card>
```

We'd put the property `handle` into our scope object.

Now, what do we put as the value? There are two that we can use:

#### @ (at)

If we pass through `@` as the value, as so:

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/{{ handle }}">Follow @{{ handle }} on Twitter!</a>',
			'</div>'
		].join(''),
		scope: {
			handle: '@'
		},
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

What `@` tells Angular is to just copy the value as it is. This will literally copy whatever we put in the `handle` attribute and put it into our scope.

#### = (equals)

However, if we want to be able to receive variables through, we can use `=`.

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/{{ handle }}">Follow @{{ handle }} on Twitter!</a>',
			'</div>'
		].join(''),
		scope: {
			handle: '='
		},
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

What this means is that if we have a controller with two properties on it, such as `twitterHandle1` and `twitterHandle2`, we can do this:

```html
<twitter-card handle="twitterHandle1"></twitter-card>
<twitter-card handle="twitterHandle2"></twitter-card>
```

Angular will then change the values over to their actual scope values before passing the value through to our directive. This also means that if we were to update either of them, Angular will automatically update our directive to match it too. Awesome! There's not really any reason why you wouldn't want the directive to update with the latest values, but if you ever do, the option is baked in.

#### Changing attribute names

Notice how we've updated our template to use `{{ handle }}`? This is because our `$scope` has the property `handle` on it now, because of the object.

However, you might not like this - you might have wanted to stick with `{{ twitter }}` but *also* have it configured by using the attribute `handle`. To do this, we can change the object property to `twitter` and we put `handle` after the `@` or `=`, like follows:

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/{{ twitter }}">Follow @{{ twitter }} on Twitter!</a>',
			'</div>'
		].join(''),
		scope: {
            twitter: '@handle'
        },
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

This means we can do this still:

```html
<twitter-card handle="billgates"></twitter-card>
```

Whilst populating `$scope.twitter` with the value. There's no advantage to this or real reason as to why you'd need to use it, but the flexibility is there if you need it.

Another exxample
```js
function ContactCard(){
	return {
		scope: {
			name: '=',
			email: '=',
			phone: '='
		},		
		template: [
			'<div>',
			    '<h4>Contact Card</h4>',
			    '<label>Name:</label> {{ name }}',
			    '<label>Email:</label> {{ email }}',
			    '<label>Phone:</label> {{ phone }}',
			'</div>'
		].join(''),
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('contactCard', ContactCard);
```

And in the view
```html
<div ng-app="app" class="app">
    <div ng-controller="ContactController as ctrl">
        <ul>
            <li ng-repeat="contact in ctrl.contacts">
                <contact-card name="contact.name" email="contact.email" phone="contact.phone"></contact-card>
            </li>
        </ul>
    </div>
</div>
```

## Directive Controllers

We can create controllers for our directives - awesome! We'd generally use these for functions to change data or retrieve data from a service (we might have a list of contacts), or manipulate the data given us (we might want to verify an email address or phone number for a contact).

Our controllers, much like the controllers we've created before, allow us to directly access `$scope` (the values passed through to us from attributes), as well as all the services that we have created, as well as built-in ones too, such as `$timeout`.

## But, how?

You've probably guessed how we can do this in your head. We attach a property named `controller` to our directives object!

This, for now, will take a function that will become our directive's controller:

```html
<twitter-card handle="billgates"></twitter-card>
```

This will be the code to initiate all of our examples. Below, we'll define our controller function and inject `$scope`. Our `$scope` will have a property called `handle` that will be set to `"billgates"`!

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/{{ handle }}">Follow @{{ handle }} on Twitter!</a>',
			'</div>'
		].join(''),
		scope: {
            handle: '@'
        },
        controller: function ($scope) {
            // $scope.handle returns 'billgates' 
        },
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

Now we can use our controller exactly like what we've done before. We can manipulate data, or call a `$timeout`. For example, we could do this:

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/{{ twitter }}">Follow @{{ twitter }} on Twitter!</a>',
			'</div>'
		].join(''),
		scope: {
            handle: '@'
        },
        controller: function ($scope, $timeout) {
            $timeout(function () {
                $scope.handle = 'angularjs'
            }, 5000);
        },
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

This will set our Twitter handle to "angularjs" after 5 seconds.

## controllerAs

As you've learned already, the best practice is in fact to use the `controllerAs` syntax. But we're passing a function through as our controller, so how are we going to tell Angular that we want to use `controllerAs`? You guessed it - the `controllerAs` property.

Much like our `ng-controller`, where we use `SomeController as some`, we use `controllerAs` and put it's value as `some` (or whatever you want to call it).

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/{{ handle }}">Follow @{{ handle }} on Twitter!</a>',
				'<button ng-click="ctrl.changeHandle()">Change Handle</button>',
			'</div>'
		].join(''),
		scope: {
            handle: '@'
        },
        controller: function ($scope) {
            // $scope.handle === 'billgates'

            this.changeHandle = function () {
                $scope.handle = 'angularjs';
            };
        },
        controllerAs: 'ctrl',
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

As you can see here, we're setting our controller as `ctrl`. This means that anything we attach to `this` in the controller will be accessible via the `ctrl` object in our template - exactly like our controllers before!

You might have noticed how `handle` is still on our `$scope` object - this is because it's passed through as a scope property. We'll cover how to get that into `this` soon.

We've got a function to change our Twitter handle. This updates `$scope` - where our data is stored. As we trigger this event using `ng-click`, any changes that we do to `$scope` inside the function is automatically reflected in the view.

## Existing Controllers

Instead of a function, we can pass through a string to the `controller` property as well - much like what we do with `ng-controller`. This means we can use an existing controller as our directive's controller. It also means that we can remove the `controllerAs` property if we're using a string, as we can do `'SomeController as some'`.

```html
<twitter-card handle="billgates"></twitter-card>
```

```js
function TwitterController($scope) {
	// $scope.handle === 'billgates';
}

angular
	.module('app')
	.controller('TwitterController', TwitterController);

function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="https://twitter.com/{{ handle }}">Follow @{{ handle }} on Twitter!</a>',
				'<button ng-click="ctrl.changeHandle()">Change Handle</button>',
			'</div>'
		].join(''),
		scope: {
            handle: '@'
        },
        controller: 'TwitterController as ctrl',
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

Here we've got our controller initiated with our scope data, ready for us to manipulate it.

Now we can manipulate our data to our hearts content. Our controllers can also have our services (such as `$timeout` or a custom service) injected so we can utilise the power of them in our directives too!

Example: let's put the username to lowercase
```js
function ContactCard() {
	return {
		scope: {
			name: '=',
			email: '=',
			phone: '=',
			username: '='
		},
		template: [
			'<div>',
				'<h4>Contact Card</h4>',
				'<label>Name:</label>',
				'{{ name }}',
				'<label>Email:</label>',
				'{{ email }}',
				'<label>Phone:</label>',
				'{{ phone }}',
				'<label>Username:</label>',
				'<span class="username">{{ username }}</span>',
			'</div>'
		].join(''),
		controller: function($scope){
			$scope.username = $scope.username.toLowerCase();
		},
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('contactCard', ContactCard);
```

# bindToController

`bindToController` works exactly like our `scope` property, but puts the items into `this` instead of `$scope`. This is awesome - as we're going to be using `controllerAs`, we should have all of our values assigned the same variable.

Let's take a look at how we'd convert our directives over to using `bindToController`:

### Before

```js
function TwitterCard() {
	return {
    		template: [
    			'<div class="twitter">',
    				'<a href="{{ twitter.twitterLink }}/{{ handle }}">Follow @{{ handle }} on Twitter!</a>',
    			'</div>'
    		].join(''),
    		scope: {
    		    handle: '='
    		},
    		controller: function ($scope) {
    			// $scope.handle === 'billgates'

    			this.twitterLink = 'https://twitter.com';
    		},
    		controllerAs: 'twitter',
    		restrict: 'E'
    	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

You'll notice the inconsistency - we're using `{{ handle }}` as well as `{{ twitter.twitterLink }}`. This is data from our scope (passed through to the directive) as well as directive from our controller (using `this` to match best practices). Mixing the two isn't good!

### After

To fix this, we'll add a property called `bindToController` to our directive containing the values we want to have passed through. 

```html
<twitter-card handle="billgates"></twitter-card>
```

```js
function TwitterCard() {
	return {
		template: [
			'<div class="twitter">',
				'<a href="{{ twitter.twitterLink }}/{{ twitter.handle }}">Follow @{{ twitter.handle }} on Twitter!</a>',
			'</div>'
		].join(''),
		scope: {},
		controller: function () {
			// this.handle === 'billgates'

			this.twitterLink = 'https://twitter.com';
		},
		controllerAs: 'twitter',
        bindToController: {
            handle: '='
        },
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('twitterCard', TwitterCard);
```

Order is restored. We now have consistency! All of our values are now added to our controller's `this` object - meaning we're only accessing our data from our controller now!

You might have noticed how we've still got our `scope` property - this is to tell Angular that we do still want a brand new scope - we're just not attaching anything to it.

Another example
```js
function ContactCard() {
	return {
		scope: {},
		template: [
			'<div>',
				'<h4>Contact Card</h4>',
				'<label>Name:</label>',
				'{{ contact.name }}',
				'<label>Email:</label>',
				'{{ contact.email }}',
				'<label>Phone:</label>',
				'{{ contact.phone }}',
				'<label>Username:</label>',
				'<span class="username">{{ contact.username }}</span>',
			'</div>'
		].join(''),
		controller: function(){
			
		},
		controllerAs: 'contact',
		bindToController: {
			name: '=',
			email: '=',
			phone: '=',
			username: '='			
		},
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('contactCard', ContactCard);
```

And the HTML
```html
<div ng-app="app" class="app">
    <div ng-controller="ContactController as ctrl">
        <ul>
            <li ng-repeat="contact in ctrl.contacts">
                <contact-card
                        name="contact.name"
                        email="contact.email"
                        phone="contact.phone"
                        username="contact.username" />
            </li>
        </ul>
    </div>
</div>
```

## Sharing directive controllers with require

We can require the parent controller for a certain directive by using the `require` property in our directive. We pass in a string, with the directives name that we want.

Following on from our example above, we might have the following setup:

```html
<tabs>
  <tab label="Tab 1">
    Tab 1 contents!
   </tab>
   <tab label="Tab 2">
    Tab 2 contents!
   </tab>
   <tab label="Tab 3">
    Tab 3 contents!
   </tab>
</tabs>
```

If we ran this now, our `tabs` component wouldn't know about the child tabs, and there is no list of tabs to choose from when we want to change what tab is active. This is where require comes in! Require allows us to notify the parent that it exists, so we can have a list of tabs at the top to change the active tab.

Imagine our `tabs` directive looks like this:

```js
function tabs() {
  return {
    restrict: 'E',
    scope: {},
    transclude: true,
    controller: function () {
      this.tabs = [];
    },
    controllerAs: 'tabs',
    template: [
      '<div class="tabs">',
        '<ul class="tabs__list"></ul>',
        '<div class="tabs__content" ng-transclude></div>',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('tabs', tabs);
```

You might notice a property we haven't mentioned before - `transclude`. Don't worry about this yet, we're going to learn this very shortly!

In each tab, we've got a label for the tab. We're going to want to put this inside our `tabs__list` list. However, inside the `tabs` component we don't actually know what tabs we have inside the element.

One easy way to populate this list is if each of our `tab` directives notify our `tabs` directive that they exist. In our example, we've got three `tab` elements, so each of these will notify the parent controller.

Imagine our `tab` directive looked like this:

```js
function tab() {
  return {
    restrict: 'E',
    scope: {
      label: '@'
    },
    require: '^tabs',
    transclude: true,
    template: `
      <div class="tabs__content" ng-if="tab.selected">
        <div ng-transclude></div>
      </div>
    `,
    link: function ($scope, $element, $attrs) {

    }
  };
}

angular
  .module('app', [])
  .directive('tab', tab)
  .directive('tabs', tabs);
```

You'll notice we've added `require` with the value `^tabs` - this is telling Angular to require the parent controller from our `tabs` component.

Here, with `transclude` we have a simple sort-of "transparent" directive (our content is passed into our directive, not replaced). What this does (and again, more on the whole tranclusion concept later) is wrap our contents in a new `<div />`. For instance:

```html
<tab label="Tab 3">
	Tab 3 contents!
</tab>
```

Will become:

```html
<tab label="Tab 3">
	<div class="tabs__content" ng-if="tab.selected">
		<div ng-transclude>
			Tab 3 contents!
		</div>
	</div>
</tab>
```

You'll notice we've also got a property named `link`. We're going to learn more about this later, but for now, assume that it is magic and we're going to be using it in this example.

Normally, our link function has three parameters - scope (`$scope`), element (the mounted DOM element) and attrs (the attributes passed through to the directive). However, when we use `require`, we get a fourth - ctrl. This will be equal to the parents (directive) controller, allowing us to access everything to do with it.

Let's add an `addTab` method to our `tabs` directives controller. This will add a tab to the list so we can repeat and display the tabs labels at the top of the directive, so the user can click on them to change the active tab.

```js
function tabs() {
  return {
    restrict: 'E',
    scope: {},
    transclude: true,
    controller: function () {
      this.tabs = [];

      this.addTab = function (tab) {
        this.tabs.push(tab);
      };
    },
    controllerAs: 'tabs',
    template: [
      '<div class="tabs">',
        '<ul class="tabs__list"></ul>',
        '<div class="tabs__content" ng-transclude></div>',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('tabs', tabs);
```

Now, if we access the fourth argument in our link function inside our `tab` directive:

```js
function tab() {
  return {
    restrict: 'E',
    scope: {
      label: '@'
    },
    require: '^tabs',
    transclude: true,
    controllerAs: 'tabs',
    template: [
      '<div class="tabs__content" ng-if="tab.selected">',
        '<div ng-transclude></div>',
      '</div>'
    ].join(''),
    link: function ($scope, $element, $attrs, $ctrl) {
        // $ctrl = { tabs: [], addTab: func(){} }
    }
  };
}

angular
  .module('app', [])
  .directive('tab', tab)
  .directive('tabs', tabs);
```

You'll see that we can now access the parent's directive controller and methods! From here, we can add the tab information in to our parent's tab array.

#### Example
```js
function Tab() {
	return {
		restrict: 'E',
		scope: {
			label: '@'
			// from the view <tab label="Tab 1">
		},
		require: '^tabs',
		transclude: true,
		template: [
    	    '<div class="tabs__content" ng-if="tab.selected">',
      	        '<div ng-transclude></div>',
            '</div>'
            // will go inside of <tab label="Tab 1">
		].join(''),
		link: function ($scope, $element, $attrs, $ctrl) {
			$scope.tab = {
				label: $scope.label,
				selected: false
			};
			$ctrl.addTab($scope.tab);
			// $ctrl is the 4th argument, given because we use 'require'
		}
	}
}

angular
	.module('app')
	.directive('tab', Tab);
```

and 
```js
function Tabs() {
	return {
		restrict: 'E',
		scope: {},
		transclude: true,
		controller: function () {
			this.tabs = [];

			this.addTab = function addTab(tab) {
				this.tabs.push(tab);
			};
			
			this.selectTab = function selectTab(index) {
				for (var i = 0; i < this.tabs.length; i++) {
					this.tabs[i].selected = false;
				}
				this.tabs[index].selected = true;
			};
		},
		controllerAs: 'tabs',
		link: function ($scope, $element, $attrs, $ctrl) {
			$ctrl.selectTab($attrs.active || 0);
		},
		template: [
      	'<div class="tabs">',
        	'<ul class="tabs__list">',
          	    '<li ng-repeat="tab in tabs.tabs">',
            	    '<a href="" ng-bind="tab.label" ng-click="tabs.selectTab($index);"></a>',
                '</li>',
            '</ul>',
        	'<div class="tabs__content" ng-transclude></div>',
        '</div>'
		].join('')
	};
}

angular
	.module('app')
	.directive('tabs', Tabs);
```

In the view
```html
<div ng-app="app" class="app">
    <tabs>
        <tab label="Tab 1">
            Tab 1 contents!
        </tab>
        <tab label="Tab 2">
            Tab 2 contents!
        </tab>
        <tab label="Tab 3">
            Tab 3 contents!
        </tab>
    </tabs>
</div>
```

# Using the compile/link functions

Each directive has a lifecycle. Up until now we've only been using one part of the lifecycle - the controller. The controller is initiated and ran just before the directive is about to be mounted into the DOM. This is so we can manipulate any values that we need in time for the rendering.

However, it might come to the point where we need to actually do raw DOM manipulation on the directive itself. For instance, we might have a jQuery plugin that straps into a DOM element - we'd need the actual DOM element in order to initiate it. One problem - the controller is initiated *before* the directive is in the DOM. What do we do?


### `link`

This is where the `link` function comes in. If we specify this, **we get a function executed *after* the directive has been mounted in the DOM**. We also then get the DOM element passed through to us as the second parameter.

```js
function someDirective() {
  return {
    template: [
	  '<div>',
	    'Hello!',
	  '</div>'
	].join(''),
    link: function ($scope, $element, $attrs) {

    }
  };
}

angular
  .module('app', [])
  .directive('someDirective', someDirective);
```

You can see above that we get three parameters (they must be in that order!). `$scope` - much like what we can inject into our controllers. `$element`, our DOM mounted element, and `$attrs`, an object of all the attributes used when the directive is initiated.

### `compile`

Compile allows us to manipulate the element before it is inserted into the DOM. This runs in between the `controller` and the `link` function. This gives us access to the unmounted DOM node, and the attributes.

```js
function someDirective() {
  return {
    template: [
      '<div>',
        'Hello!',
      '</div>'
    ].join(''),
    compile: function ($element, $attrs) {

    }
  };
}

angular
  .module('app', [])
  .directive('someDirective', someDirective);
```

In our compile function, we'd then return an object with `pre` and `post` values. Both of these are functions.

These are `pre-link` and `post-link` functions, giving us access to every single point in the directive lifecycle.

Take a look at this diagram of the lifecycle:

![Image](https://camo.githubusercontent.com/fe421dba43140e49c1f36b6bb247322f64928918/687474703a2f2f692e737461636b2e696d6775722e636f6d2f58524473362e706e67)

This means that if we put some `console.log` calls in our compile function, as so:

```js
function someDirective() {
  return {
    template: [
      '<div>',
        'Hello!',
      '</div>'
    ].join(''),
    controller: function () {
        console.log('controller');
    },
    compile: function ($element, $attrs) {
        console.log('compile');

        return {
            pre: function (scope, element, attrs) {
                console.log('pre-link');
            },
            post: function (scope, element, attrs) {
                console.log('post-link');
            }
        }
    }
  };
}

angular
  .module('app', [])
  .directive('someDirective', someDirective);
```

We would get this printed out in the console:

```js
compile
controller
pre-link
post-link
```

What are all of these stages?

- `compile` - ready to compile the directive
- `controller` - manipulate all data **before** the directive is actually compiled
- `pre-link` - the directive is **compiled** to DOM nodes, but isn't inserted into the DOM
- `post-link` - the directive has been **inserted into the DOM** (**same as the link function**)

Generally, we should be using the pre-link (compile) function to do any DOM manipulation - moving nodes, changing HTML/styles etc.

We'd want to use the post-link (link) function to add event listeners.

This gives us full control over what we want to do with our directives.

Example:
```js
function SomeDirective() {
	return {
		template: [
			'<div>',
				'Replace this text!',
			'</div>'
		].join(''),
		compile: function (elem, attrs) {
			return {
				pre: function (scope, element, attrs) {
					console.log(element);
					element[0].innerText = "My Text";
				},
				post: function (scope, element, attrs) {
					console.log(element);
					element[0].addEventListener('click', function(){
						alert('Yo');
					});
				}
			}
		}
	}
}

angular
	.module('app')
	.directive('someDirective', SomeDirective);
```

# Using the link function for DOM manipulation
## Native Events

Now that we've got access to the actual DOM nodes, we can do our own, manual DOM events on the elements. Whilst generally we'd use `ng-click` and let Angular do the dirty work for us, we can do it ourselves manually if we are using 3rd-party plugins that aren't compatible with Angular.

Let's take a simple directive:

```js
function SomeDirective() {
	return {
		template: [
			'<div>',
				'<span>Click on me!</span>',
			'</div>'
		].join(''),
		link: function (scope, elem, attrs) {

		}
	}
}

angular
	.module('app')
	.directive('someDirective', SomeDirective);
```

Now it's important to note that `elem` isn't *actually* the raw DOM node. It is a jqLite (a light version of jQuery) (or jQuery if you have loaded jQuery before Angular) element. However, we can access the raw DOM node via `elem[0]`.

Let's add a click event to our `<span />`.

```js
function SomeDirective() {
	return {
		template: [
			'<div>',
				'<span>Click on me!</span>',
			'</div>'
		].join(''),
		link: function (scope, elem, attrs) {
			var actualElement = elem[0];

			var spanElement = actualElement.querySelector('span');

			spanElement.addEventListener('click', function () {
				alert('You clicked me!');
			});
		}
	}
}

angular
	.module('app')
	.directive('someDirective', SomeDirective);
```

We're adding a DOM event to the actual DOM element rather than using jQuery/jqLite. This is because the API for them slightly differ, and as we can't guarantee what would be loaded on the page, we'll use native JavaScript events instead.

Here, we will get an alert showing when the user clicks on the span. Awesome! Now, say that we want to actually update the `scope` values when the user clicks on the span - how do we do this? First of all, let's put a scope value in our view and controller:

```js
function SomeDirective() {
	return {
		template: [
			'<div>',
				'<span>Click on me!</span>',
				'{{ status }}',
			'</div>'
		].join(''),
		controller: function ($scope) {
			$scope.status = 'Not clicked!';
		},
		link: function (scope, elem, attrs) {
			var actualElement = elem[0];

			var spanElement = actualElement.querySelector('span');

			spanElement.addEventListener('click', function () {
				scope.status = 'Clicked!';
			});
		}
	}
}

angular
	.module('app')
	.directive('someDirective', SomeDirective);
```

Now you can see that we're updating `scope` in our link function. However, this won't actually work. We're outside the scope of Angular here, so Angular isn't able to tell that we've updated our scope.

However, we can manually push Angular to update, by using `scope.$apply()`. Don't worry about this magic, we'll go into detail with this soon.

```js
function SomeDirective() {
	return {
		template: [
			'<div>',
				'<span>Click on me!</span>',
				'{{ status }}',
			'</div>'
		].join(''),
		controller: function ($scope) {
			$scope.status = 'Not clicked!';
		},
		link: function (scope, elem, attrs) {
			var actualElement = elem[0];

			var spanElement = actualElement.querySelector('span');

			spanElement.addEventListener('click', function () {
				scope.status = 'Clicked!';

				scope.$apply();
			});
		}
	}
}

angular
	.module('app')
	.directive('someDirective', SomeDirective);
```

Sorted! This will update our `scope` with the new value. This is also effectively how `ng-click` works, which is why we use them instead of doing all of our DOM events in the link function!

## Update the controller

One problem - we don't *really* use `$scope` anymore - we use controller values. Well, much like when we required the parent controller in our previous README, we can actually request our own directives controller for use in the link function.

To do this, we add `require` with the value `someDirective`. Before, we used `^nameOfDirective` to get the parent's directive. Notice how we aren't using a `^` anymore - we are no longer looking upwards to the parents for a controller - instead, we're asking for the controller of the directive (the `someDirective` part).

```js
function SomeDirective() {
	return {
		template: [
			'<div>',
				'<span>Click on me!</span>',
				'{{ some.status }}',
			'</div>'
		].join(''),
		require: 'someDirective',
		controller: function () {
			$scope.status = 'Not clicked!';
		},
		link: function (scope, elem, attrs, ctrl) {
			var actualElement = elem[0];

			var spanElement = actualElement.querySelector('span');

			spanElement.addEventListener('click', function () {
				// ctrl.status = undefined;
				ctrl.status = 'Clicked!';

				scope.$apply();
			});
		}
	}
}

angular
	.module('app')
	.directive('someDirective', SomeDirective);
```

Have a look at the minor changes we've made - we've now got that fourth argument in our link function too, and we're updating `ctrl.status` in our event.

However, our status value in our controller is still on our `scope`. We need to change this over to the controller, using `controllerAs`. We can then attach the value to `this` instead of the scope.

```js
function SomeDirective() {
	return {
		template: [
			'<div>',
				'<span>Click on me!</span>',
				'{{ some.status }}',
			'</div>'
		].join(''),
		require: 'someDirective',
		controller: function () {
			this.status = 'Not clicked!';
		},
		controllerAs: 'some',
		link: function (scope, elem, attrs, ctrl) {
			var actualElement = elem[0];

			var spanElement = actualElement.querySelector('span');

			spanElement.addEventListener('click', function () {
				ctrl.status = 'Clicked!';

				scope.$apply();
			});
		}
	}
}

angular
	.module('app')
	.directive('someDirective', SomeDirective);
```


We're still using `scope.$apply()` though - why? We still use it because `$apply()` is a function only available on scope, and we still need to tell Angular that we've updated our view.


# $digest cycle

So far, we've been updating our $scope object and our controller and the changes get reflected in the view. This is awesome, but how is it actually done?

In comes the digest cycle! The digest cycle is a cycle that checks all of our values and fires callbacks if there are changes.

When we put an expression in the view (such as `{{ ctrl.name }}`), Angular creates a "watcher". This watcher then goes into an array in `$scope.$$watchers`. This watcher has a function that returns the latest value of `ctrl.name`, and a callback to update the view with the latest `ctrl.name` value.

When we run the digest cycle, we loop through all of our watchers and run the functions. The function runs, returns `ctrl.name` and checks it against its last known value. If the value is different, the callback fires, updating the view with the latest value of `ctrl.name`.

These watchers are scoped to our `$scope` object, meaning that if we're updating values in our scope, we don't have to update **all** the scopes that exist in our Angular application. For instance, if we're just updating values inside a directive, we only need to run the digest cycle inside that directive - no need to go outside of it.

There are two ways to trigger the $digest cycle - `$scope.$digest()` and `$scope.$apply()`.

### $digest()

`$scope.$digest()` runs the digest cycle on the given `$scope` object, and goes down all the children scopes. This is as far as the cycle goes - it doesn't go upwards, only downwards. If we went upwards, we'd go up scopes until we reached the root scope.

### $apply()

`$apply()` is the same as `$digest()` - except from the fact it runs `$digest` from our `$rootScope`. This means whilst `$apply()` does only go downwards, much like `$digest()`, it goes downwards from the `$rootScope`, meaning **all** of our watchers are checked and updated. This means any nested controllers will have their digest cycle ran.

## Manual digest

The reason why we have to call `$scope.$apply()` when we update values in our event listener is because Angular doesn't know that we've updated the scope. How does it know when we use `ng-click`, etc? Angular actually runs `$scope.$apply()` itself after the click event that `ng-click` provides us. This means that we're basically doing the same as Angular does when we run `$scope.$apply()` in our events.

## Transclusion

Say we want to be able to customize the content inside of our directives, like so:

```html
<our-directive>
	Content here! We want to put custom content in our directive!
</our-directive>
```

Up until now, any content *inside* the directive would be replaced by our template. However, we can change that and actually put the content into our template, and also control where we want to put it - awesome!

To do this, we add a property named `transclude` to our directive. We will set this to `true` for now. This lets us use the `ng-transclude` directive.

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div class="ourDirective">',
        'The content of our directive is:',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

We can then use the directive `ng-transclude` to put our content wherever we want it in our template.

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div class="ourDirective">',
        'The content of our directive is: <span ng-transclude></span>',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

It's as simple as that! When Angular runs, we will end up with this rendered in the HTML:

```html
<our-directive>
	<div class="ourDirective">
		The content of our directive is: <span>Content here! We want to put custom content in our directive!</span>
	</div>
</our-directive>
```

# Manual and isolate transclusion with transclude()

We can also use the fifth function provided in our `link` function - `transclude`. This function returns our transcluded content as an actual DOM element. This allows us to manually append our elements into our directives instead.

We might want to use this when we want to transform the transcluded elements depending on attributes. For instance, we could remove a `<button>` if the attribute disabled is present.

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div class="ourDirective">',
        'The content of our directive is: <span></span>',
      '</div>'
    ].join(''),
    link: function (scope, element, attrs, ctrl, transclude) {
        // transclude() = DOM elements
    }
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

Now that we've got the transcluded elements as actual DOM elements and also our whole directive element (the `element` variable), we can insert our transcluded content wherever we want. If we want to put it into the span, we can do this:

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div class="ourDirective">',
        'The content of our directive is: <span></span>',
      '</div>'
    ].join(''),
    link: function (scope, element, attrs, ctrl, transclude) {
        element.find('span').after(transclude());
    }
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

Awesome! This puts our transcluded content inside the `<span />`.

# Multi-slot transclusion transclude: {}

Instead of a string or a boolean value, to do multi-slot transclusion, we pass through an object.

We might use multi-slot transclusion when we want to move certain elements into different positions in our directives templates, instead of just putting them all in one place. We might want to wrap an image with a link or a user profile with an image.

The properties on this object are what we want to name our slots. For instance, if we've got this setup for our directive:

```html
<user-profile>
    <h4>Tim Cook</h4>
    <h6>CEO, Apple</h6>
</user-profile>
```

You can see here that our `<h4>` element is the name and our `<h6>` is the position. Therefore, it makes sense to name our slots `name` and `position`.

We then put the values of our properties to be the element that we're targeting. We'd end up with something like this:

```js
function UserProfile() {
  return {
    transclude: {
        name: 'h4',
        position: 'h6'
    },
    template: [
      '<div class="user">',
        '<h2>User Profile</h2>',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('userProfile', UserProfile);
```

We can now access these elements using the familiar `ng-transclude` directive. We pass in the slot name that we want as the value.

```js
function UserProfile() {
  return {
    transclude: {
        name: 'h4',
        position: 'h6'
    },
    template: [
      '<div class="user">',
        '<h2>User Profile</h2>',
        '<div>Name: <span ng-transclude="name"></span></div>',
        '<div>Position: <span ng-transclude="position"></span></div>',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('userProfile', UserProfile);
```

You can see how we can put our slots anywhere we like in our directive. Also, we don't have to match the tags that we transclude - you can see that although we've picked out `<h4>` and `<h6>` we're transcluding them inside of a `<span />` element (this does put our header elements *inside* our span element, not just the text).

## Optional slots

Now, if you remove either the `<h4>` or `<h6>`, you will get an error as we're expecting there to be both of them.

We can mark slots as optional, too. Let's make position optional, as everyone has a name but people might not have a position. To make a slot as optional, inside of our string we add a `?` before the element.

```js
function UserProfile() {
  return {
    transclude: {
        name: 'h4',
        position: '?h6'
    },
    template: [
      '<div class="user">',
        '<h2>User Profile</h2>',
        '<div>Name: <span ng-transclude="name"></span></div>',
        '<div>Position: <span ng-transclude="position">No position</span></div>',
      '</div>'
    ].join('')
  };
}

angular
  .module('app', [])
  .directive('userProfile', UserProfile);
```

Now we use our directive with and without specifying a `<h6>` element. If there isn't a `<h6>` element, the contents of our `<span ng-transclude="position">` will be displayed instead, meaning we can gracefully show different content if there is no position specified.

# jqLite events

jqLite allows us to use `.on` and `.off` on our `element` inside the link function. `.off()` will remove all event listeners that we've added to the element, and `.on` let's us add them for different event types, such as `click`.

If we don't unbind our events, we may suffer with issues later down the line as our element will no longer exist but our event callbacks may still be fired. If we're updating our element inside of our callback, we will get errors because the element no longer exists.

Let's add a click event to our element:

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div>',
        'Click on me!',
      '</div>'
    ].join(''),
    link: function (scope, element) {
        element.on('click', function () {
            alert('You clicked me!');
        });
    }
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

Awesome! Now we can add native DOM events to our element. Here we can also target `window`, and `document`, etc, as we might have to change our directives behaviour when the browser resizes or when the user scrolls the page. But how do we know when to unbind these events?

## $destroy

Luckily, we get an event fired when our directive is *about* to be unmounted from the DOM. We can subscribe to this event using `scope.$on`.

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div>',
        'Click on me!',
      '</div>'
    ].join(''),
    link: function (scope, element) {
        scope.$on('$destroy', function () {
           alert('About to be destroyed!');
        });
    }
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

This will alert us when our directive is about to be removed from the DOM. Now, we can unsubscribe from these events. Luckily, as explained earlier, we can use `.off()`!

```js
function ourDirective() {
  return {
    transclude: true,
    template: [
      '<div>',
        'Click on me!',
      '</div>'
    ].join(''),
    link: function (scope, element) {
        element.on('click', function () {
           alert('You clicked me!');
        });

        scope.$on('$destroy', function () {
		   element.off();
		});
    }
  };
}

angular
  .module('app', [])
  .directive('ourDirective', ourDirective);
```

Sorted! We've now created new events and removed the listeners when our directive gets destroyed.

#### Another example
```js
function Counter() {
	return {
		template: [
			'<div>',
				'<h3>Counter</h3>',
				'<div>Click anywhere to increment the counter!</div>',
				'<div>Current count: {{ ctrl.count }}</div>',
			'</div>'
		].join(''),
		controller: function ($scope) {
			this.count = 0;
		},
		require: 'counter', // gives us ctrl in the link function
		controllerAs: 'ctrl', // use this and ctrl.count
		link: function(scope, element, attrs, ctrl){
			element.on('click', function(){
				ctrl.count++;
				scope.$apply(); // we're outside of the controller scope, we need to remind it
			});

			scope.$on('$destroy', function(){
				element.off();
			});			
		}
	}
}

angular
	.module('app')
	.directive('counter', Counter);
	
// this could also be written without controllerAs	
	
function Counter() {
    return {
        template: [
            '<div class="counter">',
                '<h3>Counter</h3>',
                '<div>Click anywhere to increment the counter!</div>',
                '<div>Current count: {{ count }}</div>',
            '</div>'
        ].join(''),
        controller: function ($scope) {
            $scope.count = 0;
        },
        link: function (scope, element) {
            element.on('click', function () {
                scope.count++;
                scope.$apply();
            });
 
            scope.$on('$destroy', function () {
                element.off();
            });
        }
    }
}
 
angular
    .module('app')
    .directive('counter', Counter);	
```

# Testing custom directives

We already know how to use protractor to test our HTML output, so the explanation on how to test directives is very similar.

Our protractor setup currently runs a local webserver so we have a web page to test in our tests - this is the `index.html` that we've used before (you can see an example in this repo). Here we include all of our directives etc, and we use them like we would inside a normal application. This allows protractor to use the directive like a normal user would.

Inside this repo, we've got a counter directive that increments when we click on the directive.

```js
function Counter() {
	return {
		template: [
			'<div class="counter">',
				'<h3>Counter</h3>',
				'<div>Click anywhere to increment the counter!</div>',
				'<div class="counter__count">Current count: {{ count }}</div>',
			'</div>'
		].join(''),
		controller: function ($scope) {
			$scope.count = 0;
		},
		link: function (scope, element) {
			element.on('click', function () {
				scope.count++;

				scope.$apply();
			});

			scope.$on('$destroy', function () {
				element.off();
			});
		}
	}
}

angular
	.module('app')
	.directive('counter', Counter);
```

Let's test this that our directive is functioning properly.

Inside our `index.html`, we have this:

```html
<counter></counter>
```

This initializes and puts our counter directive on the page.

Now, in our `Index.spec.js` file inside `spec/`, we can grab the page.

```js
describe('Directive Test', function() {
	browser.get('http://localhost:8080');
});
```

Now let's grab our counter directive - this has the class `counter`. Let's also grab the current count.

```js
describe('Directive Test', function() {
	browser.get('http://localhost:8080');

	var counter = element(by.css('.counter'));
	var count = element(by.css('.counter__count'));
});
```

Now we can test that the counter displays an initial 0 count by grabbing the innerHTML.

```js
describe('Directive Test', function() {
	browser.get('http://localhost:8080');

	var counter = element(by.css('.counter'));
	var count = element(by.css('.counter__count'));

	it('should have an initial 0 count', function () {
		expect(count.getInnerHtml()).toEqual('Current count: 0');
	});
});
```

Awesome! Now, let's click on the counter and check that it increments the counter correctly.

```js
describe('Directive Test', function() {
	browser.get('http://localhost:8080');

	var counter = element(by.css('.counter'));
	var count = element(by.css('.counter__count'));

	it('should have an initial 0 count', function () {
		expect(count.getInnerHtml()).toEqual('Current count: 0');
	});

	it('should increment when we click on it', function () {
		counter.click();

		expect(count.getInnerHtml()).toEqual('Current count: 1');
	});

});
```

Sorted - now our directive is tested, and is working perfectly!

Another test example
```js
describe('UserProfile test', function(){
	browser.get('http://localhost:8080');

	var directive = element.all(by.css('.user')).get(0);

	it('should display the right info', function(){
		expect(directive.getText()).toContain('Name');
		expect(directive.getText()).toContain('Position');
		expect(directive.getText()).toContain('Description');
		expect(directive.getText()).toContain('Bill Gates');
	})
})
```

# Bonus: Using the component() method


We use components every day - be it a dropdown box, a login form or a navigation bar. Components are awesome - much like directives, they're reusable, isolated pieces of functionality that we can use again and again. Other frameworks provide similar abilities - in fact the whole of React is based off of components - nothing else!

Instead of passing through a function to our `component` method (like what we do with the `directive` method), we pass through an object instead. This is really similar to the object we return in our directives.

For example:

```js
function Counter() {
	return {
		template: [
			'<div ng-click="counter.increment()" class="counter">',
				'<h3>Counter</h3>',
				'<div>Click anywhere to increment the counter!</div>',
				'<div class="counter__count">Current count: {{ counter.count }}</div>',
			'</div>'
		].join(''),
		controller: function ($scope) {
			this.count = 0;

			this.increment = function () {
				this.count++;
			};
		},
		controllerAs: 'counter'
	}
}

angular
	.module('app')
	.directive('counter', Counter);
```

Would turn into this:

```js
var Counter =  {
	template: [
	    '<div ng-click="counter.increment()" class="counter">',
	        '<h3>Counter</h3>',
	        '<div>Click anywhere to increment the counter!</div>',
	        '<div class="counter__count">Current count: {{ counter.count }}</div>',
	    '</div>'
	].join(''),
	controller: function ($scope) {
	    this.count = 0;

	    this.increment = function () {
	        this.count++;
	    };
	},
	controllerAs: 'counter'
};

angular
	.module('app')
	.component('counter', Counter);
```

Pretty much the same thing! However, there are a few restrictions to using the `.component()` method:

- Every item is an element - we can't create attributes
- We no longer use the `scope` property. Everything is bound to the controller
- We no longer use `bindToController` - this is simply named `bindings` instead
- When we use `require`, we have to pass through an object instead of a string, with the property being anything that we want and the string being what we'd normally use
    - For example, instead of `{ require: '^parentController' }`, we use `{ require: { parent: '^parentController' } }`
- We cannot use a `link` or `compile` function

Then why even use them? Well, directives are old and a bit verbose for what we may need 99% of the time. Components are a new, updated method that has matched the way the frontend has changed. Think of them as a simple way to write a directive, and if you need to go complicated, use a directive instead.

#### Another example

```js
var ContactCard = {
	bindings: {
		name: '=',
		email: '=',
		phone: '='
	},
	template: [
		'<div>',
			'<h4>Contact Card</h4>',
			'<label>Name:</label>',
			'{{ ctrl.name }}',
			'<label>Email:</label>',
			'{{ ctrl.email }}',
			'<label>Phone:</label>',
			'{{ ctrl.phone }}',
		'</div>'
	].join(''),
	controllerAs: 'ctrl',
	restrict: 'E'
};


angular
	.module('app')
	.component('contactCard', ContactCard);
```

Instead of
```js
function ContactCard() {
	return {
		scope: {
			name: '=',
			email: '=',
			phone: '='
		},
		template: [
			'<div>',
				'<h4>Contact Card</h4>',
				'<label>Name:</label>',
				'{{ name }}',
				'<label>Email:</label>',
				'{{ email }}',
				'<label>Phone:</label>',
				'{{ phone }}',
			'</div>'
		].join(''),
		restrict: 'E'
	};
}

angular
	.module('app')
	.directive('contactCard', ContactCard);
```

# Custom Filters

Custom filters come in two types - single value filters and dataset filters. We can apply a custom filter to filter an array in an `ng-repeat`, or we can apply a filter to an expression to format the expression differently. Both of these are declared via the `.filter` method.

```js
function MyCustomFilter() {
	// wooo!
}

angular
	.module('app')
	.filter('myCustomFilter', MyCustomFilter);
```

Looks familiar, yes?

Our custom filters should return a function that will then process the data passed to it. Let's create a filter to make our expression uppercase.

## Single value filters

When we return a function in our filter, as such:

```js
function MyCustomFilter() {
	return function (str) {

	};
}

angular
	.module('app')
	.filter('myCustomFilter', MyCustomFilter);
```

We get the expression's value passed through to the function. Anything we then returned from our returned function will be put in place of the expression. We could return the string `'hello'` but that wouldn't be any use to anyone.

Let's return the `str` variable, in uppercase.

```js
function makeUppercase() {
	return function (str) {
		return str.toUpperCase();
	};
}

angular
	.module('app')
	.filter('makeUppercase', makeUppercase);
```

Awesome! We can now use this like any other filter in Angular.

```html
<div>
	{{ 'My String' | makeUppercase }}

	{{ ctrl.variable | makeUppercase }}
</div>
```

Which will result in:

```html
<div>
	MY STRING

	OTHER STRING <!-- ctrl.variable = 'other string' -->
</div>
```

## Arguments

We can also pass arguments through to our custom filters. Much like what we've done with the `date` filter before, we can pass through as many arguments we like to the filter, and they're then the 2nd, 3rd, etc, argument passed through to our function.

We can add a toggle to our `makeUppercase` filter on whether or not to *actually* make the text uppercase.

```html
<div>
	{{ 'My String' | makeUppercase:true }}

	{{ ctrl.variable | makeUppercase:false }}
</div>
```

We can then receive this argument in our function, and not make it uppercase if it's false.

```js
function makeUppercase() {
	return function (str, active) {
		return active ? str.toUpperCase() : str;
	};
}

angular
	.module('app')
	.filter('makeUppercase', makeUppercase);
```

As the `true` or `false` can also point to a variable's value instead (`{{ 'My String' | makeUppercase:variableName }}`), we can turn our filters on and off based on different variables. For instance, for administrators, we might want their name to be uppercase, but all other members just leave their names the same.

Awesome!

## Filters for datasets

If we apply this filter to a data-set (for instance on an `ng-repeat`), we simply get passed the array instead of a string expression.

Assume that we have this:

```html
<ul>
	<li ng-repeat="album in ctrl.albums | startsWithLetter:'a'">
	</li>
</ul>
```

This is calling a custom filter named `startsWithLetter`, passing through `'a'` as an argument. We can then define our custom filter as follows:

```js
function startsWithLetter() {
	return function (items, letter) {
		// items = ctrl.albums (an array of albums)
		// letter = 'a'
	};
}

angular
	.module('app')
	.filter('startsWithLetter', startsWithLetter);
```

Now we can filter through the array like we would in native JavaScript:

```js
function startsWithLetter() {
	return function (items, letter) {
		// items = ctrl.albums (an array of albums)
		// letter = 'a'

		return items.filter(function (item) {
			return item.name[0] === letter;
		});
	};
}

angular
	.module('app')
	.filter('startsWithLetter', startsWithLetter);
```

This will filter out our array, only returning items where the `name` property begins with the letter `a`. The array you return from this function will be all the elements that are displayed in the rendered `ng-repeat`.


Examples
```js
function UpperFirstLetter() {
	return function (str) {
		return str[0].toUpperCase() + str.slice(1);
	}
}

angular
	.module('app')
	.filter('upperFirstLetter', UpperFirstLetter);
```

and 
```js
function City(){
	return function(contacts, city){
		return contacts.filter(function(contact){
			return contact.location.city === city;
		});
	};
}

angular
	.module('app')
	.filter('city', City);
```

and
function removeAllVowels() {
	return function (str) {
		return str.replace(/[aeiou]/gi, '');
	};
}

angular
	.module('app')
	.filter('removeAllVowels', removeAllVowels);

## Testing filters

Like our services, we can inject filters into our tests. We use the `$filter` helper.

As our filters do not care explicitly what *type* of data is given to them, we don't need to load them up in Protractor and test them in the actual application. We can simply inject them into our karma tests and test the functionality out of them with any data!

Let's say we've got this filter:

```js
function firstUppercase() {
	return function (str) {
		return str.charAt(0).toUpperCase() + str.slice(1);
	};
}

angular
	.module('app')
	.filter('firstUppercase', firstUppercase);
```

We can inject this using `$filter` in our tests:

```js
describe('UserService', function () {
	var $controller, firstUppercase;

	beforeEach(module('app'));

	beforeEach(inject(function ($filter) {
		firstUppercase = $filter('firstUppercase');
	}));
});
```

Now, as we returned a function in our filter, we can simply call `firstUppercase` as a function and receive our manipulated value in return.

```js
describe('UserService', function () {
	var $controller, firstUppercase;

	beforeEach(module('app'));

	beforeEach(inject(function ($filter) {
		firstUppercase = $filter('firstUppercase');
	}));

	it('should capitalise the first letter', function () {
		expect(firstUppercase('test')).toEqual('Test');
	});
});
```

Nice - our tests now pass! You can pass through any data you like, meaning we can also test any filters that we create on datasets.

```js
describe('removeAllVowels Filter', function () {
	var $controller;

	beforeEach(module('app'));

	beforeEach(inject(function ($injector) {
		$filter = $injector.get('$filter');

		removeAllVowels = $filter('removeAllVowels');
	}));

	it('should remove all vowels', function(){
		expect(removeAllVowels('Biscuit')).toEqual('Bsct');
	});

});
```
and for testing list filter
```js
describe('Favorite Food Filter', function () {
	var $controller;

	beforeEach(module('app'));

	beforeEach(inject(function ($injector) {
		$filter = $injector.get('$filter');

	}));

	it('should choose filter on favorite food correctly', function(){
		var mockedList = [
			{favoriteFood: 'bread'},
			{favoriteFood: 'milk'}
		];

		var results = $filter('favoriteFood')(mockedList, 'milk')

		expect(results.length).toBe(1);
		expect(results[0].favoriteFood).toBe('milk');
	})
	
});
```

# The event system: Publishing events

All events can be published on our `$scope` or `$rootScope` objects. Why do we use events? Well, communication between controllers in two different aspects of the application can become quite hard - how can our controllers notify each other of updates? Or imagine if we receive data in a service and that data gets updated - how can we notify the controllers that there is new data to consume. This is where events come in! 

Angular offers us two ways of publishing events - either up or down. Up will go all the way from the current scope to our root scope, and down will go down from our current scope into it's children scopes, and all it's children's scopes, and so on and so forth.

Child scopes are a bit tricky to understand - but don't worry, they're really simple! Let's imagine where we start our app - `ng-app`. This is our `$rootScope`. Then, we use `ng-controller` or a directive inside `ng-app`. This will create another scope, inside of our root scope. Then, if we were to use a directive inside of them, we'd get a child scope inside their scope. Whenever we use a directive (`ng-controller`, `ng-repeat`, custom directives etc) that create their own scope, they're made in their parents scopes.

To publish events downwards, we use `$scope.$broadcast`. To publish event upwards, we use `$scope.$emit`.

The first argument we pass through to these functions is the name of the event. This is what we would then specify when we want to listen for the event. We could have a message being sent and then received, so we'd generally namespace these into `message` and then the action - such as `message:sent` and `message:received`.

The second argument we pass through is data. This can then be picked up by the subscriber. For instance, we might want to publish an event when the user sends a message - we can send the message data through with the event too, and subscribe to it in a directive that then displays the message.

Examples of this are:

```js
$scope.$emit('eventName'); // passing through data is optional

$scope.$emit('anotherEvent', { obj: 'hello!' });

$scope.$broadcast('aDifferentEvent', 3949324); // we can pass through any data
```

## Subscribing to events

We can then use a function named `$on` to subscribe to these events. We pass through a callback too, which retrieves the data (if there is any) too.

We can subscribe to the events above like so:

```
$scope.$on('eventName', function () {
	// no data passed through
});

$scope.$on('anotherEvent', function (event, data) {
	// data = { obj: 'hello' }
});

$scope.$on('aDifferentEvent', function (event, data) {
	// data = 3949324
});
```

Simple!

## $rootScope

We can also broadcast events on the `$rootScope` - after all it is a scope! As all the children scopes are *eventual* children of the root scope, we will use `$broadcast` as this goes down the scopes.

Publishing and subscribing to events on the `$rootScope` is generally preferred - most of the time there is no advantage to only publishing events upwards/downwards from the current scope so by using events on the root scope, we can guarantee everyone will receive the event we are broadcasting - every scope will get notified of the event.

```js
$rootScope.$emit('eventName');
$rootScope.$broadcast('aDifferentEvent', 3949324);

$rootScope.$on('eventName', function () {
	// awesome!
});
$rootScope.$on('aDifferentEvent', function (event, data) {
	// awesome!
});
```

## Unsubscribing from an event

One awesome thing that Angular does when we subscribe to an event is provide us a really easy way to unsubscribe from it. Angular will automatically unsubscribe all the event subscribers on our `$scope` object (that's how we can use `$scope.$on` to listen for `$destroy`), but it can't unsubscribe from our subscribers on the `$rootScope`.

`$scope.$on` returns a closure function that we can actually call to unsubscribe it!

```js
var unbind = $rootScope.$on('eventName', function () {
	// awesome!
});

// unbind === func() {}
```

We can then call `unbind()`, and this will unsubscribe the event!

We could then hook this into our `$scope.$on('destroy')` function call (the one that gets emitted when our directive is about to be removed):

```js
var unbind = $rootScope.$on('eventName', function () {
	// awesome!
});

$scope.$on('$destroy', unbind);
```

Example
```js
function ContactController($rootScope, $scope) {

    var ctrl = this;

    var removeListener = $rootScope.$on('remove', function(event, data){
        ctrl.contacts.splice(data, 1);
    })

    $scope.$on('remove', removeListener);

    ctrl.contacts = [
    // data goes here
    ];
}

angular
    .module('app')
    .controller('ContactController', ContactController);    
```


And in our directive
```js
function Contact() {
	return {
		restrict: 'E',
		template: [
			'<div class="contact">',
				'Name: {{ ctrl.contact.name.title }} {{ ctrl.contact.name.first }} {{ ctrl.contact.name.last }} - <a href="" ng-click="ctrl.remove(ctrl.id)">Remove</a>',
			'</div>'
		].join(''),
		controller: function ($rootScope) {
			this.remove = function (id) {
				$rootScope.$broadcast('remove', id);
			};

		},
		controllerAs: 'ctrl',
		bindToController: {
			id: '=',
			contact: '='
		}
	}
}

angular
	.module('app')
	.directive('contact', Contact);
```

and HTML
```html
<div ng-app="app" class="app">
    <div ng-controller="ContactController as ctrl">
        <ul>
            <li ng-repeat="contact in ctrl.contacts">
                <contact id="$index" contact="contact"></contact>
            </li>
        </ul>
    </div>
</div>
```
Since the event is unsubscribed we can only click once.

# Built-in form validation methods

We're already two-way binding our input values to our controller via `ng-model`, but Angular allows us to take our form integration much, much further.

When we assign a `name` to our form and input elements, Angular begins its magic and gives us access to a lot of useful tools to validate the user input. Why do we validate? So we don't get incorrect data! Whilst we would still validate the data on the server, we can save the user time (and server resources) by validating on the client first. Imagine if we could signup to Facebook with just numbers in our name - it wouldn't make any sense. Angular makes it easy for us to prevent the user from making these types of requests. 

Let's take this example form:

```html
<form>
	<input ng-model="ctrl.username" />
	<input ng-model="ctrl.password" />
</form>
```

And add name elements to our `<form>` and `<input />`s.

```html
<form name="form">
	<input
		name="username"
		ng-model="ctrl.username" />
	<input
        name="password"
        ng-model="ctrl.password" />
</form>
```

We now get quite an awesome object added to our `$scope`:

```js
$scope.form = {
	username: {
		$untouched: true,
		$touched: false,
		$pristine: true,
		$dirty: false,
		$valid: true,
		$invalid: false,
		$error: {}
	},
	password: {
        $untouched: true,
        $touched: false,
        $pristine: true,
        $dirty: false,
        $valid: true,
        $invalid: false,
        $error: {}
    }
};
```

As you can see we get quite a big, detailed object back. What do all of these mean?

- `$untouched` - this is initially `true`, set to `false` when the user goes in and then out of the input
- `$touched` - opposite of `$untouched`
- `$pristine` - this is initially `true`, set to `false` when the user changes the input's value (the user does not have to go out of the input for this to change)
- `$dirty` - opposite of `$pristine`
- `$valid` - if the field's value matches all validation rules applied to it
- `$invalid` - opposite of `$valid`
- `$error` - an object of all errors that the input is currently failing on

Whilst `$pristine` and `$touched` offer us some cool features, the core of the power is in the `$error` and `$valid` items.

By default, inputs in HTML allow us to set validation rules on them - for instance, required and maxlength.

Angular will check all of these, and let us know in our object whether or not the input passes these validation rules - this allows us to show messages if the user hasn't entered the correct information.

If we have this form:

```html
<form name="form">
	<input
		name="username"
		required="required"
		ng-model="ctrl.username" />
</form>
```

We will get this object:

```js
$scope.form = {
	username: {
		$untouched: true,
		$touched: false,
		$pristine: true,
		$dirty: false,
		$valid: false,
		$invalid: true,
		$error: {
			required: true
		}
	}
};
```

You can see here that we have an error in our input - it's required, and not filled in! We can see all the individual errors that the input fails on in `$error`, but also get a general value on whether or not our field is valid by looking at `$valid`.

Let's display the error in the view, if the user exists our input and still leaves it blank. We can do this by combining the `$touched` and `$error.required` values.

```html
<form name="form">
	<input
		name="username"
		required="required"
		ng-model="ctrl.username" />

	<div ng-if="form.username.$touched && form.username.$error.required">
		Username is required!
	</div>
</form>
```

This will display our error if the user goes into our input and then leaves it blank. This is better user experience because it means the error won't immediately be shown when the user loads the page. Simple!

```html
<div ng-app="app" class="app">
    <div ng-controller="FormController as ctrl">
        <form name="form">
            <!-- <pre>{{ form | json }}</pre> -->
            <div>
                Username: 
                <input 
                    type="text"
                    name="username"
                    minlength="3"
                    maxlength="20"
                    required="required"
                    ng-model="ctrl.username"
                />

                <div ng-if="form.username.$touched">
                    <div ng-if="form.username.$error.required">
                        Username is required!
                    </div>
                    <div ng-if="form.username.$error.minlength">
                        Username must be more than 3 characters!
                    </div>
                    <div ng-if="form.username.$error.maxlength">
                        Username must be less than 20 characters!
                    </div>                          
                </div>                                      
            </div>


            <div>
                Password:     
                <input 
                    type="password"
                    name="password"
                    minlength="8"
                    required="required"
                    ng-model="ctrl.password"
                />

                <div ng-if="form.password.$touched">
                    <div ng-if="form.password.$error.minlength">
                        Password must be more than 8 characters!
                    </div>
                    <div ng-if="form.password.$error.required">
                        Password is required!
                    </div>                        
                </div>                    
            </div>

            <div>
                Email:     
                <input 
                    name="email"
                    type="email"
                    required="required"
                    ng-model="ctrl.email"
                />

                <div ng-if="form.email.$touched">
                    <div ng-if="form.email.$error.required">
                        Email is required
                    </div>
                    <div ng-if="form.email.$error.email">
                        Email must be valid
                    </div>                        
                </div>                
            </div>                                       
        </form>
    </div>
</div>
```

# ngMessages

`ngMessages` is a separate module for Angular. so we need to make sure we require the file and module into our main module.

```js
angular
	.module('app', [
		'ngMessages'
	]);
```

And then we're ready to use it!

## What does it do?

`ngMessages` allows us to take an object, and display different messages depending on what properties exist on that object.

This links in with our `$error` object that we had in the previous README. To refresh your memory, the `$error` object may look something like this, for a field named `username`:

```js
{
	username: {
		$error: {
			required: true
		}
	}
}
```

Let's pass the `$error` object into `ngMessages`. As a parent component, we use the `ng-messages` directive.

```html
<form name="form">
	<input
	    name="username"
		ng-model="ctrl.username"
		required="required" />

	<div ng-messages="form.username.$error">
	</div>
</form>
```

Now that we've done that, we can use the directive `ng-message` for each property we want to display errors for. As we've only got the possibility of `required` appearing in our object (as that is the only validation we've defined), we'll have one element:

```html
<form name="form">
	<input
	    name="username"
		ng-model="ctrl.username"
		required="required" />

	<div ng-messages="form.username.$error">
		<div ng-message="required">Username is required!</div>
	</div>
</form>
```

We can use this on different inputs too. For instance, with an email, we get an `email` property too. We can also add a `minlength` validation:

```html
<form name="form">
	<input
	    name="email"
	    type="email"
		ng-model="ctrl.email"
		minlength="2"
		required="required" />

	<div ng-messages="form.email.$error">
	</div>
</form>
```

We'll now have an object that looks like this:

```js
{
	email: {
		$error: {
			required: true,
			minlength: true,
			email: true
		}
	}
}
```

And now we can simply add more DOM elements for each error message:

```html
<form name="form">
	<input
	    name="email"
	    type="email"
		ng-model="ctrl.email"
		minlength="2"
		required="required" />

	<div ng-messages="form.email.$error">
		<div ng-message="required">Email is required!</div>
		<div ng-message="minlength">Must be more than 2 characters!</div>
		<div ng-message="email">Must be a valid email!</div>
	</div>
</form>
```

It's worth noting that only one message will be displayed at a time, in order of the DOM nodes. At first, our `required` message will show, then if we type one letter in our input, the `minlength` message will show. Then when we've typed more letters, the `email` message will appear.

## Only on $touched

We can also then add an `ng-if` to only show the error messages once the user has actually interacted with the input.

```html
<form name="form">
	<input
	    name="email"
	    type="email"
		ng-model="ctrl.email"
		minlength="2"
		required="required" />

	<div ng-messages="form.email.$error" ng-if="form.email.$touched">
		<div ng-message="required">Email is required!</div>
		<div ng-message="minlength">Must be more than 2 characters!</div>
		<div ng-message="email">Must be a valid email!</div>
	</div>
</form>
```

Awesome! Let's compare this to what our previous code would've been:

```html
<div ng-if="form.email.$touched">
    <div ng-if="form.email.$error.required">
        Email is required!
    </div>
    <div ng-if="form.email.$error.minlength">
        Email must be more than 2 characters!
    </div>
    <div ng-if="form.email.$error.email">
        Must be a valid email!
    </div>
</div>
```

You'll see we have cut down a lot of repeated code - also if we were to change the name of our input, we'd only have to change it once with `ngMessages` - 3 times (and maybe many more) without it.

# $parsers and $formatters

We can add parsers and formatters by requiring in the `ngModel` controller in our directive.

This can solve some simple issues and save us processing data down the line - for instance, our model might be minutes, but we might want to display the data as hours and minutes. It saves us processing the data later on in our controllers - the data is simply formatted there and then.

```js
function changeCase() {
	return {
		restrict: 'A',
		require: 'ngModel',
		link: function (scope, element, attrs, ngModel) {

		}
	}
}

angular
	.module('app')
	.directive('changeCase', changeCase);
```

Here we can push functions into two different arrays - `$parsers` and `$formatters`.

### $parsers

Parsers parse incoming data from the `ng-model` directive before saving them to the model. Let's change all values to be stored in lowercase in our model.

```js
function changeCase() {
	return {
		restrict: 'A',
		require: 'ngModel',
		link: function (scope, element, attrs, ngModel) {
			ngModel.$parsers.push(function (str) {
				return str.toLowerCase();
			});
		}
	}
}

angular
	.module('app')
	.directive('changeCase', changeCase);
```

Now, regardless of what case we actually type in inside our input, it'll be saved into the model in lowercase.

### $formatters

Formatters are the opposite of parsers - they format the data from the model into the view. Let's change all of our model values to be displayed in uppercase in our view.

```js
function changeCase() {
	return {
		restrict: 'A',
		require: 'ngModel',
		link: function (scope, element, attrs, ngModel) {
			ngModel.$formatters.push(function (str) {
				return str.toUpperCase();
			});
		}
	}
}

angular
	.module('app')
	.directive('changeCase', changeCase);
```

This will take our model values and display them in uppercase in our field. Combine this with our previous `$parser`, and all our of actual model values will be in lowercase, but displayed in uppercase in our view.

## Using our parsers/formatters

You might have noticed that our directive is restricted to being used as an attribute. This means that we can apply it to **any input that we have `ng-model` attached on** (will error out if not attached directly).

```html
<input ng-model="ctrl.username" change-case />
```

# $validators

Sometimes HTML validators arent enough - for instance, we can't test if data fits to a certain format (like requiring that a string must be 2 characters, 2 numbers and then 2 characters again), or if an input is only numbers.

Let's create a directive to see if our input is *only* numbers. Up until now we've only used directives as elements with templates. However, we're now creating directives as attributes (remember that we can restrict our directives to only be attributes) and not having a tempate - by applying our directive to an element, we're affecting the behaviour of that element - not the contents.

Much like `$parsers` and `$formatters`, we add our custom validators into `$validators`. Here we have a function where we can test if the value is valid, returning true or false depending on their validity.

```js
function integer() {
	return {
		restrict: 'A',
		require: 'ngModel',
		link: function (scope, element, attrs, ngModel) {
			ngModel.$validators.integer = function (value) {
				return value.test(/^\-?\d+$/);
			};
		}
	}
}

angular
	.module('app')
	.directive('integer', integer);
```

You might've noticed we're simply adding to the `ngModel.$validators` object instead of pushing into it. This is because we need to give our validators a simple name that will then get added to our `$errors` object if the validation returns false. We can also use these custom validators in `ngMessages`! To activate this validation on an input, we add it as an attribute like when we use `maxlength`, etc.

Example usage of our new validator would look like this:

```html
<form name="form">
	<input name="number" ng-model="ctrl.number" integer />

	<div ng-messages="form.number.$errors">
		<div ng-message="integer">Number must be an integer!</div>
	</div>
</form>
```

Awesome! Custom validation that slots in nicely with the built-in validation we've used previously.

# ngRoute : Routing our applications

Up until now, nothing our users have done will be reflected by the URL. Every action is taking place in the context of the main page. Although we're creating a single page application, we still need to split it into logical chunks. Just think how Facebook has user profiles, your timeline, your settings, etc. all under different URLs - we need to be able to do the same.

Our URLs should represent the action that the user wants to make - it wouldn't make sense to have our settings page at `/home` or our home page at `/settings`. We should also be able to revisit our URLs and receive the same page back. A user should be able to bookmark a settings page or send the link to their friend and see the same content the second time.

Angular allows us to do this - we can define these routes in our application, using controllers and templates (quite similar to our directives). Angular, by default, attaches these route URLs to the `#` (hash). This is to maximize browser compatibility - we can change the hash of the page without refreshing the page - only newer browsers can actually update the URL without refreshing the page. This means our `http://site.com/settings` and `http://site.com/home` routes will actually become `http://site.com/#/settings` and `http://site.com/#/home` respectively.

## ngRoute

`ngRoute` is a module that is provided to us by the Angular team. This is a basic router that allows us to specify different templates and controllers for our views.

You will need to make sure that you include `angular-route.js` in your code and add `ngRoute` to your main module's dependencies!

Now, where do we actually configure our routes?

One neat thing that Angular allows us to do is to "configure" our module. We can call the `.config` function provided to us by our modules, and specify any configuration for that module in there.

```js
angular
	.module('app', ['ngRoute'])
	.config(function () {
		// this is ran as soon as we initiate the module (ng-app)
	});
```

This function, much like our controllers, allows us to dependency inject our services into it. This means that we can inject `$routeProvider` - a service given to us by `ngRoute`, that allows us to configure our views.

To define a route, we call `$routeProvider.when` with two arguments - the URL that we want to configure, and a configuration object. This configuration object can take quite a few different options.

```js
angular
	.module('app', ['ngRoute'])
	.config(function ($routeProvider) {

		$routeProvider
			.when('/user', {
				// configuration object
			});
	});
```

In our configuration object, we can use the following items -

- `template` or `templateUrl` - specifies the template that we use for that route (this works exactly like it would in a directive)
- `controller` - specifies the controller that we use for that route (works the same as when we provide a string as the controller value in a directive)
- `resolve` - an object of resolves that provides the data we need for that route (more on this later)

Let's configure our `/user` route to use `user.html` as a template, and the `UserController` as its controller.

```js
angular
	.module('app', ['ngRoute'])
	.config(function ($routeProvider) {
		$routeProvider
			.when('/user', {
				templateUrl: 'views/user.html',
				controller: 'UserController'
			});
	});
```

Awesome! Now, when we go to `/#/user` in our application, we will see the user view, using the user controller to manage its data. Wait a minute - no we won't.

In order to actually display our routes on the page, we need to tell `ngRoute` where to actually *put* the user view. We can do this using the directive `ng-view`.

In our HTML, we would do something like this:

```html
<div ng-app="app" class="app">
	<div ng-view></div>
</div>
```

The `ng-view` directive will then put whatever route's template as it's contents when we go to that route - awesome!

### Dynamic Views

Being able to go to `/user` is great, but what if we wanted to view a different user's profile? Well, we would need to specify the ID of that user. But our route isn't setup to receive an ID, and we can't hard code *every* ID into our router. This is where dynamic views come in.

Much like when we used `$resource`, we can put variables into our URLs by using a colon. For instance, if we wanted to be able to go to `/user/1231` and `/user/94343` etc, we'd put `:id` into our URL.

```js
angular
	.module('app', ['ngRoute'])
	.config(function ($routeProvider) {
		$routeProvider
			.when('/user/:id', {
				templateUrl: 'views/user.html',
				controller: 'UserController'
			});
	});
```

This now allows us to go to the URLs we mentioned above. Awesome! But how do we actually know what the user's ID is? We'd need to go and fetch the user data so it's important that we can access what the variable is actually equal to.

This is where another service provided by `ngRoute` comes in - `$routeParams`. We can inject this into our controllers and see what the ID variable is equal to.

```js
function UserController($routeParams) {
	// $routeParams = { id: 1231 };
}

angular
	.module('app')
	.controller('UserController', UserController);
```

Now that we can access all of our route params, we can now go off and fetch the data for that user - simple!

## Resolving Data

When we load our page, we might require some data from the server. We might have a user profile that needs data from the server, so we know all about that user and a list of their photos for example. This is where resolving data comes in - we can request data before our routes load, to then use in our page.

Now, we could go and fetch user data in our controller, but that means that the view will load and then we will have a flicker between the view having no user data and the view being populated with data.

Instead, we can use the `resolve` property we spoke about earlier - this allows us to specify a bunch of promises that we want to be resolved *before* our view is rendered.

Say that we have a `UserService` that returns a `$http.get` call to get the user's profile:

```js
function UserService($http) {
	this.getUser = function (id) {
		return $http.get('/user/' + id);
	};
}
```

And we're currently injecting that into our `UserController`, and using `$routeParams` to specify the user's ID.

```js
function UserController($routeParams, UserService) {
	var ctrl = this;

	UserService
		.getUser($routeParams.id)
		.then(function (res) {
			ctrl.user = res.data; // our user object is populated from the backend
		});
}

angular
	.module('app')
	.controller('UserController', UserController);
```

This will cause the flicker that we mentioned earlier. Instead, we can define our `UserService.getUser` call in the `resolve` property on our route's configuration.

```js
angular
	.module('app', ['ngRoute'])
	.config(function ($routeProvider) {
		$routeProvider
			.when('/user/:id', {
				templateUrl: 'views/user.html',
				controller: 'UserController as user',
				resolve: {
					user: function ($routeParams, UserService) {
						return UserService.getUser($routeParams.id);
					}
				}
			});
	});
```

Here we're doing very similar things to what we're doing in our controller - injecting `$route` and our `UserService`, but instead we're returning the promise given to us by our `$http.get` call. Once this promise resolves, `ngRoute` will then render our view.

That's great, but now how do we get access to that data? Simple - you notice that we're using the key `user` in our resolve object? We can now inject `user` into our controller, accessing all the data that the resolve gives us.

```js
function UserController(user) {
	var ctrl = this;

	ctrl.user = user.data;
}

angular
	.module('app')
	.controller('UserController', UserController);
```

Simple! No flicker, and we've got dynamic routes working whilst also fetching the relevant data!

Example
```js
angular
    .module('app', ['ngRoute'])
    .config(function($routeProvider){
    	$routeProvider
    		.when('/user/:name', {
    			templateUrl: 'views/user.html',
    			controller: 'UserController as ctrl',
    			resolve: {
    				user: function ($route, $http) {
    					console.log($route);
    					return $http.get("http://0.0.0.0:8882/rest/user/" + $route.current.params.name);
    				}
    			}
    		})
    });
```

Our controller
```js
function UserController(user) {
	var ctrl = this;

	ctrl.user = user.data;
	console.log(ctrl.user);
}

angular
	.module('app')
	.controller('UserController', UserController);
```

Our index
```html
<div ng-app="app" class="app">
    <a href="#/user/liam">Liam</a> - <a href="#/user/jayden">Jayden</a> - <a href="#/user/mary">Mary</a>

    <div ng-view></div>
</div>
```

And views/user.html
```html
<div>
	<h2>{{ ctrl.user.name.title }} {{ ctrl.user.name.first }} {{ ctrl.user.name.last }}</h2>
	<p>{{ ctrl.user.email }}</p>
</div>
```

# uiRouter

`uiRouter` is quite similar to `ngRoute`, but each "route" is known as a "state". We define states, not routes.

Each state that we define is quite similar to a route in `ngRoute`, but we have to give each state a name too. This allows us to have children states inside of a state (we'll go onto nested states/views soon).

This is awesome - you might've noticed how in the last lab we've got three links to `#/user/name`. Instead, with uiRouter, we can use the state names instead of URLs. This saves us time in the long run - if we have 100 different places in our app that link to the user page, imagine having to update all of them to the URL if it ever changed! However, as we've got state names, we won't have to update any of them.

Let's take a look at how we'd define a route in `ngRoute`:

```js
angular
	.module('app', ['ngRoute'])
	.config(function ($routeProvider) {
		$routeProvider
			.when('/user', {
				templateUrl: 'views/user.html',
				controller: 'UserController'
			});
	});
```

And how we'd define a route in `uiRouter`:

```js
angular
	.module('app', ['ui.router'])
	.config(function ($stateProvider) {
		$stateProvider
			.state('user', {
				url: '/user',
				templateUrl: 'views/user.html',
				controller: 'UserController'
			});
	});
```

You can see they're very similar. We've moved the URL into the configuration object, and replaced the URL with the state's name. We're also using `$stateProvider` instead of `$routeProvider`.

Instead of using `ng-view`, we use `ui-view` to place the states in our HTML.

We'll go into more advanced concepts with `uiRouter` soon - things such as nested views and resolving data.

## uiSref

`uiRouter` also provides a directive named `ui-sref` (as in, [$state.href()](http://angular-ui.github.io/ui-router/site/#/api/ui.router.state.directive:ui-sref)). We mentioned earlier about linking to states by name - this is where `uiSref` comes in. We can use this on our hyperlinks to generate links to our states. We pass in the state name as the value and `uiRouter` will replace the link with a link to our state.

Say we've got a state named `docs`, that links to `/documentation/v1`:

```js
angular
	.module('app', ['ui.router'])
	.config(function ($stateProvider) {
		$stateProvider
			.state('docs', {
				url: '/documentation/v1',
				templateUrl: 'views/user.html',
				controller: 'UserController'
			});
	});
```

We can then use `ui-sref="docs"` to link to that state.

```html
<a href="" ui-sref="docs">Go to the docs!</a>
```

This will then get automatically changed into:

```html
<a href="/documentation/v1">Go to the docs!</a>
```

This is awesome - we can change the URL on our states without changing the name and all of our links get updated to match the new URL.

## uiSrefActive

`uiRouter` also provides us with one more directive - `ui-sref-active`. We pass in a class name as the value, and when the given state inside our `ui-sref` is active, it will apply this class to the link.

For instance, if we have this:

```html
<a href="" ui-sref="docs" ui-sref-active="active">Go to the docs!</a>
```

When we're actually on the docs page, that link will get the `active` class applied to it:

```html
<a href="" class="active" ui-sref="docs" ui-sref-active="active">Go to the docs!</a>
```

Simple!

Example / only what changes from previous version using ngRoute
```html
<div ng-app="app" class="app">
    <a href="" ui-sref="user({name: 'liam'})" ui-sref-active="active">Liam</a> - <a href="" ui-sref="user({name: 'jayden'})" ui-sref-active="active">Jayden</a> - <a href="" ui-sref="user({name: 'mary'})" ui-sref-active="active">Mary</a>

    <div ui-view></div>
</div>
```

and the main module
```js
angular
    .module('app', ['ui.router'])
    .config(function($stateProvider){
    	$stateProvider
    		.state('user', {
    			url: '/user/:name',
    			templateUrl: 'views/user.html',
    			controller: 'UserController as ctrl',
    			resolve: {
    				user: function($http, $stateParams){
    					console.log($stateParams);
    					return $http.get('http://0.0.0.0:8882/rest/user/' + $stateParams.name)
    				}
    			}
    		});
    });
```

# Nested View

Imagine that we have a normal setup for a web page - a header, a footer, and everything in between those change depending on what page we are on. This is great for most cases - we can swap between different pages such as home, about, contact, etc.

But what if we want to have a settings page, with multiple different pages for us to look at? We might want to be able to edit profile information, but also change our notification preferences or even have a "delete your account page".

We'd setup our settings route, and this would be displayed in our main section where all the routes go. What now? How do we get all these different pages rendered *inside* our settings page?

We could just create a tabs component that changes what we can see depending on what tab has been clicked, but it means our URL will always stick at `/settings` rather than changing between `/settings/notifications` and `/settings/user`.

This is where nested views come in. As mentioned before with states, a state can have multiple children states. These will then be rendered inside of our parent state - but we must make sure that we use the `ui-view` directive inside our parent state too.

Our previous setup might've looked like this:

```js
angular
	.module('app', ['ui.router'])
	.config(function ($stateProvider) {
		$stateProvider
			.state('settings', {
				url: '/settings',
				templateUrl: 'views/settings.html',
				controller: 'SettingsController'
			})
			.state('settingsUser', {
                url: '/settings/user',
                templateUrl: 'views/settings/user.html',
                controller: 'UserSettingsController'
            })
            .state('settingsNotifications', {
                url: '/settings/notifications',
                templateUrl: 'views/settings/notifications.html',
                controller: 'NotificationsSettingsController'
            })
	});
```

Let's setup our settings example in `uiRouter`.

```js
angular
	.module('app', ['ui.router'])
	.config(function ($stateProvider) {
		$stateProvider
			.state('settings', {
				url: '/settings',
				templateUrl: 'views/settings.html',
				controller: 'SettingsController'
			})
			.state('settings.user', {
                url: '/user',
                templateUrl: 'views/settings/user.html',
                controller: 'UserSettingsController'
            })
            .state('settings.notifications', {
                url: '/notifications',
                templateUrl: 'views/settings/notifications.html',
                controller: 'NotificationsSettingsController'
            })
	});
```

We're not saving much code here - but by having child states it means we can render those states *inside* the parent state - the first example of code would replace the settings state with either the notifications or user settings state.

You'll notice how we state the parent controller in the name of the state. We put the parent name first, then a dot, and then the actual state name. This tells `uiRouter` that `settings` is the parent state.

You'll also notice on our `settings.user` and `settings.notifications` states, we haven't put the URLs as `/settings/user` and `/settings/notifications` respectively - this is because they automatically inherit the URL from their parent state. We are simply adding on `/user` and `/notifications` to `/settings`.

Now, inside of our `settings.html` we need to make sure we include the `ui-view` directive. This is where the templates for our users and notifications pages will be rendered.

```html
<div class="settings">
	<h3>Settings</h3>

	<a ui-sref="settings.user">User Settings</a> - <a ui-sref="settings.notifications">Notification Settings</a>

    <div ui-view></div>
</div>
```

Now our user and notifications pages will be rendered underneath the settings navigation - neat!

Also, when we go to `/settings/user`, `uiRouter` automatically detects that our parent state is `settings`, and puts this into our main applications `<div ui-view>`. It'll then sort out the children states, so it renders the page correctly.

It's important to note that when we load a child state, such as `settings.user`, it'll resolve all the parent state's resolves. If we had a resolve on `settings` to fetch settings data, going to our `settings.user` state will load that resolve on the `settings` state.

Example 
```js
angular
    .module('app', ['ui.router'])
    .config(function($stateProvider, $urlRouterProvider){
    	$stateProvider
    		.state('home', {
    			url: '/',
    			templateUrl: 'views/home.html'
    		})
    		.state('home.timeline', {
    			url: 'timeline',
    			templateUrl: 'views/home/timeline.html'
    		})
    		.state('home.notifications', {
    			url: 'notifications',
    			templateUrl: 'views/home/notifications.html'
    		})
    		.state('home.user', {
    			url: 'user',
    			templateUrl: 'views/home/user.html'
    		})    		
    	$urlRouterProvider.otherwise('/');	
    });
```

and in our views/home.html
```html
<div class="settings">
	<h4>Twitter Home</h4>

	<nav><a ui-sref="home.timeline" ui-sref-active="active">Timeline</a> - <a ui-sref="home.notifications" ui-sref-active="active">Notifications</a> - <a ui-sref="home.user" ui-sref-active="active">User</a></nav>
	
	<div ui-view />
</div>
```

# Testing Routing

When we test our routes/states we should check that the URL is as we expect, that it's using the correct template and fetching the correct data that it needs.

To get all of our states configuration, we can inject `$state` and use `$state.get` to retrieve the configuration object for that state. As we've registered all of our states with the `$stateProvider`, we can then access them all via `$state`.

An example test would look like:

```js
describe('Routes', function () {
	var $state;

	beforeEach(module('app'));

	beforeEach(inject(function ($injector) {
		$state = $injector.get('$state');
	}));

	describe('Settings', function () {
		var state;

		it('should have the correct URL', function () {
			state = $state.get('settings');

			expect(state.url).toEqual('/settings');
		});
	});
});
```

Here we're testing that the URL is correct. We can then test the `templateUrl` too:

```js
describe('Routes', function () {
	var $state;

	beforeEach(module('app'));

	beforeEach(inject(function ($injector) {
		$state = $injector.get('$state');
	}));

	describe('Settings', function () {
		var state;

		it('should have the correct URL', function () {
			state = $state.get('settings');

			expect(state.url).toEqual('/settings');
		});

		it('should use the correct template', function () {
            expect(state.templateUrl).toEqual('views/settings.html');
        });
	});
});
```

We'd then repeat this for all of our routes. This ensures that all of our routes are correct so that if we accidentally change a URL in the future, we won't be providing a bad user experience to the existing users!

# Performance with Track By

Now that we've started to build our Angular applications, we can start to think about scaling them. As we start to display more data and allow complex user interactions with that data, our application can become slow, much like if we build a one-way street and try and drive 5,000 cars in both directions. There are a few neat tricks we can use to improve performance.  Each performance enhancement we use in Angular is like adding an extra road, allowing things to become much quicker.

## What is track by?

Track by allows us to identify JavaScript objects in an `ng-repeat` list so that Angular won't `$destroy` or re-create DOM nodes unnecessarily.

For example, if we were to have an `ng-repeat` repeating the news, Angular will display all of the news items on the page.

Later on, if we were to refresh the data (refresh the news), Angular will have to rebuild every DOM node in the repeat, even if two of the articles are the same. Any change in the array will result in a rebuild of the DOM - Angular has no way of telling what items in the new array are the same in the last array.

To prevent this, we can use `track by` in our `ng-repeat`s. This tells Angular what to use to identify the news article.

If our data structure looks like this:

```js
var newsItems = [{
	id: 2342339,
	title: 'Apple customer goes to the top for iPhone battery answer',
	timestamp: 1457697486000
}, {
	id: 2342320,
	title: 'Android N brings split-screen multitasking apps',
	timestamp: 1457609266000
}];
```

Here we've got two items of news. Angular will then display these on the page. If we were then to refresh the news, and a new item of news comes in:

```js
var newsItems = [{
	id: 2342342,
	title: 'Computer wins series against Go master',
	timestamp: 1457773283000
}, {
	id: 2342339,
	title: 'Apple customer goes to the top for iPhone battery answer',
	timestamp: 1457697486000
}, {
	id: 2342320,
	title: 'Android N brings split-screen multitasking apps',
	timestamp: 1457609266000
}];
```

Angular would then delete the original two DOM nodes, and then render three DOM nodes in its place - this is because it doesn't know what makes each news article uniques (it can't tell what has changed, so assumes it all has).

## Using track by

As you can see, all of our news articles have unique IDs associated with these. Let's let Angular know about these!

This:

```
<ul class="news">
	<li ng-repeat="item in ctrl.news">
		{{ item.title }}
	</li>
</ul>
```

Will turn into this:

```
<ul class="news">
	<li ng-repeat="item in ctrl.news track by item.id">
		{{ item.title }}
	</li>
</ul>
```

Letting Angular know to track by the `id` property on the news articles.

If we go back to when we update the data - instead of removing two DOM nodes and creating three, Angular just creates one new DOM node at the top of the list - awesome!

# Filters inside/outside of controllers

When we use a filter on an `ng-repeat`, such as:

```html
<input ng-model="ctrl.search" />
<ul>
	<li ng-repeat="contact in ctrl.contacts | filter:ctrl.search">
		{{ contact.name }}
	</li>
</ul>
```

Everytime that our digest cycle is run, our filter is re-run, even if there are no changes to the `ctrl.search` value. This means there are pointless recalculations done by Angular.

One way that we can stop this is by actually filtering on the `ctrl.contacts` array in our controller. We can then control *when* we filter on the list.

We would take this:

```js
function ContactList() {
	this.contacts = [{
		name: 'Bill Gates',
		email: 'bill@microsoft.com',
		phone: '01234567890',
		username: 'b1lLG4Tes'
	},{
		name: 'Steve Jobs',
		email: 'steve@apple.com',
		phone: '12345678910',
		username: 'steveJOBS!!!!!!'
	},{
		name: 'Joe Bloggs',
		email: 'joe@bloggs.com',
		phone: '13092019340',
		username: 'jb'
	},{
		name: 'President Obama',
		email: 'president@whitehouse.com',
		phone: '75934988239',
		username: 'obamaY0'
	}];

	this.search = '';
}
```

and call `$filter('filter')` on our `contacts` array:

```js
function ContactList($filter) {
	this.contacts = [{
		name: 'Bill Gates',
		email: 'bill@microsoft.com',
		phone: '01234567890',
		username: 'b1lLG4Tes'
	},{
		name: 'Steve Jobs',
		email: 'steve@apple.com',
		phone: '12345678910',
		username: 'steveJOBS!!!!!!'
	},{
		name: 'Joe Bloggs',
		email: 'joe@bloggs.com',
		phone: '13092019340',
		username: 'jb'
	},{
		name: 'President Obama',
		email: 'president@whitehouse.com',
		phone: '75934988239',
		username: 'obamaY0'
	}];

	this.search = '';

	this.filteredList = $filter('filter')(this.contacts, this.search);
}
```

Now we have a filtered list in our `filteredList`. We will then change the `ng-repeat` over to use this list instead.

```html
<input ng-model="ctrl.search" />
<ul>
	<li ng-repeat="contact in ctrl.filteredList">
		{{ contact.name }}
	</li>
</ul>
```

Notice how we don't use a filter in our `ng-repeat` anymore, and it looks a lot neater? Having the filter in the controller allows us to know exactly what our data is going to be when we look at the controller, and it simplifies the view.

Now we need to update the filter when the `ctrl.search` value changes - we can do this using `ng-change`.

```html
<input ng-model="ctrl.search" ng-change="ctrl.refilter()" />
<ul>
	<li ng-repeat="contact in ctrl.filteredList">
		{{ contact.name }}
	</li>
</ul>
```

We're calling a `refilter` function in our controller - let's define that:

```js
function ContactList($filter) {
	this.contacts = [{
		name: 'Bill Gates',
		email: 'bill@microsoft.com',
		phone: '01234567890',
		username: 'b1lLG4Tes'
	},{
		name: 'Steve Jobs',
		email: 'steve@apple.com',
		phone: '12345678910',
		username: 'steveJOBS!!!!!!'
	},{
		name: 'Joe Bloggs',
		email: 'joe@bloggs.com',
		phone: '13092019340',
		username: 'jb'
	},{
		name: 'President Obama',
		email: 'president@whitehouse.com',
		phone: '75934988239',
		username: 'obamaY0'
	}];

	this.search = '';

	this.filteredList = $filter('filter')(this.contacts, this.search);

	this.refilter = function () {
		this.filteredList = $filter('filter')(this.contacts, this.search);
	};
}
```

There's no need for us to explicity write the `$filter` call twice. We can just simply call the `refilter` function in the controller:
Note **we need to inject $filter**.
```js
function ContactList($filter) {
	this.contacts = [{
		name: 'Bill Gates',
		email: 'bill@microsoft.com',
		phone: '01234567890',
		username: 'b1lLG4Tes'
	},{
		name: 'Steve Jobs',
		email: 'steve@apple.com',
		phone: '12345678910',
		username: 'steveJOBS!!!!!!'
	},{
		name: 'Joe Bloggs',
		email: 'joe@bloggs.com',
		phone: '13092019340',
		username: 'jb'
	},{
		name: 'President Obama',
		email: 'president@whitehouse.com',
		phone: '75934988239',
		username: 'obamaY0'
	}];

	this.search = '';

	this.refilter = function () {
		this.filteredList = $filter('filter')(this.contacts, this.search);
	};

	this.refilter();
}
```

Awesome! Now our filter is in our controller, and is only updated when we want it to be!

# ngModelOptions

So far, we've been updating our model values immediately. However, in some circumstances, we might want to wait until the user has actually finished typing. You'll notice this is used quite a lot in popular applications. Facebook waits for you to have finished typing for a little bit before making a search query. This reduces server load and stops them firing off hundreds of pointless requests as the user types.

We apply `ng-model-options` to our inputs, passing in a configuration option.

```html
<input ng-model="ctrl.search" ng-model-options="{}" />
```

This configuration option can take the following options:

### updateOn

We can choose `ng-model` to only update on a certain type of event, such as `blur`. We can also use the event `default` to allow it to update on all events. You can use as many events as you want, as long as they are separated by a space.

```html
<input ng-model="ctrl.search" ng-model-options="{updateOn: 'blur'}" />
```

This will only update `ctrl.search` when the user exits the input.

### debounce

We can also "debounce" updates. This means that we can set a timer for the update after the user has stopped typing.

If we set it to 200ms, it will wait for no button presses on the input for 200ms before updating the value. You'll notice that Google has a similar feature - it doesn't search until you have finished typing.

```html
<input ng-model="ctrl.search" ng-model-options="{debounce: 1000}" />
```

This will only update `ctrl.search` after the user has stopped typing for a full second.

We can also pass through an object of different event types to debounce. For instance, if we wanted it to update immediately after the user exits the input, but a second after the user stops typing, we'd use:

```html
<input ng-model="ctrl.search" ng-model-options="{ updateOn: 'default blur', debounce: {'default': 1000, 'blur': 0} }" />
```

# Dependency Injection

Let's say we've got a controller that injects `$scope`, `$timeout` and `UserService`.

```js
function SomeController($scope, $timeout, UserService) {

}

angular
	.module('app')
	.controller('SomeController', SomeController);
```

When we plug this controller into Angular, Angular checks what dependencies it wants and creates an `$inject` array on our controller:

```js
function SomeController($scope, $timeout, UserService) {

}

SomeController.$inject = ['$scope', '$timeout', 'UserService'];

angular
	.module('app')
	.controller('SomeController', SomeController);
```

This is where the overhead comes in! Angular has to parse the string version of our function, filter out all the unnecessary parts and compile an array of the needed dependencies.

## strictDI

strictDI means that Angular will no longer create that `$inject` property for us - we must specify it ourselves, removing any unnecessary overhead.

We can turn on strictDI by putting the directive `ng-strict-di` on the same element we put `ng-app` on.

```
<div ng-app="app" ng-strict-di>
</div>
```

Now, any custom filter/service/directive/controller/etc that does not have the `$inject` property defined will throw an error. If we've annotated all of our functions correctly (saving Angular a load of time), it'll work exactly like before - just that little bit faster!

# applyAsync

We can turn on $applyAsync in our modules config.

```js
angular
	.module('app')
	.config(function ($httpProvider) {
        $httpProvider.useApplyAsync(true);
	});
```

Here we're injecting `$httpProvider` (that configures everything to do with `$http`) and turning applyAsync on. But what does it actually do?

applyAsync batches our `$http` calls that happen at a similar time into one digest cycle call. If we have two `$http` calls that happen at the same time, normally we'd be running two digest cycles - this isn't great for performance.

Instead, applyAsync will notice that these two requests are near each other and wait for them both to complete, running one digest cycle after that. This is great! It saves a lot of processing time for one little configuration object. However, this does mean there is a slight delay between making your request and then Angular making the actual HTTP request - this is because it needs to wait to see if there are any other `$http` calls to batch into one.

Improving performance is all about trade offs. As you build more Angular applications, you'll become comfortable deciding when to implement this feature.

# Disabling debug info

Load a previous Angular lab and look at it in developer tools. You'll see loads of weird classes. These are there to tell our testing applications what is actually going on inside Angular, so they don't need to dive into the JavaScript code to find out. `ng-binding` tells the testing program that the value is bound to a variable. `ng-scope` is where a new scope has been created. They're not necessary for Angular to function, however.

Much like applyAsync, it's just a simple configuration switch to turn these off.

We use `$compileProvider` and call `debugInfoEnabled` with false, turning it off.

```js
angular
	.module('app')
	.config(function ($compileProvider) {
        $compileProvider.debugInfoEnabled(false);
	});
```

Now that we've done that, you'll no longer see any classes or comments added anywhere. Awesome! A little overhead, but in the long run, makes things a lot faster.

# Watching models with $scope.$watch and $scope.$watchCollection

In our controllers, we can watch when values update using `$scope.$watch`. We pass through two functions to this - the first one is a function that returns the value we want to watch. The second is the function that gets called when the value is updated.

```js
function SomeController($scope) {
	var ctrl = this;
	ctrl.search = '';

	$scope.$watch(function () {
		return ctrl.search;
	}, function (newValue, oldValue) {
		console.log('value updated!');
	});
}

angular
	.module('app')
	.controller('SomeController', SomeController);
```
```html
<input ng-model="ctrl.search" />
```

When a user types into our input, our function will get called with its old value and its new value. For instance, if we typed the letter `r` into our input, it would get called with `oldValue` equal to `''` and `newValue` equal to `'r'`.

## Watching objects/arrays

We've looked at observing strings, now let's watch objects/arrays. We can do this with `$scope.$watchCollection`


```js
function SomeController($scope) {
	var ctrl = this;
	ctrl.collection = {
		id: 5,
		name: 'Test'
	};

	$scope.$watchCollection(function () {
		return ctrl.collection;
	}, function (newValue, oldValue) {
		console.log('value updated!');
	});
}

angular
	.module('app')
	.controller('SomeController', SomeController);
```

This will then fire out whenever we change any item in that object! However, this doesn't work that well when we change a value inside an object inside an object. For instance, if we have an object with the variable `user` and update the `name` property inside it from `Bob` to `Alice`, we will get notified. Same as if we removed the property, or added a new one. However, we don't get the same level of checks on deep nested objects.

## Deep-watching objects/arrays

We can deep watch objects/arrays by going back to `$scope.$watch`, but passing in a third parameter of `true` to tell Angular to deep watch the collection.

```js
function SomeController($scope) {
	var ctrl = this;
	ctrl.collection = {
		id: 5,
		name: 'Test',
		country: {
			name: 'United States'
		}
	};

	$scope.$watch(function () {
		return ctrl.collection;
	}, function (newValue, oldValue) {
		console.log('value updated!');
	}, true);
}

angular
	.module('app')
	.controller('SomeController', SomeController);
```

Before, with `$scope.$watchCollection`, if we had updated the country's name, we wouldn't have got a callback fired. However, with `$scope.$watch`, we do! Just be careful - this requires more resources to check the object, so use them only when you must.

Angular doesn't deep watch by default as it is more intensive and requires more computation time in order to find differences. If it did do it by default, our digest cycle will be a lot slower!

Be careful using these functions - they mean that extra checks are added to the digest cycle (on top of the ones automatically created by Angular), meaning that every time it is ran, it takes even longer.

# $$watchers, $digest cycle and dirty-checking

Whenever we need to watch a model value (such as using `$scope.$watch` or `{{ ctrl.value }}`), Angular pushes an item into a property named `$$watchers` on our scope.

What is a `$$watcher`? A watcher stores the function that we use to get the latest value of the item (remember the first function we pass through to `$scope.$watch`?), the last known value (oldValue that gets passed to our callback), our callback and also whether or not we're deep watching the collection.

When we run the digest cycle, Angular loops through all of our watchers and executes the first function, that returns the latest value of the item. It then compares (or deep checks) the last value and the new value, and calls the callback when the values are different.

Imagine we have an `ng-repeat` repeating a list of people, with 5 different expressions in our element, displaying name, email, phone, address and nickname. When we have 1000 people, we have 1000x5=5000 watchers added to the `$$watchers` array. These are then **all** ran when we run the digest cycle - can you see why it gets slow now?

It's important that we try and minimize our `$$watchers` count - use `$scope.$watch` only when you need to, and try and avoid watching full objects, as it takes more time to compare them.


