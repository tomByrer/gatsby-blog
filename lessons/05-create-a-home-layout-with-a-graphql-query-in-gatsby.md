# Create a Home Layout Component with a GraphQL Query in Gatsby

Inside your `src/pages` directory and review the [`index.js` file](https://github.com/eggheadio-projects/build-a-blog-with-react-and-markdown-using-gatsby/blob/master/lessons/05-create-a-home-layout-component-with-a-graphql-query-in-gatsby/src/pages/index.js).

```js
import React from "react"
import { StaticQuery, graphql } from 'gatsby'
```
The first 2 lines pull in 2 outside libs to help us create the home page.  `React` creates the HTML via JSX.  The 2 other functiions are helpers to use the `cgatsby-config.js`'s export as a data source.

At the bottom of the file:
```js
export default Layout 
```

Since this is the only export, `layout` is the only function all the other scripts outside see.  Ohter functions are consumed internally.

```js
const Layout = () => {
  return (
    <div>
      <Header />
    </div>
  )
}
```
Only thing `loyout` does here is wrap a simple `<div>` around the `<Header />` code returned above, & I'm not sure if that is needed; could use a fragment or export the header directly?

```js
const Header = () => {
  return (
    <StaticQuery
      query={graphql`
        query {
          site {
            siteMetadata {
              title
              description
            }
          }
        }
      `}
      render={data => <TitleAndDescription data={data} />}
    />
  )
}
```
`Header` has 2 simple tasks: make a GraphQL call to pull data from our `cgatsby-config.js`, then send it to `TitleAndDescription`.  Splitting the code up like this (composition) helps seperates conserns & increases readablity.

```js
const TitleAndDescription = ({data}) => {
  const title = data.site.siteMetadata.title
  const description = data.site.siteMetadata.description

  return (
    <div style={{
      display: 'flex',
      flexDirection: 'column',
      alignItems: 'center',
      fontFamily: 'avenir'
    }}>
      <h2 style={{marginBottom: 0}}>{title}</h2>
      <p style={{
        marginTop: 0,
        opacity: 0.5
      }}>
        {description}
      </p>
    </div>
  )
}
```
Most of the HTML and CSS styles live in `TitleAndDescription`.  The data from `Header`'s database call is displayed here.
