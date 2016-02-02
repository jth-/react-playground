# Step Three: Multiple Components
## Getting Coordinated
While state-management frameworks exist for when applications begin to scale, there are times when components can have a relationship to each other that is simple to express. This is usually demonstrated through the familiar DOM notions of parents and children. In React, this looks a lot like nested DOM elements:
```js
  //...
  render: function(){
    return (
      <Parent>
        <Child />
      </Parent>
    )
  }
  //...
```
 React goes a step further, however, and treats this relationship as ownership, meaning that the parent component can set the `props` of a child component. Also notice that we can simply insert other React elements within our render function instead of mounting it to a DOM element through `ReactDOM.render`.

## Now It's Your Turn
Taking our counter example from before, created a nested component within your component that combines a `prop` from the parent as well as the count from the parents `state`.
