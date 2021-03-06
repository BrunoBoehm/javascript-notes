# ReactJS

React is a JavaScript *library* (not a framework - as opposed to Angular) that's used for building user interfaces. It's an open source project, that started at Facebook, and is maintained by developers at Facebook and Instagram, and also a large community of contributors. One of the benefits and goals of the React project is to make developing a large scale, single page application easier.
React is also included in the larger movement in the world of JavaScript, the functional programming movement. You may have heard about functional JavaScript, a programming paradigm that emphasizes function composition over object orientation. React also aims to follow the principles of immutable data. So we create copies of objects and replace them, instead of mutating the originals. React is commonly used in enterprise applications, by companies including PayPal, AirBnB, Apple, Uber, and, of course, Facebook.

React encourages us to write small, laser-focused components that compose together in an elegant manner.

React has a virtual DOM that writes to the browser DOM only when it needs to. It only interacts with the virtual DOM, that JavaScript object in between the JavaScript logic and the actual DOM. When we call the `render` function, React will update the virtual DOM. That will push only the necessary changes all the way to the real DOM.

Virtual DOM is a technique employed by several front-end libraries and frameworks, most notably React. In a nutshell, virtual DOM builds a virtual representation of what our document should look like. When we're ready to render things to the screen, the virtual DOM will take a look at the existing DOM and change only what needs to be changed (in more technical terms, it's diffing and re-rendering the changes).

The performance gains here are not to be underestimated. Virtual DOM is created by a bunch of super smart people using extremely efficient algorithms. Most virtual DOMs also batch their updates to the DOM, ensuring that the real DOM gets modified as little as possible.

This means that we don't need to write imperative code to update every tiny bit of our application, *we just declare what the end result should look like, and the virtual DOM will do the rest*! The ability to simply declare what our component should look like and how it should behave is a huge win. That means we can think more about how our UI fits together, rather than how we're supposed to be updating it!

- [Why did we build React?](https://facebook.github.io/react/blog/2013/06/05/why-react.html)
- [The difference between Virtual DOM and DOM](http://reactkungfu.com/2015/10/the-difference-between-virtual-dom-and-dom/)
- [React (Virtual) DOM Terminology](https://facebook.github.io/react/docs/glossary.html)

## Declarative Programming
Let's say we have some kind of search component that allows us to filter a list of results. When the input updates, we filter the list data and then display the updated results in our component. 

In React, we just tell it what we want the component to look like (i.e. display these items that have been filtered), whereas in a non-declarative application, we'd have to slog through manually updating our DOM — removing the results that are not relevant anymore, and adding the new ones to the list.

[Declarative programming](http://stackoverflow.com/questions/33655534/difference-between-declarative-and-imperative-in-react-js) allows us to focus on what our application should look like — as opposed to being concerned with manually updating DOM, adding and removing classes, and so on. That stuff is all done for us in React: we just tell React what the end result should be. It'll do the heavy lifting for us.

## ES6
[ES6](https://nodejs.org/en/docs/es6/) is the next specification for JavaScript, and it's finally started to appear in a major way in browsers and on servers thanks to Node.js 5.

We'll use `"use strict";` - generally, it turns silent failures into thrown errors, and it helps prevent variables sneaking into the global scope. You can use it at the top of the current script — strict mode then applies to the entire script. Alternatively, you can apply strict mode to individual functions.

Strict mode does just as its name implies: it enforces stricter rules on the execution of your code. Note that some transpilers (like babel) can set strict mode for you.
Strict mode also enables some newer features that ES6 developers wanted to make sure users explicitly opted in to.

There are a lot of new features, like

* [`const` and `let`](#block-scoping)
* [Classes](#classes-use-strict)
* [Arrow Functions](#arrow-functions)
* [Promises](#promises)
* [Object Literal Extensions](#object-literal-extensions)
* [Spread Operator](#spread-operator)
* [Template Strings](#template-strings)
* [Destructuring](#destructuring)

### Block Scoping

#### `let` ("use strict")

The keyword [`let`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let) is a new way of declaring local variables. How does it differ from good ol' `var`? Variables declared with `let` have block-level scope:

```javascript
// https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Scoping_rules
function letTest() {
  let x = 31;
  if (true) {
    let x = 71;  // different variable
    console.log(x);  // 71
  }
  console.log(x);  // 31
}
```

Notice how `x` declared outside of the `if` block differs from the `x` declared inside the block. Block-level scope means that the variable is available only in the block (`if`, `for`, `while`, etc.) in which it is defined; it differs from JavaScript's normal function-level scope, which restricts the variable to the function in which it is defined (or `global`/`window` if it's a global variable).

#### `const`

The keyword [`const`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/const) does not require strict mode. Like `let`, it declares a variable with block-level scope; additionally, it prevents its variable identifier from being reassigned.

That means that the following will throw an error:

```javascript
const myVariable = 1;

myVariable = 2; // syntax error
```

However, this does not mean that the variable's value is immutable — the value can still change.

```javascript
const myObject = {};

// this works
myObject.myProperty = 1;

// 1
console.log(myObject.myProperty)
```

### Classes ("use strict")

```javascript
class Polygon {
  constructor(height, width) {
    this.height = height;
    this.width = width;
  }

  // whaaaaat -- getters!
  get area() {
    return this.calcArea();
  }

  calcArea() {
    return this.height * this.width;
  }
}

const rectangle = new Polygon(10, 5);

console.log(rectangle.area);
```

Let's extend it:

```javascript
class Square extends Polygon {
  constructor(sideLength) {
    super(sideLength, sideLength)
  }
}

const mySquare = new Square(5);

// Square { height: 5, width: 5 }
mySquare;

// [Function: Square]
mySquare.constructor;

// 25
mySquare.area;
```

### Arrow functions

[Arrow functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) provide not only a terser way to define a function but also _lexically bind the current `this` value_. This ain't your grandpa's JS.

```javascript
const greet = (greeting, person) => {
  return greeting + ', ' + person + '!';
};

// 'Hello, Marv'
greet('Hello', 'Marv');

var a = [
  'Hydrogen',
  'Helium',
  'Lithium',
  'Beryl­lium'
];

// compare this implementation...
var a2 = a.map(function(s){ return s.length });

// ... to this implementation with the fat arrow
var a3 = a.map(s => s.length);
```

Fat arrows also have implicit returns — the following are equivalent:

```javascript
var a3 = a.map(s => s.length);
var a4 = a.map(s => {
  return s.length;
});
```

If the function only accepts one argument, parentheses are optional:

```javascript
// this...
var a3 = a.map(s => s.length);

// ... is the same as this
var a3 = a.map((s) => s.length);
```

If there are zero or two or more arguments, though, you must use parens:

```javascript
var evens = [1, 2, 3, 4].reduce((memo, i) => {
  if (i % 2 === 0) {
    memo.push(i)
  }

  return memo;
}, []);
```

### Promises

[Promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) offer a new way of handling asynchronicity.

```javascript
const promise = new Promise((resolve, reject) => {
  return someIntenseTask().then(result => {
    if (result.success) {
      return resolve(result)
    }

    return reject(result.error)
  })
})

promise.then(result => {
  return doSomething(result);
}).catch(error => handleError(error))
```

### Object literal extensions

ES6 gives us a number of handy [new ways to deal with objects](https://github.com/lukehoban/es6features#enhanced-object-literals). They're features that you either wish JavaScript had, or ones you didn't know you needed.

```javascript
const prop = function() {
  return "I'm a prop!";
}

const myObj = {
  // computed (dynamic) property names
  ['foo' + 'bar']: 'something',

  // methods
  shout() {
    return 'AH!'
  },

  // short for `prop: prop`
  prop
}

// 'something'
myObj.foobar

// "I'm a prop!"
myObj.prop()

// 'AH!'
myObj.shout()
```

### Spread operator

The [spread operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_operator) — `...` — is unassuming but incredibly powerful.

We can use it for arrays:

```javascript
const a = [1, 2, 3]
const b = [0, ...a, 4, 5]

// [0, 1, 2, 3, 4, 5]
b
```

functions:

```javascript
function printArgs() {
  // recall that every function gets an `arguments`
  // object
  console.log(arguments);
}

// using `a` from above
// { '0': 1, '1': 2, '2': 3 }
printArgs(...a);
```

### Template Strings

[Template strings](https://nodejs.org/en/docs/es6/) in ES6 are most commonly used for string interpolation. Instead of writing:

```javascript
var foo = 'bar';
var sentence = 'I went to the ' + foo + ' after working in ES5 for too long.';
```

we can now write:

```javascript
var foo = 'bar';
var sentence = `I went to the ${foo} after working in ES5 for too long.`;
```

You can also use _tagged template literals_ to perform more advanced manipulation:

A _tag_ is simply a function whose first argument is an array of strings and whose subsequent arguments are the values of the substitution expressions (the things in `${}`).

Here's the example from [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals#Tagged_template_literals):

```javascript
var a = 5;
var b = 10;

function tag(strings, ...values) {
  console.log(strings[0]); // "Hello "
  console.log(strings[1]); // " world "
  console.log(values[0]);  // 15
  console.log(values[1]);  // 50

  return "Bazinga!";
}

tag`Hello ${ a + b } world ${ a * b }`;
// "Bazinga!"
```

### Destructuring

Destructuring makes it easier than ever to pull values out of objects and arrays and store them in variables. We destructure an array by putting our new variable names at the corresponding index and an object by giving our variable the same name as the key we are interested in.

```js
const [a, b] = [1, 2];
// a === 1 && b === 2

const { a, b } = { a: 1, b: 2 }
// a === 1 && b === 2
```

To see what other amazing things we can to with destructuring, check out the [docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).


## Making requests using XHR, $.ajax and fetch()
Getting remote data in JavaScript has classically required a fair amount of plumbing to make things happen.
It's not that it's *hard* to get data out of `XMLHttpRequest`, but it does take quite a bit of setup. 
Let's make a simple request of the Github repository commits API.

```js
let xhr = new XMLHttpRequest();
xhr.open('GET', 'https://api.github.com/repos/jquery/jquery/commits');
xhr.responseType = 'json';

xhr.onload = function() {
  console.log(xhr.response);
};

xhr.onerror = function() {
  console.log('Booo');
};

xhr.send();
```

Sure, it works, but that's a lot of setup to just say "give me some JSON from this URL".
Things get a little better with jQuery's `$.ajax`, except then we have to tightly couple ourselves to jQuery, and ultimately, it's just syntactic sugar over `XMLHttpRequest`.

### GET

The `fetch()` function is a new API for fetching resources. It's a global function, which means no creating new XHR objects, and it vastly streamlines simple resource requests. Let's try that call to the Github commits API again.

```js
fetch('https://api.github.com/repos/jquery/jquery/commits')
  .then(res => res.json())
  .then(json => console.log(json));
```

In JavaScript, a `Promise` object represents a value that may not be available yet, but will be resolved at some point in the future. Essentially, the promise is an object that represents the result of an operation, whenever it occurs. This allows us to write more flexible asynchronous code than simply passing callback functions to asynchronous functions.

All promises implement a `then` function that is called when the promise is *fulfilled*, or completed successfully. So this is very similar to the idea of a callback on success that we'd use with `XMLHttpRequest` or `$.ajax`.

The interesting thing about this `fetch` code is that it highlights a powerful feature of a `thenable` object — we can chain each `then` call, and the next one receives the result of the previous one as its argument.

```js
fetch('https://api.github.com/repos/jquery/jquery/commits')
  .then(res => res.json())
  .then(json => console.log(json));
```

the line `then(res => res.json())` is getting the response `res` from `fetch` and using the `json` method (more on this in a bit) to turn it into JSON. Then it's passing the JSON to the next line, `then(json => console.log(json))`, to be handled by that function.

The `fetch` API includes a *mixin*, or additional code, called [Body](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch#Body), which has functions that specialize in transforming the `body` of a request or response.

In an `XMLHttpRequest`, you would potentially have to `JSON.parse` the `responseText` data to turn it into JSON. The `Body` mixin takes that a step further, giving us handy ways to parse many formats, including JSON, plain text, and even blobs for binary or image data.

So calling `res.json()` in our `fetch` is just a nice shorthand for saying "give me the `body` of the response parsed as JSON".

GitHub's API uses [OAuth2](https://developer.github.com/v3/oauth/) for authorization. In a production setting, you would register an application with GitHub and receive an application ID and secret. This allows GitHub to track and monitor API access, and ensure that its users are protected by only granting authorization through registered apps.

```js
const token = 'YOUR_TOKEN_HERE'
fetch('https://api.github.com/user/repos', {
  headers: {
    Authorization: `token ${token}`
  }
}).then(res => res.json()).then(json => console.log(json));
```

We just pass the desired headers as part of a second options argument to `fetch` and we are in business. Easy as that!


**Top-Tip:** Don't ever give out your access token or store it in a publicly accessible place or a shared GitHub repository. We're just using these for learning purposes. In a production setting, user's access tokens would be stored securely in a database and not exposed to other people.

As you can see, `fetch` provides us with such a clean, low-maintenance way to fetch and work with resources. You may be wondering why you'd ever use XHR again.

Keep in mind that, while it is increasing, [browser support](http://caniuse.com/#feat=fetch) for `fetch` is still limited primarily to current versions of Chrome, Firefox, and Opera. So if you're supporting older browsers, don't let XHR and jQuery Ajax go just yet. They're still powerful and useful tools for creating dynamic applications.

### POST

While `GET` operations are straightforward, when we're building out full applications, we often need to use other HTTP verbs, such as `POST`, to write data as well as read it. Luckily, it's very easy to `POST` with `fetch` as well.

Let's look at an example of posting a new comment to a commit with the GitHub API. Replace the commit with a commit from one of your repositories, and use your token if you want to try this out.

```js
const token = 'YOUR_TOKEN_HERE';
const postData = {
  body: 'Great stuff'
};

fetch('https://api.github.com/repos/:your_ghname/:your_repo/commits/:sha/comments', {
  method: 'POST',
  body: JSON.stringify(postData),
  headers: {
    Authorization: `token ${token}`
  }
}).then(res => console.log(res));
```

Here we created an object called `postData` that we will pass as a JSON string using `JSON.stringify` in the request `body`. We're also setting the method to `'POST'`, and finally using our `Authorization` header like we did before, since any write action is going to require authorization.

All of these additional settings go in that `options` argument, which is just an object that we can pass as the second argument to `fetch`.

Finally, we can examine the response in our `then` function just the same as we did with a `GET` request.

**Top-tip:** Make sure you read the API documentation carefully! They will often specify which fields are required and which are optional, as well as the format of the request body. GitHub expects JSON data in the body, but another API might want form data (which you can create with `new FormData()` or XML or something else. Always read the docs!

- [`fetch()`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [GitHub API](https://developer.github.com/v3/)
- [Handlebars](http://handlebarsjs.com)

## Hello World
From the react website let's take the dev source files
Here's an example on [codepen](http://codepen.io/gaearon/pen/ZpvBNJ?editors=0010)
```html
<!DOCTYPE html>
<html>
    <head>
        <script src="https://fb.me/react-15.2.1.js"></script>
        <script src="https://fb.me/react-dom-15.2.1.js"></script>
        <title>My First React File</title>
    </head>
    <body>
        <div id='react-container'></div>
        <script>
            ReactDOM.render(
                React.createElement('div', null, 'Hello World'),
                document.getElementById('react-container'))
        </script>

    </body>
</html>
```

## React.createElement()
We'll run out mini-React application using Python Simple Server. From the directory of the project, in your terminal, *simply* run:

```
$ python -m SimpleHTTPServer
```

To learn more about Python Simple Server, check out [this blog post](http://www.linuxjournal.com/content/tech-tip-really-simple-http-server-python). 

We're going to use the React (and ReactDOM) libraries, so we should include those in our code. Run `npm install` to install dependencies. Now let's add the libraries by loading the right scripts in our `index.html` file:

```html
<script src="node_modules/react/dist/react.js"></script>
<script src="node_modules/react-dom/dist/react-dom.js"></script>
```

These should go in the body tag, after any content, but _before_ the `index.js` script. That file will contain our own code, so it expects React to already be loaded by that point!

Let's create a really basic page title in React using `React.createElement()` in the `index.js` file:

```js
const title = React.createElement('h1', {}, 'My First React Code');
```

Let's briefly talk about the arguments of `React.createElement()`.

- The first one is type of element we're creating, in this case an `<h1>` tag. This could also be another React component. If we're creating an HTML element, we pass in the name as a string, just like we did above. If we're creating a React component, we pass in the variable that the component is assigned to.
- The second argument is an object containing properties ('props' in React terms) that get passed to the component. Since we're just getting started with React, we won't use these just yet — but be aware that the second options serves this purpose.
- The third argument is the children of that component. This can be a quoted string like shown above, in which case the content will be interpreted as text. However, we can also pass in a reference to another component, allowing us to nest elements and components within each other.

Now that we have our element, it's time to render it to the page. We do this using `ReactDOM.render()`.
```js
ReactDOM.render(
  title,
  document.getElementById('main')
);
```
This takes two arguments: 

- the first one being the thing we want to render (our `title` element)
- the second one is a target DOM node to render things into.

### Nesting with const
Now we're going to add an element as a child, so we pass it by reference instead of using a string:
```js
const title = React.createElement('h1', {}, 'My First React Code');
const container = React.createElement('div', {}, title);

ReactDOM.render(
  container,
  document.getElementById('main')
);
```

Our `title` seems a little lonely though... Let's add a sibling! We'll create a `paragraph` element and then pass it as another child to our `container` children.

```js
const title = React.createElement('h1', {}, 'My First React Code');
const paragraph = React.createElement('p', {}, 'Writing some more HTML. Cool stuff!');
const container = React.createElement('div', {}, [title, paragraph]);

ReactDOM.render(
  container,
  document.getElementById('main')
);
```

Note how if we want to add multiple children, we use an _array_!

### Nesting inline
We can nest children as much as we want. We also don't need to store our elements in variables before using them, we can declare them inline as well (though the downside of this is less readable code):

```js
const list =
  React.createElement('div', {},
    React.createElement('h1', {}, 'My favorite ice cream flavors'),
    React.createElement('ul', {},
      [
        React.createElement('li', {}, 'Chocolate'),
        React.createElement('li', {}, 'Vanilla'),
        React.createElement('li', {}, 'Banana')
      ]
    ));

ReactDOM.render(list, document.getElementById('main'));
```
### Adding attributes
As mentioned before, we pass properties to an element using the second argument (an object, which we've left empty for now). Suppose we wanted to add some classes to make our ice cream flavors stand out.

The prop is called `className` because `class` is a _reserved keyword_ in JavaScript. Using reserved keywords as keys in an object is something that you should never do, since this can result in unexpected behavior. Instead, React expects the `className` prop instead, if we want to add a class to our element.

```js
const list =
  React.createElement('div', {},
    React.createElement('h1', {}, 'My favorite ice cream flavors'),
    React.createElement('ul', {},
      [
        React.createElement('li', { className: 'brown' }, 'Chocolate'),
        React.createElement('li', { className: 'white' }, 'Vanilla'),
        React.createElement('li', { className: 'yellow' }, 'Banana')
      ]
    ));

ReactDOM.render(list, document.getElementById('main'));
```

We can also add any other HTML attributes here, like `disabled`, `id`, and so on. These props are also used to pass in custom data to our components!

- [Raw React](http://jamesknelson.com/learn-raw-react-no-jsx-flux-es6-webpack/)

## Introducing JSX
JSX, or JavaScript as XML. So instead of creating all these createElement function calls, we're going to use tags right here in our JavaScript.
[Babel](https://babeljs.io) will take the JSX and turn it into createElement calls, so the browser can read it easily. Babel is a transpiler that will transpile JavaScript code. It works for JSX, and it also works for ES6 and beyond. So, instead of having to wait around to use syntax that's brand new, we can use it right away with the help of Babel.

Babel turns JSX code like
```html
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```
into compiled javascript like
```js
React.createElement(
  "ul",
  null,
  React.createElement(
    "li",
    null,
    "Item 1"
  ),
  React.createElement(
    "li",
    null,
    "Item 2"
  ),
  React.createElement(
    "li",
    null,
    "Item 3"
  )
);
```

We're using version 5.8. Version six, which is the newest version of Babel, isn't going to work as an in-browser transpiler. Let's copy this scr URI and paste it into another script tag. The process of in-browser transpiling means that all of our code that isn't ready for the browser is going to be transpiled at runtime. This is a slow process, so this isn't recommended for production, we're going to use webpack to include Babel as a module.

Note we add a `type="text/babel"` to our script tag.
```html
<!DOCTYPE html>
<html>
    <head>
        <script src="https://fb.me/react-15.2.1.js"></script>
        <script src="https://fb.me/react-dom-15.2.1.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.34/browser.js"></script>
        <title>My First React File</title>
    </head>
    <body>
        <div id='react-container'></div>
        <script type="text/babel">
            ReactDOM.render(<ul>
                    <li>item 1</li>
                    <li>item 2</li>
                    <li>item 3</li>
               </ul>,
                document.getElementById('react-container'))
        </script>

    </body>
</html>
```

Looking at this code, there are some important things to note. First of all, JSX is not a string — it's not in between quotes. Think of it as another type in JavaScript. Secondly, the parentheses containing the JSX are entirely optional, but recommended by convention.

It's important to note that using JSX is entirely optional. If writing HTML in your JavaScript feels like committing a mortal sin, it's okay to use React.createElement(). You'll be less productive, but at least you'll feel good about it!

**JSX always has one, and only one element** (that optionally has children, grandchildren, and so on): returning two values at once in JavaScript is conceptually impossible.

Another thing to note is that since we're still writing JS code, we need to avoid using keywords in our code. You might have noticed it already: we're setting HTML classes using the `className` attribute (or prop, in React terms), instead of `class`. This is because class is a reserved keyword in JavaScript! The same thing is true for the for label, which is another keyword in JS. If you want to use the HTML `for` attribute, you'd use `htmlFor` instead.

Babel also allows us to use new JS features before they are standardised and implemented in the browser, allowing us to write the most modern code we can, without worrying about browser support. Babel transpiles everything back down to JavaScript that _all_ browsers can understand. Neat!

[Browserify](http://browserify.org/) lets us require modules using [Node's version of the CommonJS module system](https://github.com/substack/browserify-handbook#node-packaged-modules). This means that we can include modules in our file (both local files as well as `node_modules` installed with `npm`). When compiling a file with Browserify, it'll check every file for stuff that it needs to import, and also include that code. In more technical terms, it's traversing the dependency tree and inlining those dependencies in our script. What we'll end up with is one big JS file that includes _all_ of our code, including any dependencies (like `React`, or our own components) in that file too. That way, we also only need to have one script reference in our HTML: the bundled version!

### Browserify

One of the benefits of Browserify is that it wraps every module in an [IIFE](https://developer.mozilla.org/en-US/docs/Glossary/IIFE), ensuring that no variable is global (unless you force it by setting something on `window`). This allows for pretty powerful modularization — we only export what we want other modules to use, and the rest is 'private' by default.

Let's see if we can get this to work! First of all, we'll need to install the `browserify` module:

```
$ npm install --save-dev browserify
```

Once that's done, we'll compile our code using the `browserify` command. We can do so by running the following:

```
$ browserify index.js -o bundle.js
```

The first argument is the path to our main JS file (that is responsible for importing all other files). Next, we tell it where we want the output bundle to go. In this case, that's the same directory, in a file called `bundle.js`. When you run the command above, chances are you'll run into an error that says `browserify` is not found. That's totally fine! It's not globally installed, but we don't need it to be, because we'll build our JS using an `npm` script. Taking a look at the `package.json` file, we'll find an object called `scripts` that contains various scripts we can run in our project. We'll add another script now that builds our JS:

```json
"scripts": {
  ... (other scripts)
  "bundle": "browserify index.js -o bundle.js",
}
```

Now, we'll run the script using `npm run bundle`. Wait, now it does work? Why's that? Well, `npm` knows `browserify` is a module that has an executable (or a binary), and links it in `node_modules/.bin/`. When `npm run` runs a script, it first checks if any command there can be found in that `.bin` folder, before using the system-wide commands. Handy!

Our `index.js` file is still empty at this point though. Let's practice writing modular code by creating a new file in `components/foo.js` (you'll also need to create the `components/` directory). In that file, we'll add this content:

```js
module.exports = 'I am a component!';
```

We'll get to what the `module.exports` stuff is in just a second. We can import this component in our `index.js` by using `require()` and assigning the result to a variable:

```js
const component = require('./components/foo');
```

Note that files are always referred to using a relative path (even if they are in the same directory). This way Node knows whether to look for a local module or one found in `node_modules`, or in the global modules. Adding the `.js`  extension is not required.

#### Named exports

Named exports allow us to export several things at once. This is useful for utility modules or libraries. Exporting several things at once is done by exporting an object when setting the value of `module.exports`.

```js
// In a file called `fruits.js`
module.exports = {
  apple: 'red',
  banana: 'yellow',
};

// In a file in the same directory
const fruits = require('./fruits');
console.log(fruits.apple); // prints 'red'

// In another file, also in the same directory
const apple = require('./fruits').apple;
console.log(apple); // prints 'red'
```

When using named exports, we can choose to either import the entire thing and then reference the keys on the exported object, or we can import one specific key. The last example can also be rewritten using ES2015 destructuring syntax:

```js
const { apple } = require('./fruits');
console.log(apple); // prints 'red'
```

#### Default Exports
A default export means we're exporting just one thing. This is useful for exporting components in their own file, since there's only one thing there: the component itself. Exporting one thing only is done by exporting a reference to what we want to export when setting the value of `module.exports`. You can also inline the value of what you want to export.

```js
// In a file called `Tweet.js`
const React = require('react');

class Tweet extends React.Component {
  render() {
    return (
      <div className="tweet">
        <img src="http://twitter.com/some-avatar.png" className="tweet__avatar" />
        <div className="tweet__body">
            <p>We're writing this tweet in JSX. Holy moly!</p>  
        </div>
      </div>
    );
  }
}

module.exports = Tweet;

// In a file in the same directory
const Tweet = require('./Tweet');

ReactDOM.render(
  <Tweet />,
  document.getElementById('main')
);
```

You'll mostly be using this method. It's important to correctly export your components, otherwise the tests can't access the code you've written, causing them to fail!

### Transforming JSX with Babel and Browserify

Now that we know how we can compile our bundle using Browserify, it's time to transform our JSX using Babel. Without the right transformer, Browserify won't know how to handle the JSX in our code and will fail, thinking the code we wrote has syntax errors in it.

To use a transformer, we pass the transformer name to the `browserify` command. First, we'll have to install some extra stuff:

```
$ npm install --save-dev babel-core babel-preset-es2015 babel-preset-react babelify
```

Let's quickly go through the modules we just installed. `babel-core` is Babel itself. Just by itself, Babel does absolutely _nothing_ to your files. You need to explicitly tell it what plugins to use. Luckily, there are transform _presets_ that form a collection of these separate plugins. That's what the `babel-preset-es2015` and `babel-preset-react` modules are for: they respectively transform our ES2015 and JSX code into JS that is understandable by browsers _today_. Lastly, we install `babelify` which is the transformer for Browserify.

We still need to let Babel know what presets we'd like to use. Babel reads its configuration from a `.babelrc` file in the project's root. This is a JSON file with Babel's options:

```json
{
  "presets": ["es2015", "react"]
}
```

Now all that's left to do is let Browserify know which transformer to use. In `package.json`, we'll update our `bundle` script to use the transformer:

```json
"scripts": {
  ... (other scripts)
  "bundle": "browserify index.js -t babelify -o bundle.js",
}
```

That should do the trick. Running `npm run bundle` should now correctly transpile our ES2015 and JSX code into one file called `bundle.js`. Success!

**Important: whenever writing JSX, _always_ import React (`const React = require('react');`). This is because Babel uses `React.createElement()` to compile our JSX down to JS. If `React` isn't found in that file, it'll throw an error!**

In the past, we've always loaded our source code in the HTML:

```html
<script src="index.js"></script>
```

Instead, now we'll reference our compiled (or bundled) code:

```html
<script src="bundle.js"></script>
```

That's the only script we need to add to our HTML file to make everything work. This bundle includes our source code as well as anything else we've imported in our code, like libraries (e.g. `React`, `ReactDOM` and others).

It's very important to know how this stuff works on a high level, because most of the React code nowadays is being compiled in one way or another — be it using Browserify, Webpack or something else. However, we don't want to create unnecessary busywork for you. Every lab from now on already has the bundling stuff set up for you. You just need to run `npm run bundle` any time you want to compile your changes and view them in the browser.

- [Browserify](https://github.com/substack/node-browserify)
- [Babel](http://babeljs.io/)
- [Babelify](https://github.com/babel/babelify)
- [JSX](https://facebook.github.io/react/docs/jsx-in-depth.html)

Babel is used to transform our ES2015 (and even newer) code to ES5 — the previous version of JavaScript that all browsers know and understand. Most of the ES2015 features are already present in browsers, but it's best to transpile your code using Babel anyway.

Plugins are small, composable dependencies that transform parts of our code. These plugins get applied to the code when compiling it with Babel, each doing their own little job and changing our code. For example, the `transform-es2015-destructuring` allows us to use ES2015 destructuring in our code:

```js
// Source code
const { foo, bar } = myLib;

// Gets transformed by the plugin to:
var _myLib = myLib;
var foo = _myLib.foo;
var bar = _myLib.bar;
```

Having small, separate [plugins](https://babeljs.io/docs/plugins/) like this allows us to tweak our configuration to our heart's desire. However, installing every single plugin just to write ES2015 and React code seems like such a hassle... Luckily, there's a thing in Babel called plugin presets! These dependencies are basically a collection of plugins that are grouped together. For example, to transform the code we're writing in this course, we use `babel-preset-es2015` and `babel-preset-react`.

We install them using `npm`, and then we use a file called `.babelrc` in the root of our project to configure Babel:

```json
{
  "presets": ["es2015", "react"],
  "plugins": ["an-example-plugin", "another-example-plugin"]
}
```

## Components
Components are small user interface elements that display data as it changes over time. These components can display data, handle state, and be nested inside of one another. React can be used for an entire site or just for smaller features, like a form, or an image carousel.

While HTML elements are the basic building blocks of an application (for example, a `<div>`), a React application usually consists of several React _components_ combined together. Unlike the simple HTML elements, React components are smarter and bigger. They allow you to add event handlers, store internal state, communicate with parent components, and so on.

Components names are always capitalized, it's a best practice.
Render is always required when we create a component, because it tells react what we want to render to the DOM.

### Component with `.createClass` (old school)
While this method of creating React components is outdated (in a sense), it's important to know what its syntax looks like. Most React tutorials and guides still use this syntax, so if you see it in the wild, now you know what it is!

```js
const Button = React.createClass({
  render() {
    return React.createElement('button', {}, 'Click me!');
  }
});
```

`React.createClass()` takes one argument: an object that is basically the specification of your component. The _only_ requirement for this specification is that your object has a `render()` method — everything else is optional. The reason for `render()` being required is, of course, that React needs to know _what_ it should show on our screen! More specifically, `render()` needs to return a _single_ child (that optionally has children of its own).

```html
<!DOCTYPE html>
<html>
    <head>
        <script src="https://fb.me/react-15.2.1.js"></script>
        <script src="https://fb.me/react-dom-15.2.1.js"></script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.34/browser.js"></script>
        <title>React Components</title>
    </head>
    <body>
        <div id='react-container'></div>
        <script type="text/babel">
            var MyComponent = React.createClass({
                render() {
                    return <div>
                        <h1>Hello World</h1>
                        <p>This is my first React component!</p>
                    </div>
                }
            })

            ReactDOM.render(<MyComponent />,
                document.getElementById('react-container'))

        </script>
    </body>
</html>
```

Another example: a component with some children without using JSX

```js
const ShoppingList = React.createClass({
  render() {
    return React.createElement('ul', {}, [
      React.createElement('li', {}, 'Bananas'),
      React.createElement('li', {}, 'Vanilla ice cream'),
      React.createElement('li', {}, 'Chocolate'),
    ]);
  }
});
```

Instead of passing in a string, we can also pass in a React component! For example, to create a `<div>` with two `Button` components, we would do the following:

```js
const nestedButtons = React.createElement('div', {}, [
  React.createElement(Button),
  React.createElement(Button),
]);
```

When React was first introduced, create class was the only way to create a component. Since then, two other techniques have emerged.

### Component with a ES6 class (new school)
With the introduction and widespread adoption of ES2015, we can create React component classes. We're extending the base `React.Component` class, and adding in any methods for our component specification. In this case, that's just the `render()` method.

```js
class Button extends React.Component {
  render() {
    return React.createElement('button', {}, 'Click me!');
  }
}
```

Using JSX we can do something like:

```js
class MyComponent extends React.Component {
    render() {
        return <div>
            <h1>Hello World</h1>
            <p>This is my first React component!</p>
        </div>
    }
}

ReactDOM.render(<MyComponent />,
    document.getElementById('react-container')) 
```    


Since createElement is just plain JavaScript, you can mix in loops, if statements, and anything else JavaScript allows.
You can also easily substitute in data stored in JSON.

```js
var contacts = [
  {key: 1, name: "James K Nelson", email: "james@jamesknelson.com", description: "Front-end Unicorn"},
  {key: 2, name: "Jim", email: "jim@example.com"},
  {key: 3, name: "Joe"},
]

var ContactItem = React.createClass({
  propTypes: {
    name: React.PropTypes.string.isRequired,
    email: React.PropTypes.string.isRequired,
    description: React.PropTypes.string,
  },

  render: function() {
    // I wrap mult-line return statements in parentheses to avoid the
    // inevitable bugs caused by forgetting that JavaScript will throw away
    // the final lines when possible. The parentheses are not strictly
    // necessary.
    return (
      React.createElement('li', {},
        React.createElement('h2', {}, this.props.name),
        React.createElement('a', {href: 'mailto:'+this.props.email}, this.props.email),
        React.createElement('div', {}, this.props.description)
      )
    )
  },
})

var contactItemElements = contacts
  .filter(function(contact) { return contact.email })
  .map(function(contact) { return React.createElement(ContactItem, contact) })

var rootElement =
  React.createElement('div', {}, 
    React.createElement('h1', {}, "Contacts"),
    React.createElement('ul', {}, contactItemElements)
  )

ReactDOM.render(rootElement, document.getElementById('react-app'))
```


### Component as a stateless functional component
A stateless functional component is just a simple function that returns react elements.

```js
const MyComponent = () => {
    return <div>
            <h1>Hello World</h1>
            <p>This is my first React component!</p>
        </div>
}

ReactDOM.render(<MyComponent />,
    document.getElementById('react-container'))
```


## Adding Properties
We can make our components more dynamic by adding properties. Sending properties to a component is very similar to adding attributes to HTML.

We’re going to wrap any JSX expression in `{curly braces}` and then we’re going to reference this on the React Props object.

```js
var MyComponent = React.createClass({
    render() {
        return <div>
            <h1>{this.props.text}</h1>
            <p>{this.props.children}</p>
        </div>
    }
})

ReactDOM.render(<div>
    <MyComponent text="Hello World">
    This is message 1
    </MyComponent>
    <MyComponent text="I am a Component">
    This is message 2
    </MyComponent>
    <MyComponent text="I have been reused!">
    This is message 3
    </MyComponent>
    </div>,
    document.getElementById('react-container'))
```

Props make it very very easy to display dynamic content which is what React is all about. It’s about displaying dynamic content and being able to reuse components.

## Handling Events
Inside of the render method it's always a best practice to wrap the JSX code into `()` to make sure we're free with line breaks.
In JSX we don't use the word `class` because class is a JS reserved word. Instead we use the JavaScript style `className` and use the Camel case.

```js
var Note = React.createClass({
    edit() {
        alert("Editing Note")
    },
    remove() {
        alert("Removing Note")
    },
    render() {
        return ( 
            <div className="note">
                <p>{this.props.children}</p>
                <span>
                  <button onClick={this.edit}>EDIT</button>
                  <button onClick={this.remove}>X</button>
                </span>
            </div>
            )
    }
})

ReactDOM.render(<Note>Hello World</Note>, 
    document.getElementById('react-container'))
```    

## State
When a component's state data changes, the render function will be called again to re-render the change in state.
`getInitialState()` is a React method enabling us to set an object with our initial values.
`onChange()` enables us to call a function on state change due to an action on our checkbox.

```js
var Checkbox = React.createClass({
    getInitialState() {
        return {checked: true}
    },
    handleCheck() {
        this.setState({checked: !this.state.checked})
    },
    render() {
        var msg
        if(this.state.checked) {
            msg = "checked"
        } else {
            msg = "unchecked"
        }
        return ( <div>
                <input type="checkbox" 
                       onChange={this.handleCheck}
                       defaultChecked={this.state.checked}/>
                <p>This box is {msg}</p>
            </div>)
    }
})
ReactDOM.render(<Checkbox/>, 
    document.getElementById('react-container'))
```    

Let's improve our note system
```js
var Note = React.createClass({
    getInitialState() {
        return {editing: false}
    },
    edit() {
        this.setState({editing: true})
    },
    save() {
        this.setState({editing: false})
    },
    remove() {
        alert("Removing Note")
    },
    renderForm() {
        return (
            <div className="note">
              <textarea></textarea>
              <button onClick={this.save}>SAVE</button>
            </div>
        )
    },
    renderDisplay() {
        return ( 
            <div className="note">
                <p>{this.props.children}</p>
                <span>
                  <button onClick={this.edit}>EDIT</button>
                  <button onClick={this.remove}>X</button>
                </span>
            </div>
            )
    },
    render() {
      return (this.state.editing) ? this.renderForm()
                                  : this.renderDisplay()

    }
})

ReactDOM.render(<Note>Hello World</Note>, 
    document.getElementById('react-container'))
```

## Using Refs
To grab data from our app we need to use a ref tag. Anytime you need to reach out to a form element or something where you can't access the value via Props and State, a Reference might be useful.

On our `renderForm()` method we add the ref tag
```js
renderForm() {
    return (
        <div className="note">
          <textarea ref="newText"></textarea>
          <button onClick={this.save}>SAVE</button>
        </div>
    )
}
```

Let's update our `save()` method
```js
save() {
    var val = this.refs.newText.value
    alert('Later we will save this value: ' + val)
    this.setState({editing: false})
},
```

## Props
Prop types are an optional feature, and serve as documentation about how we wish components to work, and what values you expect for them.

Let's create a new Board component and validate its props

```js
var Board = React.createClass({
    propTypes: {
        count: function(props, propName) {
            if(typeof props[propName] !== "number") {
                return new Error("the count must be a number")
            } 

            if(props[propName] > 100) {
                return new Error('Creating ' + props[propName] + ' notes is ridiculous')
            }
        }
    },
    render() {
        return (<div className='board'>
            {this.props.count}
            </div>)
    }
})

ReactDOM.render(<Board count={5000}/>, 
    document.getElementById('react-container'))
```

Let's update this code to put some dummy notes

```js
var Board = React.createClass({
    propTypes: {
        count: function(props, propName) {
            if(typeof props[propName] !== "number") {
                return new Error("the count must be a number")
            } 

            if(props[propName] > 100) {
                return new Error('Creating ' + props[propName] + ' notes is ridiculous')
            }
        }
    },
    getInitialState() {
        return {
            notes: [
              'Call Bob',
              'Email Sarah',
              'Eat lunch',
              'Finish proposal'
            ]
        }
    },

    render() {
        return (<div className='board'>
            {this.state.notes.map((note, i) => {
                return <Note key={i}>{note}</Note>
            })}
            </div>)
    }
})

ReactDOM.render(<Board count={10}/>, 
    document.getElementById('react-container'))
```  

## Update and Delete
The final code looks like

```js
var Note = React.createClass({
    getInitialState() {
        return {editing: false}
    },
    edit() {
        this.setState({editing: true})
    },
    save() {
        this.props.onChange(this.refs.newText.value, this.props.id)
        this.setState({editing: false})
    },
    remove() {
        this.props.onRemove(this.props.id)
    },
    renderForm() {
        return (
            <div className="note">
              <textarea ref="newText"></textarea>
              <button onClick={this.save}>SAVE</button>
            </div>
        )
    },
    renderDisplay() {
        return ( 
            <div className="note">
                <p>{this.props.children}</p>
                <span>
                  <button onClick={this.edit}>EDIT</button>
                  <button onClick={this.remove}>X</button>
                </span>
            </div>
            )
    },
    render() {
      return (this.state.editing) ? this.renderForm()
                                  : this.renderDisplay()

    }
})

var Board = React.createClass({
    propTypes: {
        count: function(props, propName) {
            if(typeof props[propName] !== "number") {
                return new Error("the count must be a number")
            } 

            if(props[propName] > 100) {
                return new Error('Creating ' + props[propName] + ' notes is ridiculous')
            }
        }
    },
    getInitialState() {
        return {
            notes: [
              {id: 0, note: 'Call Bob'},
              {id: 1, note: 'Email Sarah'},
              {id: 2, note: 'Eat Lunch'},
              {id: 3, note: 'Finish proposal'}
            ]
        }
    },
    update(newText, id) {
        var notes = this.state.notes.map(
            note => (note.id !== id) ?
               note : 
                {
                    ...note, 
                    note: newText
                }
            )
        this.setState({notes})
    },
    remove(id) {
        var notes = this.state.notes.filter(note => note.id !== id)
        this.setState({notes})
    },
    eachNote(note) {
        return (<Note key={note.id}
                      id={note.id}
                      onChange={this.update}
                      onRemove={this.remove}>
                  {note.note}
                </Note>)
    },
    render() {
        return (<div className='board'>
                   {this.state.notes.map(this.eachNote)}
                </div>)
    }
})

ReactDOM.render(<Board count={10}/>, 
    document.getElementById('react-container'))
```

We're passing property data up and down the tree from parent to child, and child to parent.
Note we have a `key` property: each child in an array, or iterator should have a unique key property. This is to ensure that the state and the identity of our components is maintained through multiple renders.

## Create 
We use the spread operator from ES6, that takes whatever is in the state of notes and makes those the first items in the array. Then we're adding a new item in the array: an object with an ID and note text.

Inside of our Board component let's add a button to add a note

```js
render() {
    return (<div className='board'>
               {this.state.notes.map(this.eachNote)}
               <button onClick={() => this.add('New Note')}>+</button>
            </div>)
}
```

In our Board component let's now make sure we have the method to handle the `onClick`: the `.add()` function.
We also make sure to create an Id for each note by creating a `nextId()` function.

```js
...
getInitialState() {
    return {
        notes: []
    }
},
nextId() {
    this.uniqueId = this.uniqueId || 0
    return this.uniqueId++
},
add(text) {
    var notes = [
        ...this.state.notes,
        {
            id: this.nextId(),
            note: text
        }
    ]
    this.setState({notes})
}
```

## Using Props
Props allow us to pass values into our components. These values can be anything: a string, an array, functions, and so on. They give us the opportunity to make our components more dynamic, and a **lot more** reusable. For example, say we have a `<MovieCard />` component. A movie has a title, a poster image, and many other attributes (or **prop**erties!). Our component would kind of look like this, with _hardcoded_ data:

```js
import React from 'react';
import ReactDOM from 'react-dom';

class MovieCard extends React.Component {
  render() {
    return (
      <div className="movie-card">
        <img src="http://image.tmdb.org/t/p/w342/kqjL17yufvn9OVLyXYpvtyrFfak.jpg" alt="Mad Max: Fury Road" />
        <h2>Mad Max: Fury Road</h2>
        <small>Genres: Action, Adventure, Science Fiction, Thriller</small>
      </div>
    );
  }
}

ReactDOM.render(
  <MovieCard />,
  document.getElementById('main')
);
```

To pass props to a component, you add them as attributes when you render them:

```js
<MyComponent propName={propValue} />
```

The value of a prop is passed in through curly braces, like above.

Armed with that knowledge, let's update our `ReactDOM.render()` call to include the data for the Mad Max movie in our props:

```js
ReactDOM.render(
  <MovieCard
    title="Mad Max: Fury Road"
    poster="http://image.tmdb.org/t/p/w342/kqjL17yufvn9OVLyXYpvtyrFfak.jpg"
    genres={['Action', 'Adventure', 'Science Fiction', 'Thriller']} 
  />,
  document.getElementById('main')
);
```

Notice how we passed in the genres as an inline array? We could also pass in variables instead, like this:

```js
const madMaxGenres = ['Action', 'Adventure', 'Science Fiction', 'Thriller'];

ReactDOM.render(
  <MovieCard
    title="Mad Max: Fury Road"
    poster="http://image.tmdb.org/t/p/w342/kqjL17yufvn9OVLyXYpvtyrFfak.jpg"
    genres={madMaxGenres} 
  />,
  document.getElementById('main')
);
```

Now that we've passed in our props, let's change our hardcoded data in the `render()` method to make use of the props we pass in instead. Props in a component can be accessed through `this.props` in the `render()` method (and most other component methods):

```js
class MovieCard extends React.Component {
  render() {
    return (
      <div className="movie-card">
        <img src={this.props.poster} alt={this.props.title} />
        <h2>{this.props.title}</h2>
        <small>Genres: {this.props.genres.join(', ')}</small>
      </div>
    );
  }
}
```

What if we didn't have a poster image for a movie? Ideally, we'd have a default poster image for that instead. Instead of passing in that default poster image in case we don't have one, we can tell update our `MovieCard` component to use a default value instead, if the `poster` prop was not provided. To do that, we add the `propTypes` property to our `MovieCard` class:

```js
class MovieCard extends React.Component {
  render() {
    // ... The render stuff from before
  }
}

MovieCard.defaultProps = {
  poster: 'http://i.imgur.com/bJw8ndW.png'
};
```

Now, whenever we omit the `poster` prop, or if it's undefined, the `MovieCard` component will use this default prop instead.

If we were still writing our components using `React.createClass()` instead of the ES2015 way, this is how we would add default props to that component:

```js
const MovieCard = React.createClass({
  getDefaultProps() {
    return {
      poster: 'http://i.imgur.com/bJw8ndW.png'
    };
  },
  render() {
    // ... The render stuff from before
  }
})
```

Note that the order of the method definitions does _not_ matter: `getDefaultProps()` could be added below the `render()` method too. Generally, though, it's best to keep your `render()` method last when declaring methods, and keeping the code for the initial state and props for the component all the way up top.

- [React Default Prop Values](https://facebook.github.io/react/docs/reusable-components.html#default-prop-values)
- [Babel: transform-class-properties](http://babeljs.io/docs/plugins/transform-class-properties/)

### PropTypes
Let's pretend we're running a super modern ice cream store where orders are done through the computer and shown in the browser using React. This means that we'd need some kind of `<Order />` component to represent all the delicious items that people have ordered.

We'll take a moment to stop and think about how we want to represent our order. Which data (i.e.) props do we need? What are the options? Are some of them required? Let's list them:

- `cone` — a boolean indicating if the ice cream should be in a cone, defaults to true
- `size` — a string to indicate the size of the order, defaults to `'regular'`
- `scoops` — an array of ice cream flavors
- `orderInfo` — an object containing data about the ice cream order

Our `<Order />` component would roughly look like this:

```js
class Order extends React.Component {
  render() {
    return (
      <div className="order">
        <ul>
          <li>{this.props.cone ? 'Cone' : 'Cup'}</li>
          <li>{this.props.size}</li>
          <li>{this.props.scoops.length} scoops: {this.props.scoops.join(', ')}</li>
          <li>Ordered by {this.props.orderInfo.customerName} at {this.props.orderInfo.orderedAt}.</li>
        </ul>
      </div>
    );
  }
}
```

Now that we know what our component will look like, let's add our default props (see the props list above). Afterwards, we'll start adding PropTypes to validate all the props being passed in. We do so by setting the `propTypes` property (which is an object) on the `Order` class:

```js
class Order extends React.Component {
  render() {
    // ...
  }
}

Order.defaultProps = {
  cone: true,
  size: 'regular'
};

Order.propTypes = {
  cone: React.PropTypes.bool,
  size: React.PropTypes.string,
  scoops: React.PropTypes.arrayOf(React.PropTypes.string).isRequired,
  orderInfo: React.PropTypes.object.isRequired
};
```

### Defining "shape" for object PropTypes
We told the `orderInfo` prop to expect an object, but can we be more specific? We don't just need any object, we want an object with the properties (`customerName` and `orderedAt`) that we care about!

Good news: we can! Using `React.PropTypes.shape`, we can tell our component to expect the prop to have a certain _shape_:

```js
Order.propTypes = {
  cone: React.PropTypes.bool,
  size: React.PropTypes.string,
  scoops: React.PropTypes.arrayOf(React.PropTypes.string).isRequired,
  orderInfo: React.PropTypes.shape({
    customerName: React.PropTypes.string.isRequired,
    orderedAt: React.PropTypes.number.isRequired // We're using UNIX timestamps here
  }).isRequired
};
```

- [PropTypes reference](https://facebook.github.io/react/docs/reusable-components.html#prop-validation)

Example: 
```js
// const React = require('react');
import React from 'react';

class Product extends React.Component {
  render(){
    return (
      <div className="product">
        <p>Name: {this.props.name}</p>
        {this.props.producer ? <small>{this.props.producer}</small> : null}
        <p>{this.props.hasWatermark ? 'Watermarked' : 'Not watermarked'}</p>
        <p>Weight: {this.props.weight}</p>
      </div>
    )
  }
};

Product.defaultProps = {
  hasWatermark: false
};

Product.propTypes = {
  name: React.PropTypes.string.isRequired,
  producer: React.PropTypes.string,
  hasWatermark: React.PropTypes.bool,
  color: React.PropTypes.oneOf(['white', 'eggshell-white', 'salmon']).isRequired,
  weight: (props, propName) => {
    const weight = props[propName];

    if (weight === undefined) {
      return new Error('The `weight` prop is required.');
    }

    if (isNaN(weight)) {
      return new Error('The `weight` prop is not a number.');
    }

    const isValidWeight = weight > 80 && weight < 300;

    if (!isValidWeight) {
      return new Error('The `weight` prop should range between 80 and 300.');
    }
  },

  // name: a string — required
  // producer: a string — optional
  // hasWatermark: a boolean — optional, defaults to false
  // color: a string — required, can only be 'white', 'eggshell-white' or 'salmon'
  // weight: a number — required, ranges between 80 and 300
};

module.exports = Product;
```

## React this.props.children
In React, a component can have one, many or no children. Consider the following code:

```js
<VideoPlayer>
  <VideoHeader>
    <h1 className="video-title">The Simpsons</h1>
  </VideoHeader>
  <VideoControls />
</VideoPlayer>
```

In this example, the `VideoPlayer` has two children: `VideoHeader` and `VideoControls`. `VideoHeader`, in turn, has one child: the `h1` with the title content. `VideoControls`, on the other hand, has no children.

Why is this important? As you can see above, we can use children to compose our interface. For a more concrete example, let's say we're creating a `<Panel>` component that allows us to add content to it. Using a panel might look a little like this:

```js
<Panel title="Browse for movies">
  <div>Movie stuff...</div>
  <div>Movie stuff...</div>
  <div>Movie stuff...</div>
  <div>Movie stuff...</div>
</Panel>
```

As you can see, we're adding content *inside* of the `<Panel>` tags. Now, how do we render that content in our component? We access it through **`this.props.children`** — a special prop that is passed to components automatically.

```js
export default class Panel extends React.Component {
  render() {
    return (
      <div className="panel">
        <div className="panel-header">{this.props.title}</div>
        <div className="panel-body">{this.props.children}</div>
      </div>
    );
  }
}
```

Since `this.props.children` can have one element, multiple elements, or none at all, its value is respectively `undefined`, a single child node, or an array of child nodes. Sometimes, we want to transform our children before rendering them — for example, to add additional props to every child. If we wanted to do that, we'd have to take the possible types of `this.props.children` into account. For example, if there is only one child, we can't map it.

### React.Children
Luckily, React provides us with a clean API to handle of looping children. If there is only one child (or none at all), it won't throw a fuss — it'll handle things for us nicely in the background.

Let's say we have a list of `Movie` components that are nested inside of a `MovieBrowser` component:

```js
<MovieBrowser>
  <Movie title="Mad Max: Fury Road" />
  <Movie title="Harry Potter & The Goblet Of Fire" />
</MovieBrowser>
```

Now, let's assume for some reason that we need to pass down an extra prop to our children — the props would like to know if they are being played or not. Our `MovieBrowser` component would look something like this, before we added the prop:

```js
export default class MovieBrowser extends React.Component {
  render() {
    const currentPlayingTitle = 'Mad Max: Fury Road';
    
    return (
      <div className="movie-browser">
        {this.props.children}
      </div>      
    );
  }
}
```

Now let's add in our `isPlaying` prop to the children of `MovieBrowser`:

```js
export default class MovieBrowser extends React.Component {
  render() {
    const currentPlayingTitle = 'Mad Max: Fury Road';
    const childrenWithExtraProp = React.Children.map(this.props.children, child => {
      return React.cloneElement(child, {
        isPlaying: child.props.title === currentPlayingTitle
      });
    });
    
    return (
      <div className="movie-browser">
        {childrenWithExtraProp}
      </div>      
    );
  }
}
```

`React.Children.map` has two parameters: the first one is the children themselves, and the second one is a function that transforms the value of the child. In this case, we're adding an extra prop. We do that using `React.cloneElement`. As the first argument we pass in the child component itself, and as the second argument, we pass in any additional props. Those additional props get merged with the child's existing props, overwriting any props with the same key.

As another example, let's say we want to wrap our components in an extra `div` with a special class. We also want to display the total amount of children.

```js
export default class SomeComponent extends React.Component {
  render() {
    const childrenWithWrapperDiv = React.Children.map(this.props.children, child => {
      return (
        <div className="some-component-special-class">{child}</div> 
      );
    });
    
    return (
      <div className="some-component">
        <p>This component has {React.Children.count(this.props.children)} children.</p>
        {childrenWithWrapperDiv}        
      </div>      
    );
  }
}
```

- [Explanation on Children](https://facebook.github.io/react/docs/multiple-components.html#children)
- [React.Children API](https://facebook.github.io/react/docs/top-level-api.html#react.children)

## State
Let's quickly talk about what _state_ is in React. State is basically data that is mutated in your component. Like with any state, this state can also **change**. That's an important part: while a component can't change its own props, it _can_ change its state.

State is used to handle several things in your component:

- Interactivity (e.g. changing data when a user clicks a button)
- Fetching remote data (remote data is, by definition, not available right away when the component is mounted — state gives us a way of updating the component once that data arrives)
- Reacting to the passing of time (i.e. setting an interval or timeout)

The best way to figure out if data should go in props or state is to ask ourselves _'Will this data ever change?'_. If not, it's a prop. If it will, it should go in state! Keep in mind that whenever props _and/or_ state change, the component will run its `render()` method again.

### Setting Initial State
Let's say we have a `<ToggleButton />` component. A toggle button has an on and off state. Using props for that value wouldn't work, since we can't actually change our props! Let's use state for this instead. We'll assume that the default state of this component is to be in the _off_ state. Let's call that state property `isEnabled`. Setting the initial state is done in the `constructor` of our ES2015 class component:

```js
class ToggleButton extends React.Component {
  constructor() {
    super();
    
    this.state = {
      isEnabled: false
    };
  }

  render() {
    return (
      <div className="toggle-button">I am toggled {this.state.isEnabled ? 'on' : 'off'}.</div>
    );
  }
}
```

If, for some reason, we were still using `React.createClass()`, we would add a method called `getInitialState()` that returns our state object:

```js
const ToggleButton = React.createClass({
  getInitialState() {
    return {
      isEnabled: false
    };
  },

  render() {
    return (
      <div className="toggle-button">I am toggled {this.state.isEnabled ? 'on' : 'off'}.</div>
    );
  }
});
```

Our component would show 'I am toggled off.' on the screen, since the initial state has set the `isEnabled` property to `false`. Not very exciting yet, but we'll get there!

### Keep state slim!
It's important to try and keep your state **as small as possible**. You should strive for a minimal amount of data in your state and compute the rest. For example, let's say we have a component `<Address />` that takes in two props: the `street` and the `city`. We'll add those two together to show the user a complete address. An example of having computed data in your state would be this:

```js
class Address extends React.Component {
  constructor(props) {
    super();
    
    this.state = {
      fullAddress: `${props.street}, ${props.city}`
    }
  }

  render() {
    return (
      <div className="address">{this.state.fullAddress}</div>
    );
  }
}
```

While this is all perfectly valid React code, storing computed values in your state (in this case, `fullAddress`) should be avoided. There's no good reason for the full address to go into our state, since we're just using props to 'compute' the full address. Instead, we should use the component's props directly:


```js
class Address extends React.Component {
  render() {
    return (
      <div className="address">{this.props.street}, {this.props.city}</div>
    );
  }
}
```

While component state is a very powerful feature, it should be used as sparingly as possible. State is hard to manage and can be very easy to lose sight of.

- [Official React docs on state](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#components-are-just-state-machines)
- [Props vs. state](https://github.com/uberVU/react-guide/blob/master/props-vs-state.md)
- [Props in getInitialState Is an Anti-Pattern](https://facebook.github.io/react/tips/props-in-getInitialState-as-anti-pattern.html)

Another example

```js
import React from 'react';

class Bomb extends React.Component {
  constructor(props) {
    super();

    this.state = {
      secondsLeft: props.initialCount
    }
  };

  render() {
    const message = this.state.secondsLeft === 0 ? 'Boom!' : `${this.state.secondsLeft} seconds left before I go boom!`;

    return(
      <div>{message}</div>
    )
  };
}

module.exports = Bomb;
```

## React Event System
React has its own event system with special event handlers called `SyntheticEvent`. The reason for having a specific event system instead of using native events is cross-browser compatibility.

It's important to keep in mind that they are the  _exact same events_, just implemented in a consistent way! That means these events also have methods like `preventDefault()`, `stopPropagation()`, and so on.

We attach event handlers to an element much like how we'd add a prop. The handler name is always comprised of `on`, and the event name itself — for example `click`. These are joined together and camel-cased, so if we wanted to add a click handler, we'd call the prop `onClick`. This prop takes a function as a value — it can either be a reference to a method on the class (like our `tickle()` method), or an inline function. Most of time, we'll use a function reference. It looks like this:

```js
class Tickler extends React.Component {
  constructor() {
    super();
    
    this.tickle = this.tickle.bind(this);
  }
  
  tickle() {
    console.log('Tee hee!');
  }

  render() {
    return (
      <button onClick={this.tickle}>Tickle me!</button>
    );
  }
}
```

The important bit here is the `constructor()`, where we're binding our `tickle()` method. Note that this is _not_ required in this example (since we're not accessing the component's `this`). Realistically, all methods in a React component class will almost always use `this` in one way or another, so it's a good idea to get the binding out of the way, even if you don't explicitly need it yet.

There are a lot of event handlers we can add to an element, for example `onKeyUp`, `onMouseDown`, `onFocus`, `onSubmit`, and many more. Check out the [complete list of supported events](https://facebook.github.io/react/docs/events.html#supported-events) to see what else you can play around with!

- [React Synthetic Events](https://facebook.github.io/react/docs/events.html)
- [Supported-events](https://facebook.github.io/react/docs/events.html#supported-events)

### Accessing event data
Let's take a deeper look at the actual event being passed through. A `SyntheticEvent` event has all of its usual properties and methods. These includes its type, target, mouse coordinates, and so on. As a reminder, we add an event handler to a component, and then we can use the event's data like this:

```js
export default class Clicker extends React.Component {
  constructor() {
    super();
    
    this.handleClick = this.handleClick.bind(this);
  }
  
  handleClick(event) {
    console.log(event.type); // prints 'click'
  }

  render() {
    return (
      <button onClick={this.handleClick}>Click me!</button>
    );
  }
}
```

For example, if we wanted to get the target of an event, we'd use `event.target`. If we want to prevent a default action whenever an event happens, we call `event.preventDefault()`. This is all super similar to regular browser events and should feel very familiar!

### Event Pooling
Event pooling means that whenever an event fires, its event data (an object) is sent to the callback. The object is then immediately cleaned up for later use. This is what we mean by 'pooling': the event object is in effect being sent back to the pool for use in a later event. It's something that trips up a lot of people, and you might have run into it yourself when inspecting `SyntheticEvent` in the browser.

If we click the button of our `Clicker` component and then inspect the logged out object in our console, we notice that all properties are `null` again. By the time we inspect the object in our browser, the event object will have already been returned to the pool. This means that we can't access event data in an asynchronous manner by saving it in the state, or running a timeout and _then_ accessing the event again.

You usually don't need to access your event data in an asynchronous manner like described above, but if you do, there are two options: you either store the data you need in a variable (e.g. `const target = event.target`), _or_ we can make the event persistent by calling that method: `event.persist()`.

```js
import React from 'react';

class DelayedButton extends React.Component {
  constructor(){
    super();

    this.handleClick = this.handleClick.bind(this);
  }

  handleClick(event){
    event.persist();
    setTimeout(() => {
      this.props.onDelayedClick(event);
    }, this.props.delay);
  }

  render(){
    return (
      <button onClick={this.handleClick}></button>
    )
  }
}

module.exports = DelayedButton;
```

## Updating State
While a React component can have initial state, the real power is in updating its state — after all, if we didn't need to update the state, the component shouldn't _have_ any state. State is only reserved for data that _changes_ in our component and is visible in the UI.

Instead of directly modifying the state using `this.state`, we use `this.setState()`. This is a function available to all React components, and allows us to let React know that the component state has changed. This way the components knows it should re-render, because its state has changed and its UI will most likely also change. 

Using a setter function like this is very performant. While other frameworks like Angular.js use "dirty checking" (continuously checking for changes in an object) to see if a property has changed, React _already knows_ because we use a built-in function to let it know what changes we'd like to make!

For example, let's say we have a component with a button, and a bit of text to indicate whether that button has been pressed yet. To update our state, we use `this.setState()` and pass in an object. This object will get merged with the current state. When the state has been updated, our component re-renders automatically.

```js
class ClickityClick extends React.Component {
  constructor() {
    super();
    
    // Define the initial state:
    this.state = {
      hasBeenClicked: false,
    };
    
    this.handleClick = this.handleClick.bind(this);
  }
  
  handleClick() {
    this.setState({
      hasBeenClicked: true,
    });
  }

  render() {
    return (
      <div>
        <p>I have {this.state.hasBeenClicked ? 'not' : null} been clicked yet!</p>
        <button onClick={this.handleClick}>Click me!</button>
      </div>
    );
  }
}
```

### How State gets merged
When updating state, we don't have to pass in the entire state, just the property we want to update. For example, consider the following state for our component:

```
{
  hasBeenClicked: false,
  currentTheme: 'blue',
}
```

If we updated the `hasBeenClicked` using `this.setState()` like we did above, it would _merge_ the new state with the existing state, resulting in this new state:

```
{
  hasBeenClicked: true,
  currentTheme: 'blue',
}
```

One super important thing to note is that it only merges things on the first level.

A deep merge means that the merge will happen recursively, leaving any unchanges properties intact. For example, consider the following code sample:

```js
const house = {
  kitchen: {
    cabinets: 'white',
    table: {
      legs: 4
    }
  }
};

// Note: `deepMerge()` isn't actually a built-in function
const updatedHouse = deepMerge(house, {
  kitchen: {
    table: {
      legs: 8
    }
  }
});
```

Deeply merging like this would only update the `legs` property with a value of `8`, but the rest of the `kitchen` and `house` objects' structure will remain intact.

We can also use `Object.assign()` by merging the `addressInfo` object with the new data ourselves:

```
{
  theme: 'blue',
  addressInfo: {
    street: null,
    number: null,
    city: null,
    country: null
  },
}
```

We can update the city like so:

```js
this.setState({
  addressInfo: Object.assign({}, this.state.addressInfo, {
    city: 'New York City',
  }),
});
```

Another example
```js
const React = require('react');

class YouTubeDebugger extends React.Component {
  constructor() {
    super();

    this.state = {
      errors: [],
      user: null,
      settings: {
        bitrate: 8,
        video: {
          resolution: '1080p'
        }
      }
    };

    this.handleChangeBitrate = this.handleChangeBitrate.bind(this);
    this.handleChangeResolution = this.handleChangeResolution.bind(this);
  }

  handleChangeBitrate() {
    this.setState({
      settings: Object.assign({}, this.state.settings, {
        bitrate: 12
      }),
    });
  }

  handleChangeResolution() {
    this.setState({
      settings: Object.assign({}, this.state.settings, {
        video: Object.assign({}, this.state.settings.video, {
          resolution: '720p'
        })
      }),
    });
  }

  render() {
    return (
      <div>
        <button className="bitrate" onClick={this.handleChangeBitrate}>Change bitrate</button>
        <button className="resolution" onClick={this.handleChangeResolution}>Change resolution</button>
      </div>
    );
  }
}

module.exports = YouTubeDebugger;
```

### Setting state is not synchronous
One thing to keep in mind is that setting state is _not_ synchronous. For all intents and purposes, it might seem that way, since our components update right away. State updates, however, are _batched_ internally and then executed simultaneously whenever React feels it's appropriate. This might result in some unexpected behavior. Going back to our `ClickityClick` component above, let's log the state after we've set it using `this.setState()`:

```js
handleClick() {
  this.setState({
    hasBeenClicked: true,
  });
  console.log(this.state.hasBeenClicked); // prints false
}
```

The console output says `false`... but we just set it to `true`! What is this madness?

State changes, however instant they might appear, happen _asynchronously_. If we want to access our new state after it has been updated, we can optionally add a callback as a second argument to the `this.setState()` function. This callback will fire once the state has been updated, ensuring that `this.state` is now the new, shiny updated state. In code:

```js
handleClick() {
  this.setState(
    { hasBeenClicked: true },
    function () {
      console.log(this.state.hasBeenClicked); // prints true
    }
  );
}
```

### State changes vs. prop changes
It's important to note the difference between changes in state and changes in props. Changes in state and/or props will both trigger a re-render of our React component. However, changes in state can only happen _internally_ due to components changing their own state. Changes in props can only happen _externally_, due to changes in prop values being passed in.

- [Transferring props](https://facebook.github.io/react/docs/transferring-props.html)
- [Component API](https://facebook.github.io/react/docs/component-api.html)

## Components lifecycle
The component lifecycle provides hooks for creation, lifetime, and teardown of components. These methods allow you to do things like add libraries, load data, and more at very specific times.

- `getInitialState()` is going to be called once and will set the default for a state
- `componentWillMount()` is called right before the render, and it's the last chance to effect state prior to the render
- `render()`, that is the only required method
- `componentDidMount()` is going to fire right after a successful render

The component lifecycle also provides methods for updating

- `componentWillReceiveProps()` gives the opportunity to change the object and effect state
- `shouldComponentUpdate()` and `componentWillUpdate()` are invoked right before rendering and are used for optimization
- `render()` method again as it is part of the updating lifecycle as well
- `componentDidUpdate()` fires right after everything in the DOM has been updated

`componentWillUnmount()` is called right before the component is unmounted, to clean up DOM elements and invalidate timers. When it is called on the parent, all of the children are unmounted as well.

```js
var Box = React.createClass({
    componentWillMount() {
        alert('Component is about to mount')
    },
    componentDidMount() {
        alert('Component just mounted')
    },
    render() {
        return <div id='myDiv'></div>
    }
})
ReactDOM.render(<Box />, 
    document.getElementById('react-container'))

var getRidOfBox = document.getElementById('myDiv')
getRidOfBox.onclick = function() {
    ReactDOM.unmountComponentAtNode(
        document.getElementById('react-container'))
        alert('component is unmounted')
}
```

Another great example is `getDefaultProps()`, that provides us a life cycle method for initializing default properties for our components.

```js
var Box = React.createClass({
    getDefaultProps() {
        return {
            backgroundColor: 'purple',
            height: 200,
            width: 200
        }
    },
    render() {
        return (<div id='myDiv'>
                    <div style={this.props}></div>
                    <section style={this.props}></section>
                </div>)
    }
})
```

## Forms
Forms in React are fairly straight-forward and similar to regular HTML elements, albeit with a few changes that we need to be aware of.

Form elements include `<input>`, `<textarea>`, `<select>`, and `<form>` itself. When we talk about inputs in this lesson, we broadly mean the form elements (`<input>`, `<textarea>`, `<select>`) and not always specifically just `<input>`.

To control the value of these inputs, we use a prop specific to that type of input:

- For `<input>` and `<textarea>`, we use `value`
- For `<input type="checkbox">` and `<input type="radio">`, we use `checked`
- For `<option>`, we use `selected`

To listen for changes to the value of an input, we simply pass in the `onChange` prop with a callback function. Default values are set using either the regular value prop (`value`, `checked`, ...) _or_ the `defaultValue`/`defaultChecked` prop. This depends on if we're using an uncontrolled or controlled component. 

React provides us with two ways of setting and getting values in form elements. These two methods are called _uncontrolled_ and _controlled_ components. The quickest way to check if a component is controlled or uncontrolled is to check for `value` or `defaultValue`. If the component has a `value` prop, it is controlled (the state of the component is being controlled by React). If it doesn't have a `value` prop, it's an uncontrolled component. Uncontrolled components can optionally have a `defaultValue` prop to set its initial value. These two props (`value` and `defaultValue`) are _mutually exclusive_: a component is either controlled or uncontrolled, but it cannot be both.

### Uncontrolled component
In uncontrolled components, the state of the component's value is kept in the DOM itself — in other words, the form element in question (e.g. an `<input>`) has its _own internal state_. To retrieve that value, we would need direct access to the DOM component that holds the value, _or_ we'd have to add an `onChange` handler.

To set an initial value for the element, we'd use the `defaultValue` prop.

We can't use the `value` prop for this: we're not using state to explicitly store its value, so the component would never update its value anymore (since we're rendering the same thing).

### Controlled component
In controlled components, we explicitly set the value of a component, and update that value in response to any changes the user makes to the value of that component. That might sound a little wonky, but when you see the code, it'll become much clearer:

```js
class ControlledInput extends React.Component {
  constructor() {
    super();
    
    this.handleChange = this.handleChange.bind(this);
    
    this.state = {
      value: '',
    };
  }
  
  handleChange(ev) {
    this.setState({
      value: ev.target.value,
    });
  }

  render() {
    return (
      <input type="text" value={this.state.value} onChange={this.handleChange} />
    );
  }
}
```

As you can see, we can easily define the initial value by setting the initial `value` property on the state to whatever we want. 

Using a controlled component is the preferred way to do things in React — it allows us to keep _all_ component state in the React state, instead of relying on the DOM to retrieve the element's value through its internal state. Whenever our state\ changes, the component re-renders, rendering the input with the new updated value. If we don't update the state, our input wouldn't update when the user would type. In other words, we need to update our input's state _programatically_.

It might seem a little counterintuitive that we need to be so verbose, but this actually opens the door to additional functionality. For example, let's say we want to write an input that only takes in a number (let's pretend there is no `<input type="number">`). We can now validate the data the user enters _before_ we set it on the state, allowing us to block any invalid values. If the input is invalid, we simply avoid updating the state, preventing the input from updating. We could optionally set another state property (for example, `isInvalidNumber`). Using that state property, we can show an error in our component to indicate that the user tried to enter an invalid value.

If we tried to do this using an uncontrolled component, the input would be entered regardless, since we don't have control over the internal state of the input. In our `onChange` handler, we'd have to roll the input back to its previous value, which is pretty tedious!

- [React Forms](https://facebook.github.io/react/docs/forms.html)

```js
const React = require('react');

class TwitterMessage extends React.Component {
  constructor() {
    super();

    this.handleChange = this.handleChange.bind(this);

    this.state = {
      tweet: ''
    };
  }

  handleChange(event) {
    this.setState({
      tweet: event.target.value
    })
  }

  render() {
    return (
      <div>
        <strong>Your message:</strong>
        <input type="text" value={this.state.tweet} onChange={this.handleChange} />
        <p>{this.props.maxChars - this.state.tweet.length} characters remanining.</p>
      </div>
    );
  }
}

module.exports = TwitterMessage;
```

Another example
```js
const React = require('react');

class LoginForm extends React.Component {
  constructor() {
    super();

    this.handleUsernameChange = this.handleUsernameChange.bind(this);
    this.handlePasswordChange = this.handlePasswordChange.bind(this);
    this.handleSubmit = this.handleSubmit.bind(this);

    this.state = {
      username: '',
      password: ''
    };
  }

  handleUsernameChange(event){
    this.setState({
      username: event.target.value
    })
  }

  handlePasswordChange(event){
    this.setState({
      password: event.target.value
    })
  }

  handleSubmit(event){
    const {username, password} = this.state;
    //=> const username = this.state.username
    //=> const password = this.state.password
    event.preventDefault();

    if (!username || !password){
      console.log('Cannot log in with incomplete info');
      return;
      // if not valid gets out of the function without proceeding
    }
    // could be an else statement
    this.props.onSubmit({ username, password })
    // <LoginForm onSubmit={login} /> with login() a function that console.log()
    // function login({ username, password }) {
    //   console.log(`Logging in ${username} with password ${password}`);
    // }
  }

  render() {
    return (
      <form onSubmit={this.handleSubmit}>
        <div>
          <label>
            Username
            <input id="test-username" type="text" value={this.state.username} onChange={this.handleUsernameChange} />
          </label>
        </div>
        <div>
          <label>
            Password
            <input id="test-password" type="password" value={this.state.password} onChange={this.handlePasswordChange} />
          </label>
        </div>
        <div>
          <button type="submit">Log in</button>
        </div>
      </form>
    );
  }
}

module.exports = LoginForm;
```

Another example
```js
const React = require('react');

function countWords(line){
  console.log(line.split(' '));
  return line.split(' ').filter(function(word) { return word }).length;
  // return line.split(' ').filter(word => word).length;
}

function validatePoem(poem){
  const lines = poem.split('\n').filter(line => line);
  // returns an array of lines without empty lines

  const correctLineCount = lines.length === 3;
  // validates that there are 3 lines

  const correctWordCount = countWords(lines[0]) === 5 && countWords(lines[1]) === 3 && countWords(lines[2]) === 5;
  // validates length of each line

  return correctLineCount && correctWordCount;
  // returns true or false
}

class PoemWriter extends React.Component {
  constructor() {
    super();

    this.handleChange = this.handleChange.bind(this);

    this.state = {
      poem: '',
      isValid: false
    };
  }

  handleChange(event){
    const content = event.target.value
    if (content) {
      this.setState({
        poem: content,
        isValid: validatePoem(content)
      })
    }
  }

  render() {
    return (
      <div>
        <textarea rows="3" cols="60" value={this.state.value} onChange={this.handleChange} />
        {!this.state.isValid ? <div id="poem-validation-error" style={{color: 'red'}}>This poem is not written in the right structure!</div> : null}
      </div>
    );
  }
}

module.exports = PoemWriter;
```

## React Component Lifecycle
React components have two sets of properties: **props** and **state**. Props are given to the component by its parent. You can think of props as an external influence that the component has no control over, whereas a component's state is internal to the component. A component's state can change in conjunction to the props changing or when the user interacts with the component.

Components go through what we call a **component lifecycle**. This is broadly divided into three parts: **creation**, **updating**, and **deletion**. For example, if you open a new chat window in a website written in React, a `ChatWindow` component is **created**. As you are interacting with it and sending messages to your friends - that's the **updating** part. And when you finally close the window, the React component gets **deleted**.

The only required method for a React component to be valid is the `render()` method which describes what the HTML for the component looks like. There are a whole host of optional methods you can use if you need more control over how the component responds to change.

## Mounting
When the component is initially created, it gets "mounted" onto the DOM. It sounds more complicated than it is: essentially the component figures out its initial state and renders its initial HTML onto the page. At the mounting stage, there are two *lifecycle hooks* you can use: `componentWillMount` and `componentDidMount`. 

`componentWillMount` will get called just _before_ `render()` so you can use it to change the initial state if you need to. You would use this method to set up any long-running processes such as fetching and updating data. `componentWillMount` is called only once in the component lifecycle, immediately before the component is rendered. It is usually used to perform any state changes needed before the initial render, because calling `this.setState` in this method will not trigger an additional render.

For example, suppose you want to keep the time and date of when the component was created in your component state, you could set this up in `componentWillMount`.

```javascript
componentWillMount: function(){
  this.setState({ startDateTime: new Date(Date.now())});
}
```

`componentDidMount` will get called just _after_ the `render()` method. That means that the HTML for the React component has been rendered into the DOM and can be accessed if necessary. This method is used to perform any DOM manipulation of data-fetching that the component might need.

In React, this is where you would set up any long-running processes you want to use in your component, for example fetching data. Suppose we were building a weather app that fetches data on the current weatherand displays it to the user. We would want this data to update every 15 seconds without the user having to refresh the page. `componentDidMount` to the rescue!

```javascript
componentDidMount: function(){
  this.interval = setInterval(this.fetchWeather, 15000);
}
```

Called once on initial render:

| Method             | nextProps | nextState | Can call `this.setState` | Called when?               | Used for                                                                                    |
|--------------------|:---------:|:---------:|:----------------------:|:--------------------------:|:-------------------------------------------------------------------------------------------:|
| `componentWillMount` |     no    |     no    |           yes          | once, just before mounting | setting initial state based on props                                                        |
| `componentDidMount`  |     no    |     no    |           no           | once, just after mounting  | setting up side effects (e.g. creating new DOM elements or setting up asynchronous functions |

## Updating
Whenever a component's state or props are changed, it gets re-rendered on the page. That's the beauty of React components - they're quick to *react* to changes. A re-render could be triggered when a user interacts with the component, or if new data (props or state) is passed in.

For example, going back to the chat window example, whenever you press "send" on a message, the `ChatWindow` component gets re-rendered as it needs to display an extra message. Whenever a re-render is triggered, there is a whole host of lifecycle hooks that get called. You can choose to use any of these to decide how your React component should respond to changes.

We are kindly provided with 4 lifecycle methods to help us handle updates:`componentWillReceiveProps`,
`shouldComponentUpdate`, `componentWillUpdate` and `componentDidUpdate`.

These methods always get called in the same order and the `render()` method which renders the React component into
the DOM will be called just before `componentDidUpdate`, so the actual order of lifecycle methods being called is:

1. `componentWillReceiveProps(nextProps)`

2. `shouldComponentUpdate(nextProps, nextState)`

3. `componentWillUpdate(nextProps, nextState)`

4. `render()` (can access props and state via `this.props` and `this.state` - previous props are no longer available)

5. `componentDidUpdate(prevProps, prevState)` (can still access current props and state via `this.props` and
`this.state` and this is the last time previous props and state will be available as they are passed into the function).

`componentWillReceiveProps` is invoked when the props the parent is passing into the component have changed. You could use this to change the component's state based on the new props.

This method is called when the component is receiving new props from it's parent. A word of caution: a common mistake
here is to assume that the props have changed. Just because the method is called doesn't necessarily mean that the props
have changed.

You could use this method for recording a trend between current and previous props. For example, imagine an open air
theater with people coming in and out. You would be interested in the trend of people's movement - are more people
coming in (audience increasing) or leaving (audience decreasing). In a lifecycle method, you might denote it as follows:

```javascript
componentWillReceiveProps(nextProps){
  this.setState({
    audienceIncreasing: nextProps.numAudienceMembers > this.props.numAudienceMembers,
    audienceDecreasing: nextProps.numAudienceMembers < this.props.numAudienceMembers
  })
}
```

`shouldComponentUpdate` is invoked just before the component is about to re-render. At this stage, you can compare the old and new props and state and prevent unnecessary re-renders: if the changes in state and/or props don't actually alter the component that's being shown to the user, there is no point "repainting" it as it is an unnecessary performance drain.

`shouldComponentUpdate` is the odd one out in the lifecycle methods as it doesn't operate on the state, but has a
`Boolean` return value determining whether the component should update or not. It's useful to prevent un-necessary
re-renders and making your website faster (this is useful especially when your application gets really big!).

```javascript
shouldComponentUpdate(nextProps, nextState) {
  return (this.props.myImportantValue !== nextProps.myImportantValue);
}
```

For example, the above code means that the React component gets re-rendered when `myImportantValue` has changed. A word
of caution though: you might think it'd be a good idea to use the `shouldComponentUpdate` function to only re-render the
component if *any* of the props have changed and avoid *all* redundant re-renders, e.g. if `this.props !== nextProps`.
However, because `props` and `nextProps` are both JavaScript objects, this comparison will always return `true`, that
is `{} === {}` is never `true` in JavaScript (object equality is one of the many, many JavaScript quirks out there...
The reasons behind it are a bit too advanced to explain at this stage, it's enough just to know about it. Further
reading [here](http://adripofjavascript.com/blog/drips/object-equality-in-javascript.html).

`componentWillUpdate` is called just after `shouldComponentUpdate` has finished and just before the new component gets rendered. You would usually use this method to update integrations with third party libraries.
No state changes are allowed in this method and it should be used solely for preparing for the upcoming update, not trigger one. One of the more common uses of **componentWillUpdate** is to to call an action, set a variable or start an animation (not in the state) based on state changes.

The `render()` method is the most familiar one to all React developers. In fact, in everyday development, we often end up writing React components that only use the `render()` method! At this stage, the next props and state have become available from `this.props` and `this.state` and the component gets rendered into the DOM.

`componentDidUpdate` is called just after the new component had been rendered. You will have access to the previous props and state as well as the current ones, and you can use this method to update any third party libraries if they happen to need an update due to the re-render.

This method used very often, but it is a kind of a looking back to the opdate that's just occurred. We will have access
to both the current props and previous props. A common use case for this would be to update a 3rd party library.

```javascript
  componentDidUpdate(prevProps, prevState) {
   if (prevProps.height !== this.props.height) {
     someChartLibrary.updateHeight(this.props.height);
   }
  }
```

Not called on initial render, but always called whenever a subsequent re-render is triggered:

|           Method          | nextProps | nextState | Can call `this.setState` |                       Called when?                      |                                     Used for                                     |
|:-------------------------:|:---------:|:---------:|:----------------------:|:-------------------------------------------------------:|:--------------------------------------------------------------------------------:|
| `componentWillReceiveProps` |    yes    |     no    |           yes          |  many times, whenever component is going to receive new props  |                     applying state changes based on new props                    |
|   `shouldComponentUpdate`   |    yes    |    yes    |           no           |    many times, whenever a re-render has been triggered    |    deciding based on new & old props & state whether a re-render should occur    |
|    `componentWillUpdate`    |    yes    |    yes    |           no           | many times, when new state and props are being received | prepare for the update, dispatch any actions or animations based on state change |
|     `componentDidUpdate`    |    yes*   |    yes*   |           yes          |    many times, just after the re-render has finished    | any DOM updates following a render (mostly interacting with 3rd party libraries) |

\* `componentDidUpdate` will actually receive `prevProps` and `prevState` as arguments, as the newly applied state and props can be accessed through `this.props` and `this.state`.

## Unmounting
In the unmounting (or deletion, or "cleanup") phase, we have just one lifecycle method to help us out: `componentWillUnmount`. `componentWillUnmount` is the last function to be called immediately before the component is removed from the DOM. It is generally used to perform clean-up for any DOM-elements or timers created in **`componentWillMount`**.

At the unmounting stage, the component gets deleted and cleared out of the page. The only lifecycle hook at this stage is `componentWillUnmount`, which is called just before the component gets deleted. This is used to clear out any stuff set up in `componentDidMount`.

For example, if you had a component that displays the weather data in your home town, you might have set it up to re-fetch the updated weather information every 10 seconds in `componentDidMount`. When the component gets deleted, you wouldn't want to continue doing this data-fetching, so you'd have to get rid of what was set up in `componentWillUnmount`.

For a React component, this is where you would clean up any of those long running processes that you set up in `componentDidMount`. In the above data fetching example, all we would have to do is clear the interval so that the weather API would no longer get called every 15 seconds:

```javascript
componentWillUnmount: function(){
  clearInterval(this.interval);
}
```

Called only once, just before the component is removed form the DOM:

|        Method        | nextProps | nextState | Can call `this.setState` |                     Called when?                    |                         Used for                        |
|:--------------------:|:---------:|:---------:|:----------------------:|:---------------------------------------------------:|:-------------------------------------------------------:|
| `componentWillUnmount` |     no    |     no    |           no           | once, just before component is removed from the DOM | destroying any side effects set up in componentDidMount |

- [React: Component Specs and Lifecycle](https://facebook.github.io/react/docs/component-specs.html)
- [Understanding the React Component Lifecycle](http://busypeoples.github.io/post/react-component-lifecycle/)

## Changing State
React is all about rendering _stuff_: A React component takes some data, builds some virtual representation of how our DOM is *supposed* to look like and returns it:

```js
class BlogPost extends React.Component {
  render () {
    return (
      <article>
        <h1>{this.props.title}</h1>
        <p>{this.props.body}</p>
      </article>
    );
  }
}
```

The above `BlogPost` component renders an article consisting of a `title` and `body`. Those are being passed down as `props`. So whenever we want to re-use the `BlogPost` component, we can simply give it a `title` and `body`:

```js
class Blog extends React.Component {
  render () {
    return (
      <div>
        <BlogPost title={'Hello World!'} body={'Hello, this is my blog.'} />
        <BlogPost title={'Good bye!'} body={'I\'m busy. I\'m shutting this blog down.'} />
      </div>
    );
  }
}
```

This is incredibly powerful, since it allows us to gradually remove complexity by re-structuring our application into smaller, easier to test units. `props` decouple our components.

As we just saw, props can be seen as arguments for pure components. Pure components don't rely on any internal state or side-effects: They simply return a virtual representation of how they want to "look" like.

There is only one problem: props are always being "passed down" from the component's immediate ancestor. So for example, the `Blog` component passes the blog post data to the `BlogPost` component. But where does the blog *data* actually come from?

```js
class Blog extends React.Component {
  render () {
    return (
      <div>
        <BlogPost title={'Hello World!'} body={'Hello, this is my blog.'} />
        <BlogPost title={'Good bye!'} body={'I\'m busy. I\'m shutting this blog down.'} />
      </div>
    );
  }
}
```

In the above example, we simply hard-coded the blog titles and bodies. Obviously this isn't really what we want, otherwise we might as well just render everything on the server — not very *reactive* at all.

Instead we typically want to dynamically load the data from some API endpoint, for instance `GET /api/posts`. So whenever we render a new blog component, we do a XHR call and load the blog posts that we want to render.

```js
class Blog extends React.Component {
  componentDidMount () {
    fetch('http://localhost:4000/api/posts')
      .then(response => response.json())
      .then(posts => {
          console.log('Yey! I got some posts!', posts);
      });
  }
  render () {
    return (
      <div>
          <BlogPost title={'Hello World!'} body={'Hello, this is my blog.'} />
          <BlogPost title={'Good bye!'} body={'I\'m busy. I\'m shutting this blog down.'} />
      </div>
    );
  }
}
```

This means that whenever we `mount` this component by rendering it as a child of some other part of our application, e.g. using `<Blog />`, React executes the `componentDidMount` method that requests data from our API.

Once we receive those blog posts, we `console.log` them. While `console.log`ging them is certainly fun, our users won't be too happy about having to open the Chrome DevTools in order to read our blog. So instead of just printing them to the console, the `Blog` component should somehow "keep track of them".

The most intuitive solution would be to "set" them as a property on the component. React provides a method for that called... `setState`! `setState` allows components to keep track of their **internal** state.

So let's change our component to update the state of the blog component once we receive the requested blog posts from our API:

```js
  componentDidMount () {
    fetch('http://localhost:4000/api/posts')
      .then(response => response.json())
      .then(posts => {
        console.log('Yey! I got some posts!', posts);

        // Let's update the state here:
        this.setState({ posts: posts });

        // or shorter: this.setState({ posts });
      });
  }
```

Now that we updated the component's state using `setState`, we want to render our posts using the `BlogPost` component, so we need to update our component's render method:

```js
  render () {
    return (
      <div>
        {
          this.state.posts.map((post) =>
            <BlogPost title={post.title} body={post.body} />
          )
        }
      </div>
    );
  }
```

Keep in mind that we didn't change the `BlogPost` component *at all* — ideally we should try to keep the majority of our components "stateless".

At this point, you might wonder why we had to use `setState`, if all `setState` does is... well... setting `this.state`. There is a very simple reason for that:

React needs to "know" that a state change happened, since whenever a component's "data" (state or props) changes, React has to re-render the component (runs its render function to figure out "what changed").

### State vs Props

At this point you might wonder when to use `props` and when to use `state`, but there is a good rule of thumb when laying out our application's architecture:

* Use `state` for adding interactivity to our component:

    A dropdown menu for example can be in an `expanded` or `collapsed` state, a modal dialog can be `open` or `closed`.

* Move the state "up":

    In our blog example, the `BlogPost` component could also "manage" its own state by doing a separate XHR request. Nevertheless, this isn't an elegant solution, since the blog needs to "know" about the blog posts anyways (how else would it "decide" how many `<BlogPost />` components should be rendered in the first place?).

    Moving **application state** higher up generally speaking simplifies the architecture of our application and allows us to keep the majority of the components stateless.

    State is hard to manage and difficult to test. You should always try to keep our components as pure as possible.

* Start with props:

    When creating the layout of your project, you typically start with a static version and then add interactivity once we reach a certain point.

    During this initial phase, there is almost never a need for state. Everything can be done using props during those initial minutes. Try to keep your components as encapsulated and isolated as possible while we're gradually adding interactivity to individual parts of your application.

    For our `<Blog />` example, we first hardcoded the `<BlogPost />` component's props and then added an API call that updated the `Blog` component's state.

In general, it's usually a good idea to start with a rather static version of your application, in which all data is being rendered by gradually passing down `props` to child components. Then — as a next step — we can add custom user interactions to your app, e.g. what happens when a user presses this button? Should it open a dialog by doing `this.setState({dialogOpen: true})`?

### `setState` in detail

Now that we built our blog, let's have a look at something something a bit more interesting: A modal.

![Modal](https://s3.amazonaws.com/learn-verified/react-changing-state-readme-modal.png)

Let's first start off laying out our component structure:

```js
class App extends React.Component {
  render () {
    return (
      <div>
        <Modal />
      </div>
    );
  }
}
```

A modal can either be open or closed, so our application needs to keep track of that. The `<Modal />` component itself only _knows_ whether or not it is open, it can't "open" itself — instead it has to expose some API for other components for opening it.

Therefore we need to keep track of whether or not the modal is open in its parent component. In this case, that's the `<App />` component. On page load, the modal shouldn't be open. The initial state of the modal is closed (`isModalOpen = false`). We can initialize a component's state in its constructor:

```js
class App extends React.Component {
  constructor (props) {
    super(props);
    this.state = {
      // modal should be closed on page load
      isModalOpen: false
    };
  }
  // ...
}
```

We then need to "tell" the `<Modal />` component whether or not it is open. The only way to communicate with the component is via its `props`. In this case, we would add a new `isOpen` prop to the `Modal` component:

```js
class App extends React.Component {
  // ...
  render () {
    return (
      <div>
        <Modal isOpen={this.state.isModalOpen} />
      </div>
    );
  }
}
```

Obviously our users are going to be very disappointed if they aren't able to open the popup, so let's add a separate button that triggers the modal:

```js
class App extends React.Component {
  // ...
  openModal () {
    this.setState({ isModalOpen: true })
  }
  render () {
    return (
      <div>
        <button onClick={this.openModal}>Open the modal!</button>
        <Modal isOpen={this.state.isModalOpen} />
      </div>
    )
  }
}
```

Now if we click the `Open the modal!` button, we update the `<App />` component's internal state, thus enforcing an update on the `<App />` component.

Since `this.state.isModalOpen` evaluates to `true` now, the modal is being opened:

```js
  render () {
    return (
      <div>
        <button onClick={this.openModal}>Open the modal!</button>
        <Modal isOpen={true} />
      </div>
    );
  }
```

But what does our modal component actually look like? Up until now, we didn't talk about the `<Modal />` component's render method.

As we just saw, the modal accepts an `isOpen` prop, which it then uses in order to add an `modal--is-open` class to its container:

```js
class Modal extends React.Component {
  render() {
    const { isOpen } = this.props;

    return (
      <div className={isOpen ? 'modal modal--is-open' ? 'modal'}>
        <button>close</button>

        <p>Hello! I am a modal.</p>
      </div>
    );
  }
}
```

Perfect! Now we can simply specify whether or not the modal is open using its `isOpen` prop.

As you might have noticed, the modal also has a "close" button. Currently it doesn't do anything, so let's think about what should happen if the close button is being pressed:

1. The user clicks the close button.
2. The `<Modal />` component needs to update the `<App />` component's `isModalOpen` state.

For convenience, we're now going to add a `closeModal` method on the `<App />` components:

```js
class App extends React.Component {
  // ...
  openModal () {
    this.setState({ isModalOpen: true })
  }
  closeModal () {
    this.setState({ isModalOpen: false })
  }
  // ...
}
```

The `<Modal />` component now needs to be able to call the `<App />` component's `closeModal` method. But React components can't directly access their ancestors, so instead we have to pass the `App`'s `closeModal` method as a handler to the `Modal`:

```js
class Modal extends React.Component {
  render () {
    const { isOpen, onClose } = this.props;

    return (
      <div className={isOpen ? 'modal modal--is-open' ? 'modal'}>
        <button onClick={onClose}>close</button>

        <p>Hello! I am a modal.</p>
      </div>
    );
  }
}
```

```js
class App extends React.Component {
  // ...
  render () {
    return (
      <div>
        <button onClick={this.openModal}>Open the modal!</button>
        <Modal isOpen={this.state.isModalOpen} onClose={this.closeModal}/>
      </div>
    );
  }
  // ...
}
```

And that's it! Now the modal is able to communicate with the `<App />` by calling the passed in handler.

There is only one problem: When we click `close`, we get the following error:

```
TypeError: onClose is not a function
```

Uh? That's a bit weird. What happened?

We forgot to bind our handler functions! Typically we would bind all you component's public methods in the constructor (click handlers etc.):

```js
class App extends React.Component {
  constructor (props) {
    super(props);
    this.state = {
        // modal should be closed on page load
        isModalOpen: false
    };
    this.openModal = this.openModal.bind(this);
    this.closeModal = this.closeModal.bind(this);
  }
  // ...
}
```

Now everything works as expected. Good job, we just implemented a React modal!

**Advanced:** If you're ever looking for an actual React modal to use in a production application, [`react-modal`](https://github.com/reactjs/react-modal) has a very similar API to the component we just implemented.

- [React: Communicate Between Components](https://facebook.github.io/react/tips/communicate-between-components.html)
- [Autobinding, React and ES6 Classes](http://www.ian-thomas.net/autobinding-react-and-es6-classes/)

## Toggling State

One way to communicate between components by is by passing around handler functions, e.g. a button usually has an `onClick` handler, while a custom modal component might accept an `onClose` function.

While it's certainly possible to structure your component hierarchy using `on...` handlers, this approach is rather inflexible  and leads to a lot of code duplication in the long term.

In this lesson we're going to be learning how decoupling those functions into isolated `actions` allows us to de-couple handlers from the component they operate on.

A lot of components have two states:

- a toggle button for instance is either "on" or "off"
- an input field can be enabled or disabled
- a checkbox can either be ticked or unticked
- a log paragraph of text could either be collapsed or expanded

### Toggle Button

Let's first have a look at a simple example: A toggle button.

![Toggle Button States](./assets/toggle_buttons.png)

A toggle button can either be enabled or disabled.

Using what we already learned about state, we could easily implement such a switch:

```js
class ToggleButton extends React.Component {
  constructor (props) {
    super(props);
    this.state = {
      // initially our `ToggleButton` is 
      enabled: false
    };
  }
  handleClick () {
    this.setState({
      // negate enabled
      enabled: !this.state.enabled
    });
  }
  render () {
    return (
      <button onClick={this.handleClick}>
        {this.state.enabled ? 'Enabled' : 'Disabled'}
      </button>
    );
  }
}
```

Our component renders a button. If the toggle button is in the `enabled` state, we display the "Enabled" lable, otherwise we consider the button to be "Disabled".

### Enabled / Disabled Inputs

Not only toggle buttons can be toggled, but also checkboxes. A checkbox is either enabled or disabled.

Implementing a form containing a checkbox (e.g. for one of those legal disclaimers) is trivial:

![Order chocolate](./assets/order_chocolate.png)

Similar to the toggle button above, the checkbox would have an enabled and disabled state.

```js
class ChocolateDisclaimer extends React.Component {
  constructor (props) {
    super(props);
    this.state = {
      // a customer first has to promise not to store the chocolate in the
      // fridge
      enabled: false
    };
  }
  handleClick () {
    this.setState({
      enabled: !this.state.enabled
    });
  }
  render () {
    return (
      <form>
        <label>
          <input type='checkbox' checked={this.state.enabled} onClick={this.handleClick} />
          I agree to never, ever store chocolate in the fridge.
        </label>
        <button onClick={...} disabled={this.state.enabled}>Submit order</button>
      </form>
    )
  }
}
```

As we can see, this component looks fairly similar to the toggle button above. The only real difference is that instead of a toggle "button", we now have an input of type `checkbox`. Other than that, everything remains the same.

Wouldn't it be nice if we could de-duplicate this logic and extract out the redundant `handleClick` handler?

### Modularizing actions

If we look at the code of the toggle button and chocolate disclaimer, we notice that the click handlers are completely **identical**.

Code redundancy is never a good thing, therefore we should try to extract out our `handleClick` function.

One way would be to have a super-class `Toggleable` that both `ChocolateDisclaimer` and `ToggleButton` inherit from:

```js
class Toggleable extends React.Component {
  toggleState () {
    this.setState({
      enabled: !this.state.enabled
    });
  }
}
```

`ToggleButton` could then inherit from this superclass:

```js
class ToggleButton extends Toggleable {
  constructor (props) {
    super(props);
    this.state = {
      // initially our `ToggleButton` is 
      enabled: false
    };
  }
  render () {
    return (
      <button onClick={this.toggleState}>
        {this.state.enabled ? 'Enabled' : 'Disabled'}
      </button>
    );
  }
}
```

This is already a bit better, but becomes quickly unmanageable. A component might for instance be `Toggleable` and `Submittable`… which becomes a bit messy very quickly. JavaScript doesn't support multiple-inheritance (inheriting from more than one class at once) and building our own mixin system is a bit unnecessary.

Instead, we can extract out our handler into a separate "action".

An action is just a plain function that accepts a context (`ctx`) and arbitrary additional arguments (for instance the event itself in case we want to
`.preventDefault()`):

```js
function toggleState (ctx, ev) {
  ctx.setState({
    enabled: !ctx.state.enabled
  });
}
```

`ctx` is the `this` context of the component that the action is "bound" to.

The above action could be used in the `ToggleButton` as well as the `ChocolateDisclaimer`.

In both cases, the context would be `this`. The action would be bound inside the component's constructor function:

```js
class ToggleButton extends React.Component {
  constructor (props) {
    super(props);
    this.state = { enabled: false };
    this.toggleState = () => toggleState(this);
  }
  render () {
    // ...
  }
}
```

Instead of using an arrow function, we could also "curry" the `toggleState` function. Currying a functions means converting a function that accepts multiple arguments into a function that accepts one argument at a time:

```js
function toggleState (ctx, ev) {
  ctx.setState({
    enabled: !ctx.state.enabled
  });
}
```

could also be written as

```js
const toggleState = ctx => {
  // actual event handler
  return ev => {
    ctx.setState({
      enabled: !ctx.state.enabled
    });
  }
}
```

or, if you want to keep it really concise:

```js
const toggleState = ctx => ev =>
  ctx.setState({
    enabled: !ctx.state.enabled
  });
```

This has the advantage that we no longer need to wrap our `toggleState` function inside the component's constructor:

```js
class ToggleButton extends React.Component {
  constructor (props) {
    // ...
    this.toggleState = () => toggleState(this);
  }
  // ...
}
```

could instead be written as without the outer arrow function:

```js
class ToggleButton extends React.Component {
  constructor (props) {
    // ...
    this.toggleState = toggleState(this);
  }
  // ...
}
```

And that's it! Now we modularized our `toggleState` handler! Instead of duplicating our `handleClick` handler, we can now apply the `toggleState` function to anything that can be toggled or turned on / off. It doesn't matter if it's a button, "Collapse"-button, input or lightsaber. Everything that can be enabled or disabled can be toggled by our `toggleState` function.

- [Flux: Actions](https://facebook.github.io/react/blog/2014/07/30/flux-actions-and-the-dispatcher.html)

## What is a store?

A store is basically just a plain JavaScript object that allows components to share state.

In a way, we can think of a store as a database. On the most fundamental level, both constructs allow us to store data in some form or another.

In Flux-terms, a store typically has a couple of methods that we're going to go into more detail as part of this lesson. Usually we won't create our own stores from scratch, but instead simply customize one of the stores provided by library that we're using (usually [facebook/flux](https://www.npmjs.com/package/flux)).

### Stores — singletons by design

Singletons are application-level singletons. While there might be a variety of different stores (such as a `UserStore`, `FeedStore`, `MessageStore` etc.), there won't be multiple instances of the same store. Typically this means exporting an individual store object and globally exposing it to all component's that `require` it.

This is somewhat analogous to our database metaphora: We might store different "kinds" of data that we store in different databases (e.g. we might unstructured data in MongoDB and relational data in something like PostgreSQL), but all clients share the "same" database. Each application node has access to the same data.

On the most fundamental level, a store encapsulates state. We can easily model this using a ES6 class:

```js
class Store {
  constructor (initialState) {
    this.state = initialState;
  }

  setState (state) {
    this.state = state;
  }

  getState () {
    return this.state;
  }
}

module.exports = new Store({});
```

### Subscribing to stores

Of course having a store that simply wraps our state object isn't too useful yet. React components are data-driven. If we update their state using `setState`, React re-evaluates the component's `render` function and updates the rendered DOM structure.

Hence we need a way to wire up our components to our global store. In some way, components need to be able to "listen" for state changes that occur in out store:

![Flux Store](./assets/Flux - Store.png)

An arbitrary number of components can subscribe to state changes that occur in the store. Component's can then react to the  state change by updating their own state and thus triggering a re-render.

But how can component's register themselves at the store?

Let's look at an example component for that!

### A `<Profile />` component

Let's assume for a moment that our store stores user data, e.g. the name and profile descriptions of individual members (something like Facebook profile).

Each user can be represented by a flat object:

```js
{
  id: 0,
  firstName: 'Konrad',
  lastName: 'Zuse',
  bio: 'I like building stuff.'
}
```

Our store simply wraps an array of user records:

```js
class UserStore {
  constructor (initialState) {
    this.state = initialState;
  }

  setState (state) {
    this.state = state;
  }

  getState () {
    return this.state;
  }
}

module.exports = new UserStore([]);
```

Our profile component now renders the state of the `UserStore` component:

```js
const userStore = require('../stores/userStore');

class Profile extends React.Component {
  render () {
    const { userId } = this.props;
    const profile = userStore.find((user) => user.id === userId);

    if (!profile) {
      return (
        <div>Loading...</div>
      );
    }

    return (
      <dl>
        <dt>First Name</dt>
        <dd>{profile.firstName}</dd>
        <dt>Last Name</dt>
        <dd>{profile.lastName}</dd>
        <dt>Bio</dt>
        <dd>{profile.bio}</dd>
      </dl>
    );
  }
}
```

We're almost there now. Currently we assume that the user that should be rendered is available in the store at the point when we render the `<Profile />` component.

This might not always be the case. E.g. our users are most likely going to be loaded from some sort of API. What if we render the component before respective HTTP request receives a response? In this case, our profile component would simply display `Loading...` forever.

We therefore need to notify subscribed components about eventual state changes. This sounds conceptually very similar to an event emitter and in fact that's exactly what we're going to implement!

We can either inherit from some event emitter (e.g. `require('events').EventEmitter`) or we can implement our own. To recap the inner-workings of how an event emitter works, let's implement our own for now!

### Turning our store into an `EventEmitter`

Our store needs to expose an API for registering components that depend on its state. Analogous to an `EventEmitter`, we call the respective method `addListener` and `removeListener`.

Both methods accept a listener function that will be called with the updated state object whenever the store's state changes.

To start off, we need to store an array of those listener functions on the initiated store object:

```js
class UserStore {
  constructor (initialState) {
    this.state = initialState;

    // Our listener functions will be stored on UserStore#listeners.
    this.listeners = [];
  }

  // ...
}
```

Now components can register themselves using `UserStore.addListener`. The `addListener` function is simply going to add the listener to the `listeners` array.

```js
class UserStore {
  // ...
  addListener (listener) {
    this.listeners.push(listener);
  }
}
```

The `UserStore` iterates through all registered event listeners whenever a state change occurs. All listeners will be called with the updated state as a first argument:

```js
class UserStore {
  // ...
  setState (state) {
    this.state = state;
    for (const listener of this.listeners) {
      listener(state);
    }
  }
}
```

And the `<Profile />` component can now call this method in order to register for subsequent state changes. In order to trigger a re-render whenever the store gets updated, we copy the store's state onto the component's state:

```js
class Profile extends React.Component {
  componentDidMount () {
    userStore.addListener((state) => {
      this.setState(state)
    });
    this.setState(userStore.getState())
  }
  render () {
    const { userId } = this.props;

    // We're now accessing `this.state` instead of `userStore`.
    const profile = this.state.find((user) => user.id === userId);

    // ...
  }
}
```

And Voila! Our component is now wired up to our store. There is just one small (but very important!) issue which we didn't address,yet!

What happens when the component is being unmounted? In other words, what happens when the user leaves the profile page and goes somewhere else?

Subsequent store updates would trigger a `setState` on an unmounted component! Not only is this going to trigger a warning in React, it's also a very common source for memory leaks in Flux architectures. Whenever we register components on a store, we have to make sure we remove all listeners at the point where the component is being unmounted.

`EventEmitter`s usually expose a `removeListener` method for cleaning up event listeners, but it's quite common for Flux stores to simply return a function from `addListener` that when called removes the listener from the store. Sounds complicated? Let's look at the code!

```js
class UserStore {
  addListener (listener) {
    this.listeners.push(listener);
    const removeListener = () => {
      this.listeners = this.listeners.filter((l) => listener !== l);
    };
    return removeListener;
  }
}
```

Now we can update our `<Profile />` component's lifecycle methods to trigger the `removeListener` method on "unmount":

```js
class Profile extends React.Component {
  // ...
  componentDidMount () {
    // We store a reference to the added event listener.
    this.removeListener = userStore.addListener((state) => {
      this.setState(state);
    });
    this.setState(userStore.getState());
  }
  componentWillUnmount () {
    // Destroy the listener when the component unmounts.
    this.removeListener();
  }
  // ...
}
```

And that's it! Our `<Profile />` component gets updated whenever we `UserStore` gets updated.

### Store API

Let's take a moment and revisit the store methods we just added:

#### `addListener(listener) #=> removeListener()`

Called by components to register a listener function. The listener function will be called with the updated state object.

The returned `removeListener` function de-registers the previously registered listener function.

#### `getState() #=> state`

Used by components to get the initial state of the store. Returns the currently encapsulated state object.

#### `setState(state)`

Explicitly stores the passed in state on the store instance. In the next lesson we're going to explore how to generalize data flow in our application to allow actions to mutate stores via a kind of central event bus ("Dispatcher"). We're slowly moving towards an architecture in which stores are being updated using external action handlers rather than explicit function calls. But we aren't quite there yet!

#### Custom Getters

So far our store only has a single method for extracting all the user records that have been stored in it.

This can be a bit messy, since in our above example, the `<Profile />` component actually stores **all** received user objects, even though it only ever renders a single one.

In scenarios like that, it's quite common to add this "filtering" logic to the underlying store.

Instead of finding the matching user object in the `<Profile />` component's render method, we can instead add a new method to the `UserStore` in order to enable us to use similar logic in other components that might also render users (such as a list of friends):

```js
class UserStore {
  // ...
  getUserById (id) {
    return this.state.find(user => user.id === id);
  }
}
```

Our `<Profile />` component can now simply call this method in order to update its own state accordingly.

```js
class Profile extends React.Component {
  componentDidMount () {
    // ...
    const user = userStore.getUserById(this.props.userId);
    this.setState({ user });
  }
}
```

And our render method no longer has to iterate over all user records:

```js
class Profile extends React.Component {
  render () {
    const {user} = this.state;

    if (!user) {
      return <div>Loading...</div>;
    }

    return (
      <dl>
        <dt>First Name</dt>
        <dd>{user.firstName}</dd>
        <dt>Last Name</dt>
        <dd>{user.lastName}</dd>
        <dt>Bio</dt>
        <dd>{user.bio}</dd>
      </dl>
    );
  }
}
```

This has a couple of advantages over copying over the "entire" `UserStore` state.

1. Performance Improvement

Computers are pretty fast, so unless there is a huge number of users, the performance difference won't be noticeable. Nevertheless, small improvements add up, so not re-rendering the `<Profile />` component whenever **any** user is definitely desirable.

Further more, we could implement a `shouldComponentUpdate` method on the `<Profile />` component:

  ```js
  shouldComponentUpdate ({ user }) {
    return user !== this.state.user;
  }
  ```

Which would ignore store updates that are unrelated to our actual user record.

2. Better modularity

Potentially, there could be all kinds of components that render user object. E.g. a chat sidebar could display each user using an individual component, a friend component or modal could equally be wired up to the shared store.

Extracting out the logic for finding individual users based on id reduces code redundancy in those cases.

- [React: Flux Overview](https://facebook.github.io/flux/docs/overview.html)
- [Actions and the Dispatcher](https://facebook.github.io/flux/docs/actions-and-the-dispatcher.html#content)

## Towards Unidirectional Data Flow

### Using Change Listeners

To understand what "unidirectional data flow" actually means, let's first consider a real-world example: We want to implement a simple application that allows us to organize tasks in some form of project board, similar to Trello:

![Trello Screenshot](./assets/Trello.png)

Trello allows you to raise issues, represented by "cards", assign them and move them into different columns, whereas each column represents a distinct step of your workflow.

When create an application like that, it's always helpful to first think about how one would go about organizing the underlying data:

Each card can be represented by a JSON object:

```js
{
  "title": "Create Mockups",
  "id": 123
}
```

Each card can only ever be in exactly one column. Each column has a name and a distinct set of cards associated with it:

```js
{
  "name": "TODO",
  "id": 456,
  "cards": [{
    {
      "title": "Create Mockups",
      "id": 123
    }
  }]
}
```

Now that we have a set of well-defined models and a beautifully designed UI, we can go about structuring our component hierarchy. In this case, the most basic screen is fairly simple. We have a project, which can be represented by a single, stateful component, multiple columns and a variety of card components.

In other words, this is what our project's render function could look like:

```js
class Board extends React.Component {
  render () {
    const { columns } = this.props;
    return (
      <div>
        {columns.map(({cards, id}) => <Column key={id} id={id} cards={cards} />)}
      </div>
    );
  }
}
```

Fairly trivial, right? A board has an arbitrary number of columns and each column can have some number of cards "pinned" to it:

```js
class Column extends React.Component {
  render () {
    const {cards} = this.props;
    return (
      <div>
        {cards.map(({title, id}) => <Card key={id} title={title} />)}
      </div>
    );
  }
}
```

The only problem with this approach so far is that it becomes incredibly hard to update deeply nested cards. We kind of just "accepted" that fact that the `columns` props gets passed down into the `<Board />` component, but where would this essential application state be actually located? Most likely we would have some form of `<App />` component that has an `this.state.board = {...}`. Upon being mounted, it would do some form of HTTP request and fetch the latest board state.

```js
class App extends React.Component {
  constructor (props) {
    super(props);
    this.state = { board: [] };
  }
  componentDidMount () {
    fetchBoard().then(board => this.setState({ board }));
  }
  render () {
    const {board} = this.state;
    return <Board board={board} />;
  }
}
```

And that's great and works beautifully. Until... it doesn't. So far all our board does is it displays cards, we can't edit them. Now who would want a read-only collaborative project management tool? — Exactly, nobody! So let's go ahead and add some handler functions!

Let's assume for a moment that we want to be able to edit the `title` of individual cards. In the old days, we would simply create a listener function on the card and delegate to the parent component (`<Column />`) once we're done editing (typically on `blur`). By delegate we mean "notifying the parent" about our changed data (in this case the changed title).

Now we all know how to attach change listeners by now, so we're going to skip this part. Let's concentrate on the remaining components instead.

The only place where we can update the state of our board / application is in the the `<App />` component.

**Remember** Components can't ever update their `props`, they can only mutate their own state.

Our `<Column />` component would attach an `onChangeTitle` listener to the
`<Card />` component:

```js
class Card extends React.Component {
  render () {
    const {cards} = this.props;
    return (
      <div>
        {cards.map(({title, id}, cardIndex) =>
          <Card
            key={id}
            title={title}
            onChangeTitle={this.handleChangeCardTitle.bind(this, cardIndex)}
          />
        )}
      </div>
    );
  }
}
```

The `handleChangeCardTitle` itself would actually "delegate" itself to its parent component, in this case the actual `<Board />` component:

```js
  handleChangeCardTitle (cardIndex, ev) {
    this.props.onChangeCardTitle(this.props.id, cardIndex, ev)
  }
```

The board would delegate to **its** parent, which is the actual `<App />` component:

```js
  handleChangeCardTitle (columnIndex, cardIndex, ev) {
    this.props.onChangeCardTitle(columnIndex, cardIndex, ev)
  }
```

The `<App />` component itself would now **actually** update the underlying state:

```js
class App extends React.Component {
  constructor (props) {
    super(props);
    this.state = { board: [] };
  }
  componentDidMount () {
    fetchBoard().then(board => this.setState({ board }));
  }
  // Magic comes in here:
  handleChangeCardTitle (columnIndex, cardIndex, ev) {
    // Actually we wouldn't even want to mutate this.state directly. Ideally we
    // should make a copy of the respective card and apply our change there.
    this.state.board[columnIndex][cardIndex].title = ev.target.value;
    updateBoard(this.state).then(() => {
      // Do some more magic here.
    });
  }
  render () {
    const {board} = this.state;
    return <Board board={board} onChangeCardTitle={this.hanldeChangeCardTitle(ev)} />;
  }
}
```

### Change Listeners? — We don't need them!

Now this _would_ work, but it's complicated beyond measures. It's much easier and less error-prone to move our state out into a separate store.

Let's take a step back and have a look at what our current architecture looks like.

```
<App /> (can update this.state.board)
  <Board /> (has to delegate to parent component)
    <Column /> (has to delegate to parent component)
      <Card /> (has to delegate to parent component)
      <Card /> (has to delegate to parent component)
    <Column /> (has to delegate to parent component)
      <Card /> (has to delegate to parent component)
```

The store could then handle the card updates in one form or another. The `<App />` component could subscribe to the store and all components would happy! No needless event handlers, just one, flat state tree.

But let's take a step back first and summarize why the above solution is problematic:

1. We had to add a separate event handler on each level.
2. Needless redundancy: `<Column />` and `<Board />` share _almost_ the same handler function — **almost**.
3. Adding a separate component "in-between" our existing components would complicated beyond measure — just imagine adding a separate `<BoardVersion />` component as a child of `<Board />`.

Clearly moving the state out into a separate, completely isolated store is the desired solution here. Instead of communicating via components that "pass through" events, we directly update the store (at least for now) and render subsequent changes by passing down updated `props`.

### Towards a Centralized Store

Having an isolated store is key in this scenario. We start by implementing our own little `BoardStore`, which is going to manage our `board`, `column` and `card` records.

Our store can be a simple even emitted that also wraps some custom data:

```js
class BoardStore {
  constructor (initialState = { columns: [] }) {
    this.state = initialState;
  }

  setState (state) {
    this.state = state;
  }

  getState () {
    return this.state;
  }
}

module.exports = new BoardStore();
```

Preferably we don't always want to implement our own eventing system every time we write a custom store, so in this case, we're simply going to inherit from `EventEmitter` (available via `events`) and use a single `change` event:

```js
const EventEmitter = require('events').EventEmitter;

class BoardStore extends EventEmitter {
  constructor (initialState = { columns: [] }) {
    this.state = initialState;
    super();
  }

  addListener (listener) {
    EventEmitter.prototype.addListener.call(this, 'change', listener)
  }

  removeListener (listener) {
    EventEmitter.prototype.removeListener.call(this, 'change', listener)
  }

  setState (state) {
    this.emit('change', state);
    this.state = state;
  }

  getState () {
    return this.state;
  }
}
```

**Advanced** Having a single store might not always be the most desirable solution. "Classical" Flux can be implemented using multiple stores.

And... BOOM! We have our store! Now let's have a look at our `<App />` component and wire it up!

### Subscribing to store changes `<App />`

Our `<App />` component is simply going to listen for store changes and encapsulate the corresponding application state whenever a store change occurs:

```js
class App extends React.Component {
  constructor (props) {
    // ...
    this.listener = this.listener.bind(this);
    this.setState({ board: boardStore.getState() });
  }
  componentDidMount () {
    boardStore.addListener(this.listener);
  }
  componentWillUnmount () {
    // We shouldn't forget this! Otherwise we would get a memory leak!
    boardStore.removeListener(this.listener);
  }
  listener (board) {
    // Update `<App />` state and trigger a re-render.
    this.setState({ board });
  }
  // ...
}
```

Our card can now update the store whenever someone changes its title. For now, we're going to add a method on the `BoardStore` to handle this logic. In subsequent lessons we're going to extract this update logic out event further.

```js
class BoardStore extends EventEmitter {
  // ...
  updateCardTitle (cardId, updatedTitle) {
    for (const column of this.state.columns) {
      const card = column.cards.find(card => card.id === cardId);

      // Ideally we should treat our store as an immutable data structure,
      // meaning instead of updated properties on cards directly, we should
      // create new cards to replace the one that should be updated. For now,
      // let's just set the title property and worry about the rest later.
      card.title = updatedTitle;
    }
    this.setState(this.state);
  }
  // ...
}
```

Stores are globally unique singletons. There will only ever be one `BoardStore`. Therefore our card component can just require it in and update the store directly by calling the `updateCardTitle` method with the updated title.

```js
class Card extends React.Component {
  constructor (props) {
    super(props);
    this.state = { title: '' };
  }
  handleChangeTitle (ev) {
    this.setState({ title: ev.target.value });
  }
  handleTitleBlur () {
    boardStore.updateCardTitle(this.props.id, this.state.title);
  }
  render () {
    // ...
  }
}
```

And we're done! Instead of passing down dozens of event handlers, we simply extracted out our state into a global store. The global store can be subscribed to and other components can update it. We essentially decoupled our component hierarchy (everything between `<App />` and `<Board />`) from our global store.

This makes adding new components and possibly bigger changes to our application structure much easier. It's significantly less code and also much easier to debug. If there is an error, it's guaranteed to be in one of the components that actually render or update the corresponding date, not in a completely unrelated "intermediary" component that simply passes down the data.

- [Redux](http://redux.js.org/)
- [Flux](https://facebook.github.io/flux/docs/overview.html)

## Component State vs Store State: ie do you really need Redux?

While our previous lessons extensively focused on moving state **out** of individual components, we don't always have to. In fact, sometimes it might even introduce more complexity than needed. Using `setState` and "local" component-level state is a perfectly fine choice in most cases.

In general, we should not start out by putting all our state into some form of global store (or multiple stores).

When architecting a user interface, try to use local state and parent props **first**. If we end up constantly passing down tons of props, we should consider connecting the component in question with the respective Flux store.

E.g. let's say we want to render some form of carousel, something like the [Bootstrap's Carousel component] (http://getbootstrap.com/javascript/#carousel):

A carousel is a perfect example on where using a store to extract out component state doesn't necessarily make things easier (or would simply be a massive overkill).

Writing the essential handler functions for the component in question using "classical" React-style without **any** "outside" state is trivial:

```js
class Carousel extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      // We start out rendering the first slide. 0 denotes the index of the
      // active item.
      currentSlide: 0,
    };
  }
  /**
   * Handler function that transitions to the next slide in the carousel.
   * This is the function that will be run once the user clicks the "next"
   * button.
   */
  goNext = () => {
    const previousSlide = this.state.currentSlide;
    this.setState({ currentSlide: previousSlide + 1 });
  }
  /**
   * Equivalent to `goNext`. Handler function that will be invoked when clicking
   * the "back" button.
   */
  goBack = () => {
    const previousSlide = this.state.currentSlide;
    this.setState({ currentSlide: previousSlide - 1 });
  }
  render() {
    // Magic goes here
  }
}
```

In this case, using the local state of the component has a couple of advantages over using an external store:

1. The state is **by definition** bound to the component

When rendering a very long list of carousels, keeping the state stored in the store in sync with the _actual_ list of rendered components is hard. Let's say  we render one carousel for each photo "collection" — which could for example be represented by an array for image sources — keeping the array length in sync with whatever data structure we would use in the store for representing the selected slide index is unnecessarily complex. For example, when adding a photo collection, we need to add the `currentSlide` property to the store as well.

Simply distinguishing between "component UI" state and global application state radically simplified the architecture in the above case, since component state can by definition not exist without a matching component (and vice versa).

2. Simplified Testing

Testing React components is extremely easy compared to other frameworks, such as Angular. Reason being that React components are by definition declarative, while Angular heavily relies on imperative APIs.

Using stores doesn't necessarily break this abstraction, but it makes it much harder to properly test all the possible states that a component can be in, since a store might contain state that isn't directly consumed by the component to be tested.

But more importantly, we now need to manage a store during testing. This means we need to make sure we **always** restore it to its previous state before every test case, otherwise this can lead to hard to debug failed tests. In Mocha, we can use `beforeEach` to run a function before every test case (`it(...)`).

Instead of restoring the store's state, we can also mock it out. This eliminates the need to reset the store.

3. Reusing the component is possible

While we focused on implementing our own set of stores, some people prefer to use Redux, Rx, mobx or some other library for managing state and implementing unidirectional data flow.

By storing state in an external store, we implicitly couple the component to whatever architecture we chose for our main application. If we're implementing an accordion component using Flux, it means everyone using our component will have to use Flux in order to interact with it (even though it might be hidden though the public API of the component).

Hence using component state (and props) instead of stores is the preferred way when creating reusable components.

### Connecting components using lifecycle methods

So far we oftentimes "connected" components to stores by adding an event listener on the store in the component's lifecycle methods:

```js
class MyCounter extends React.Component {
  componentDidMount() {
    this.removeListener = store.addListener(count => {
      this.setState({ count });
    });
  }
  componentWillUnmount() {
    this.removeListener();
  }
}
```

In `componentDidMount` we add an event listener that updates the component's state based on the store's state, thus triggering a re-rendering.

In `componentWillUnmount` we remove the event listener. Typically `addListener` returns a function that — when invoked — removes the event listener from the store. In other cases people might subclass the `EventEmitter` class directly in order to implement a store, hence there are cases in which we actually have to call `removeListener` on the store itself.

Whether or not we use `componentDidMount` instead of `componentWillMount` doesn't make a difference here. We can call `setState` in both.

### Presentational vs Container Components

**Container components** are components that are directly **connected** to our store, e.g. using the `addListener` method. They are primarily concerned with holding state, managing it and passing it to other components using props.

Container components have handler functions that dispatch actions or mutate state. They contain the "business logic" of our application.

In single page apps, a good rule of thumb is to make each page of your application (or component attached to a sub-route) a container component. While it isn't necessarily a bad idea to use nested container components, passing props to pure components tends to be easier to test and reason about.

**Presentational components** are modular, reusable (and typically small) components that are concerned with "how stuff looks". They are not connected to a particular store, can be used in different applications and are usually stateless (as in "pure").

Usually UI elements (with a bit of interaction) are presentational components and therefore not concerned with the actual state of the application. E.g. a modal, accordion, or button should not be container components.

Deciding whether or not something should be a container or presentational component is not a definitive decision. Making presentational components stateful by wiring them up to a store is usually quite easy and gets rid of a lot of indirection. For example passing down a lot of different props 5 levels deep is much more error prone than simply connecting the "leaf" component to the store.

It also means we don't need to rerender all the components in between the presentational leaf component that is due to be rendered and the intermediate components that simply pass down the state via props from the container component.

- [Interactivity and Dynamic UIs](https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html)
- [You Might Not Need Redux](https://medium.com/@dan_abramov/you-might-not-need-redux-be46360cf367#.7v3xs9al2)
- [Presentational and Container Components](https://medium.com/@dan_abramov/smart-and-dumb-components-7ca2f9a7c7d0#.jp0dni40i)

## What makes a component "presentational"?

The answer to this question, as you may have guessed, is that a presentational component is a component whose primary responsibility is to render some piece of the beautiful user interfaces that we get to build as web developers. Their job, in other words, is to look good!

![I'm So Pretty](https://media.giphy.com/media/oLz0TmduZsUjm/giphy.gif)

There is, however, a bit more thinking that we need to do here, just so we understand precisely what it means when we say that a component is of the type "presentational." Very often when we speak of classes or categories of things in the world of programming, the types or classes that we are discussing are actually formalized in the libraries or languages themselves. Think, for example, of when we declare a React `Component.` When we do that we write either `React.createClass()` or (using the ES2015 format) `class SomeComponent extends Component`. Either way, we are creating an actual instance of `Component`.

But here's the rub. When we say that some component is "presentational" *we definitely do not mean* that the component is a formal type or class defined by the React library. There is no such thing as type `PresentationalComponent` in the React library. Rather, what we are dealing with here is simply a useful *convention*, or, better yet, a *programming pattern* that coders who have used React have found themselves following over and over again as they compose their component-based React UIs.

So what defines the presentational component pattern? Here's a list of defining features:
* Presentational components are primarily concerned with how things look;
* they probably only contain a render method;
* they do not know how to load or alter the data that they render;
* they rarely have any internally changeable `state` properties;
* and, they are best written as stateless functional components.

Okay, so there's our pattern description. Now let's jump into some code and see how presentation components actually look in practice.

### Surprise, you've already written presentational components!

Yep, this is true. Think about it. If a presentational component is simply a component that doesn't know anything about how to get the data it displays, and is mainly responsible for presentation, then you've been doing this from the beginning. A simple `HelloWorld` component, for example, is almost certainly presentational. Let's see if that's right &mdash; we'll even give our component the ability to take a prop:

```javascript
const HelloWorld = React.createClass({
  render: function() {
    return <div class="hello-world">Hello {this.props.message || 'World' }</div>;
  }
})
```

So does this fit our pattern? Absolutely, it does. Here is a component that does nothing but render a piece of our UI; that has no notion of how to fetch or reload the `message` data that it takes in as a `prop`; that has no changeable state; and that only contains a render method. So, I think we can safely say it fits the pattern well.

### Great, but when would we need such a simple component?

Good question! Our `HelloWorld` example is obviously not a very real-world example, but consider this: let's say we are working on a massive web application, and we'd like to standardize as well as place some limits on the characteristics of the  text inputs used throughout the application's forms.

In this case, we could certainly establish a style guide in our development team that dictates that all uses of `<input>` use a specific set of CSS classes, defined in our stylesheets, but this leaves our app open to a lot of human error. People would have to consistently follow the convention over time. And while we could certainly add props to our inputs by doing something like this -- `<input className='field' {...props}>` -- we've left the types of props that can be provided to our inputs wide open.

With React, we can do much better! Consider this `TextField` component:

```javascript
const defaultLimit = 100

export default class TextField extends React.Component {
  render() {
    return (
      <input
        className="field field-light"
        onChange={this.props.onChange}
        maxLength={this.props.limit || defaultLimit} />
    );
  }
}
```

First off, notice that here again, what we have a component that fits the presentational pattern. It's a simple wrapper around an `<input>`. But look how powerful it is! This simple wrapper establishes the CSS classes we will use in one place for every single input used throughout the app. Think of how easy it would be to change if we later decided we wanted a different look! But that's not all we've accomplished here. The component also establishes a straightforward API for all our text fields consisting of an `onChange` callback -- because in most cases our `<input>`s are going to need to perform some action when the users type -- and a `limit` for the amount of characters that a user can enter in the field. So although our presentational component is simple, it can still have a degree of interactivity through the addition of callbacks.

Now, of course, we can argue about whether wrapping the `<input>` field in this way is a good idea. After all, `<input>`s are nice simple implementations in their own right. But providing a component-based interface to text inputs as we have in the field above is potentially a great win for simplicity in our app. It specifically defines what we mean by a text input; it does so in a way that arguably covers the majority of use-cases we can imagine for a simple text input; and it provides this definition in one place that can be found and updated easily in the future. Win, win, win. Are we beginning to see the power of presentational components? Good.

Now imagine that it's not just the `TextField` that our team has executed in this way, but say we've also defined a `<Header />` and a `<Footer />`, as well as other more unique and customized modules that are still primarily presentational. Imagine further that we've composed the majority of our UI out of these simple presentational components -- all of them almost entirely stateless, all of them designed to do one thing and one thing well: they just receive `props` from their parent components and render! That's it. They are simple and beautiful and because they aren't doing much, because they are mostly stateless, they have a better chance of remaining blissfully bug free!

This is the power and importance of presentational components. They are simple and they just work. So therefore we should strive to use them as much as possible.

### The "Stateless Functional" Component & "Pure" Functions

What if I told you we can actually make our presentational components even simpler? Well we can, and here's why: Remember how one of the principles in our checklist for the presentational component pattern was that the component (probably) does not have state? Well, if in fact we can create a component that has no state, that means that our component doesn't even really need to be a JavaScript object of type `Component` at all. It can just be a simple function &mdash; one that takes an input and returns a (portion of) the UI.

So what's this look like? Here's our `TextField` component rendered as a so-called "functional stateless" component (a feature available in React since v0.14):

```javascript
const defaultLimit = 100

export default function TextField(props) {
  return (
    <input
      className="field field-light"
      onChange={this.props.onChange}
      limit={this.props.limit || defaultLimit} />
  );
}
```
Now isn't that just beautiful? It really is. It's just so concise. We've discarded all that ugly boilerplate. But it's not only concision that makes this beautiful. By transforming our component into a stateless function, we have made our `TextField` component an extremely stable and predictable part of our application.

The predictability comes from the fact -- and here we can see the influence of the principles of functional programming on React -- that this function will always return the same UI output if given the same `props`. There are no state variables here that could be set to different values at different times that might lead the function to return something that we didn't predict. What we have here, then, is what in functional terms is called a "pure" or "referentially transparent"  function.  Our UI has become just a bit more predictable. And, as web developers who've worked on the front-end, we know what a boon that is, don't we? (To review pure functions at greater length, see [this lesson](https://github.com/learn-co curriculum/javascript-pure-functions) on the theme.)

- ["Software Design Patterns"](https://en.wikipedia.org/wiki/Software_design_pattern) (Wikipedia)
- Dan Abramov, ["Presentational and Container Components"](https://medium.com/@dan_abramov/smart-and-dumb-components 7ca2f9a7c7d0#.quaiihhh3)
- [Stateless Functions](https://facebook.github.io/react/docs/reusable-components.html#stateless-functions)
