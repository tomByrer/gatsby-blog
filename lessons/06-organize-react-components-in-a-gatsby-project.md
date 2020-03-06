# Organize React Components in a Gatsby Project

As you can see from the last lesson our `index.js` file was starting to get a little crowded. Now is a great time to go ahead and implment a little organization.

Inside of your `src` folder create a new folder called `components`.

Inside the components folder create a new file called `Header.js`. Go ahead and copy the Header component that we defined in our index.js file into the Header.js file.  Add:
```js
export default Header
```
at the end of the file

Add import for Header inside our index.js file (Use VSCode's autocomplete) & remove the unnneded `import { StaticQuery, graphql } from 'gatsby'`.

Check your page it should still work as before.
