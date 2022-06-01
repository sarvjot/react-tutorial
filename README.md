# React Tutorial Notes

## Functional Components vs Class Components
- Learn [this](https://medium.com/byte-sized-react/what-is-this-in-react-25c62c31480) for Class Components

## I get the purpose of React, but why JSX?

- If we use vanilla React without using JSX, then our code will not be very declarative, rather we would be doing everything manually [creating elements by using React's *createElements()*]
- JSX and its corresponding Babel Transpiled Vanilla React Code: 

- JSX

```html
<div className="shopping-list">
  <h1>Shopping List for {props.name}</h1>
  <ul>
    <li>Instagram</li>
    <li>WhatsApp</li>
    <li>Oculus</li>
  </ul>
</div>;
```

- Plain React

```js
React.createElement(
	"div",
	{
		className: "shopping-list",
	},
	React.createElement("h1", null, "Shopping List for ", props.name),
	React.createElement(
		"ul",
		null,
		React.createElement("li", null, "Instagram"),
		React.createElement("li", null, "WhatsApp"),
		React.createElement("li", null, "Oculus")
	)
);
```

## Maintaining State in the Component Tree

- **Bad Practice**: Using children state in parent
	- This technique is a bad practice because it makes code difficult to understand and prone to bugs
- **Good Practice**: Maintaining the state in the parent component and passing it as props to children component
	- This way several sibling components can be synchronized. These children components whose state is controlled by the parent are also called as Controlled Components.

## Updating the State without Mutation

There are several benefits of this approach

- By not mutating, we **Preserve Previous States** which we can use in future to undo/redo
- **Detecting changes** in immutable objects is easier than mutable ones. In latter one we have to traverse the whole object tree to find the point of difference between the previous copy and the current one. However in former, we can straight-away compare their references
- As a result of previous point, React also finds it **easy to determine when to re-render** if we update without mutation (see [here](https://daveceddia.com/why-not-modify-react-state-directly/))