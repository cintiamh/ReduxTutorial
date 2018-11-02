# Getting Started with Redux

https://egghead.io/courses/getting-started-with-redux

*State* / State Tree

The state tree is *read only*.

To make changes, you need to dispatch an *action*.

Action has a type.

```javascript
{
  type: "INCREMENT"
}
```

* Pure functions - no side effects
  * same arguments, same output - predictable
* Impure functions - has side effects
  * calls to DB, API, etc.

Reducer: pure function that takes the previous state and an action and outputs the next state.

Reducer example
```javascript
const counter = (state = 0, action) => {
  switch (action.type) {
    case 'INCREMENT':
      return state + 1;
    case 'DECREMENT':
      return state - 1;
    default:
      return state;
}

// Store
const { createStore } = Redux;
const store = createStore(counter);

const render = () => {
  document.body.innerText = store.getState();
};

store.subscribe(render);
render();

document.addEventListener('click', () => {
  store.dispatch({ type: 'INCREMENT' });
})
```
