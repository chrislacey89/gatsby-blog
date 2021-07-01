---
title: 'Lifting State in React'
date: 2021-04-17 12:21:13
category: 'React'
draft: false
---

![](../../assets/react.svg)

## A Quick Aside

I'm not sure if this is the best way to think about this, but this is how I make
sense of lifting the state. In this case we are going to be calling a function
from from where the component is defined to get a function from where the
component is being used. Here is what I mean...

For this exampled we will focus on the `FavoriteAnimal` component. Here is our
`FavoriteAnimal` component:

```jsx
function FavoriteAnimal({ animal, onAnimalChange }) {
  return (
    <div>
      <label htmlFor="animal">Favorite Animal: </label>
      <input id="animal" value={animal} onChange={onAnimalChange} />
    </div>
  )
}
```

Any time the input changes in our `FavoriteAnimal` component, we fire the
function `onAnimalChange`, which we get from our props.

Now let's take a look at our app component:

```jsx
function App() {
  const [name, setName] = React.useState('')
  const [animal, setAnimal] = React.useState('')

  return (
    <form>
      <Name name={name} onNameChange={event => setName(event.target.value)} />
      <FavoriteAnimal
        animal={animal}
        onAnimalChange={event => setAnimal(event.target.value)}
      />
      <Display name={name} animal={animal} />
    </form>
  )
}
```

Note that `onAnimalChange` sets the animal value in the state and passes that
value in as props back into the original component.

This process forms a sort of cycle. `FavoriteAnimal` calls a function when it is
change and lifts that up through the `onAnimalChange` prop. `FavoriteAnimal`
nested inside `App` takes that `onChange` function and uses it with the
`onAnimalChange` prop. The `onAnimalChange` prop updates the `animal` state and
passes that back into the `animal` prop, which is then read and used by the
`FavoriteAnimal` component.
