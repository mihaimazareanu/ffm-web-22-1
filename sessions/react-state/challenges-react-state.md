# Challenges: React State

## Practice useState

Start by cloning this [template repository](https://github.com/actyvystom/challenge-react-usestate).

:exclamation: Don't forget to `npm install`!

### Active toggle

- Make the `App` component render the `ActiveToggle` component.
- Add an `active` state to the `ActiveToggle` component.
- When the state is active the box should be hotpink (add the CSS class `box--active`), otherwise it should be gray.
- When the state is active the button should say "Activate", otherwise it should say "Deactivate".
- When the user clicks the button the `active` state should be toggled.

### Shopping Cart

- Make the `App` component render the `ShoppingCart` component.
- Turn the `amount` variable in the `ShoppingItem` component into a state.
- When the user clicks the + / - button the amount should be increased / decreased.

## Bonus Challenge: Handling Form Submit

There is a form in which you enter your favourite holiday and its respective date.

Make sure that, on submit, both input values are saved in separate states.

[Use this Codesandbox](https://codesandbox.io/s/usestate-form-exercise-hul887?file=/src/App.js)
