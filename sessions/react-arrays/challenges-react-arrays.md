# Challenges: React Arrays

## Exercise 1

[start here](https://codesandbox.io/s/react-arrays-exercise-fruits-start-1ht6lf)

- Create an array 'fruits'. It should contain at least 5 objects which all have the propteries 'name', 'id', 'color', e.g.:
  ```
  {
    id: 1337,
    name: 'Banana',
    color: 'yellow',
  }
  ```
  (Hint: the ids need to be unique.)
- Use the array method `map` to create a Card component for each fruit in your array. Use the name of each object as the text of the component and the id as the key prop.

- Extra: Change the `Card` component such that it receives a `color` prop and set the border color of the Card to that value. Use the color property of each fruit object for this prop.

## Exercise 2

[start here](https://codesandbox.io/s/react-arrays-exercise-start-qicf8l)

- Use map to create a Card for each user in the USERS array.
- Add a unique key to each Card.
- Inside the card component: use map to create a Tag for each role in the roles array of a user.
- Adapt the Tag component so that the tag receives an additional class called 'tag--highlight' if the tag equals the string 'admin'. (See Tag.css)
