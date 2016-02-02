# Step One: Just the Basics
## What is React?
React.js is a UI building library from Facebook that tends to be used as the View layer in a typical Model-View-Controller stack. Here's what React is really good at in a few bullet points:
* Creating re-usable UI components
* Updating the UI efficiently based on changes to data

## Getting React up and Running.
In this branch, you'll find a simple `index.html` file that gets React up and running in a project really quickly. In the head of that file, you'll find the following:
```html
<head>
  <!-- Bring in two React files located in our /js folder -->
  <script src="js/react.js"></script>
  <script src="js/react-dom.js"></script>
  <!-- Because React syntax isn't native to the browser, we'll need a transpiler in the form of Babel -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>
</head>
```
You'll notice that we're bringing in two React libraries: (1) the standard React library and (2) the React DOM library which loosely represent the two parts of working with React: (1) defining components and (2) rendering those components in the DOM.

You'll also notice in the `index.html` that there's a `script` tag in the body with the type set to `text/babel` which lets our transpiler, Babel, know that we want this block transpiled:
```html
<body>
  <div id="app-mount"></div>
  <script type="text/babel">
  </script>
</body>
```
To get started with using React, we'll use the script tag to create out first component and render it. To create a component, we'll use the `.createClass` method included on the React object (available to us thanks to our included script tags):
```html
<script type="text/babel">
  var Component = React.createClass({
    render: function(){
      return (
        // Anything we add here will render once
        // we include our component through ReactDOM
      )
    }
  });
</script>
```

The central part of any React component is the `render` method that is passed into the options object that goes into the `.createClass`. We're going to use a syntax call JSX that comes with React (and thanks to Babel we can use it in the browser). It's a bit like XML except that we're rendering it in Javascript which means we can do some Javascript like things within it like call functions, check logic and use variables. You can read more about JSX [here](https://facebook.github.io/react/docs/jsx-in-depth.html).

Here's what that could look like in our example above:

```html
<script type="text/babel">
  var Component = React.createClass({
    render: function(){
      var active = true;
      var title = "This is my title";
      return (
        // To run JS expressions, we use curly braces: {}
        // Note the use of 'className' as class is a reserve keyword in JS.
        <div className={active ? 'active' : 'inactive'}>
          <h2>{title}</h2>
        </div>
      )
    }
  });
</script>
```

So far, we've made components, but we haven't actually got them into the DOM. To do that, we'll use `ReactDOM.render` to render our defined component:
```html
<script type="text/babel">
  var Component = React.createClass({
    render: function(){
      return (
        <h2>"This is my title"</h2>
      )
    }
  });

  ReactDOM.render(
    <Component />,
    document.getElementById('app-mount')
  )
</script>
```
Notice that our `render` method takes two arguments: (1) a defined component and (2) a DOM element where we should render that component.

## Now It's Your Turn
Using our `index.html`, create a simple React component that renders some html element(s) on the div with the id `app-mount`. Try to make sure that you're rendering multiple html elements.
