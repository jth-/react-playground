# Step Two: Props and State
## Getting Dynamic
Just rendering components is kind of cool, but you can do that from the server already with languages like Twig and Nunjucks. What sets React apart from server-size options like those is its ability to update data in the component on the fly. It does this using two properties of every React component: (1) `props` and (2) `state`.

## Props are Permanent
The basic difference between `props` and `state` are that `props` are permanent (immutable), meaning that their values are set once and then never changed. You set these values when you call the component (either in   `ReactDOM.render` or within another component):
```js
  var Component = React.createClass({
    render: function(){
      var title = this.props.title;
      return (
        <h2>{title}</h2>
      )
    }
  })

  ReactDOM.render(
    <Component title="My Awesome Title" />,
    document.getElementById('app-mount')
  )
```

## State is Dynamic
Unlike `props`, `state` is meant to represent dynamic values within your component. Its value is dynamic or mutable. It might be wether or not a button has been clicked or how many times that button has been clicked. It might also represent the input of a user from a text input like the following example. Note the introduction of a few methods: `getIntialState` and `setState`:
```js
var Component = React.createClass({
  getInitialState: function(){
    // Here we set what the original
    // value of this component's state should be.
    return {text: 'Some Text'}
  },
  inputChange: function(e){
    // To update the state, we use
    // the `setState` method.
    this.setState({text: e.target.value});
  },
  render: function(){
    return (
      <div>
        <input type="text" onChange={this.inputChange} />
        <p>{this.state.text}</p>
      </div>
    )
  }
});

ReactDOM.render(
  <Component title="My Cool Props Title" />,
  document.getElementById('app-mount')
)
```

## Now It's Your Turn
Using our `index.html`, create a component that accepts any `prop` and displays it. Also create  a button that increments a count and displays that count using `state`.
