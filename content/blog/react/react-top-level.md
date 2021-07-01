---
title: 'Creating React Elements'
date: 2020-04-04 17:21:13
category: 'React'
draft: false
---

![](../../assets/react.svg)

The way we render a react element is very similar to doing something like `document.getElementById` and then appending our new element. At the highest level of any React project we start by passing JSX into the ReactDOM.render function like this:

```jsx
const element = <h1 className="heading">Hello, world</h1>
ReactDOM.render(element, document.getElementById('root'))
```

A core dependency of React is Babel. Under the hood, Babel transpiles that JSX and uses React's top level api to create a React Element with another function: `React.createElement()`.

This function takes in these params:

```jsx
React.createElement(type, [props], [...children])
```

So using that same example above, this...

```jsx
const element = <h1 className="heading">Hello, world</h1>
ReactDOM.render(element, document.getElementById('root'))
```

Will transpile into this:

```jsx
const element = /*#__PURE__*/ React.createElement(
  'h1',
  {
    className: 'heading',
  },
  'Hello, world'
)
ReactDOM.render(element, document.getElementById('root'))
```

Take a look at the [Babel output](https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=usage&spec=false&loose=false&code_lz=MYewdgzgLgBApgGzgWzmWBeGAeAFgRhmAQEMIIA5E1DAclzhIBMBLMAc1oD4AJRBEABoYAdxAAnBE2wB6AlwDcAKABKjYFAAiAeQCyAOnFomccQApEKNFGFMQwAK6p0-9nCgBRJM6gAhAJ4AkkxmtOIgIFC0AJTRCkA&debug=false&forceAllTransforms=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=false&presets=react&prettier=false&targets=&version=7.13.14&externalPlugins=) for more context.

You could almost say that at its core, React uses nothing but functions used to create a UI.
