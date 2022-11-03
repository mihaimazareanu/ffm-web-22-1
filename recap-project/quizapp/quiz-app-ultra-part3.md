## Quiz App Ultra - Part 3

In this challenge your Quiz App will get different pages. The user will see different pages by clicking on the navigation.

### Part 3a - Lifting the page state up

If we want to change the page in the `App` component, we need the `page` state (the state that is currently in the `Navigation` component) in the `App` component.

- Lift the `page` state up from the `Navigation` component into the `App` component.
- Hand down the state and a function that manipulates the state from the `App` component to the `Navigation` component via props.
- The `Navigation` component should use these props just like it used the state earlier.

### Part 3b - Creating multiple page components

- Create a `pages` folder next to the `components` folder. Create a `Cards` component inside the `pages` folder. The `Cards` component should take a `cards` array as a prop and render the cards using the `Card` component.
- Use the `Cards` component inside the `App` component instead of rendering all cards directly in the `App` component. Your `App`component could look like this after this step:

  ```js
  function App() {
    const [page, setPage] = useState("home");

    return (
      <div className="app">
        <Header />
        <main className="app__main">
          <Cards cards={cards} />
        </main>
        <Navigation page={page} setPage={setPage} />
      </div>
    );
  }
  ```

- Create a `Profile` component and a `Create` component inside the `pages` folder. These two components should only return a simple static disclaimer saying "Profile / Create page is currently under construction" or something similar.
- Use conditional rendering to render:
  - the `Cards` component when the user is on the "home" or the "bookmark" page
  - the `Create` component when the user is on the "create" page
  - the `Profile` component when the user is on the "profile" page

### Part 3c - Bookmarked cards

- Add a `isBookmarked` property to your `card` objects. Set some cards to be bookmarked and some cards to be not bookmarked (`true` / `false`).
- Hand over the `isBookmarked` property of each card to the `Card` component as a prop. Use the new prop in the `Card` component to show whether the card is bookmarked or not through the styling of the bookmark button.
- Use the `isBookmarked` prop of the `card` objects, so that the user sees all cards when they are on the "home" page and only bookmarked cards when they are on the "bookmark" page.
