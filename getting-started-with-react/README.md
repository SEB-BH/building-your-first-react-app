<h1>
  <span class="headline">Building Your First React App</span>
  <span class="subhead">Getting Started with React</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to explore the React file structure created by Vite, and start the development server.

## Getting started with React

You just built your first React app! Congrats! We used a tool called [Vite](https://vite.dev/guide/) to help accomplish this. 

> 💡 Vite (French word for "quick", pronounced like "veet") is a build tool that aims to provide a faster and leaner development experience for modern web projects.

Vite gives us a couple of essential capabilities:

- A starting file structure.
- A development server.

## Default file structure

The three most essential files created by Vite are: `index.html`, `App.jsx`, and `main.jsx`. Let's explore how these files interact.

The entry point into our application is the `index.html` file located at the root of our project. You can see its contents below:

```html
<!-- index.html -->

<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/favicon.svg" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>first-react-app</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.jsx"></script>
  </body>
</html>
```

The `index.html` file has some familiar boilerplate and two elements in the body - a `<div>` with an `id` of `"root"` and a `<script>` that calls the `src/main.jsx` file. Let's check out that JSX file:

```jsx
// src/main.jsx

import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>,
)
```

In index.html, Vite created this element: `<div id="root"></div>`

This <div> is where the React app will appear.

In main.jsx, this line finds the element with the id "root":

```jsx
createRoot(document.getElementById('root'))
```

`createRoot()` tells React to take control of that element. React will manage everything displayed inside it.

We can then use `.render()` to place a React component (`<App />`) inside the root:

```jsx
createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App /> 
  </StrictMode>,
)
```

The React `root` is now rendering a single `App` component (ignore the `StrictMode` component for now), which is being imported from `src/App.jsx`:

```jsx
// src/App.jsx

const App = () => {

  return (
    <h1>Hello, world!</h1>
  )
}

export default App
```

You can begin to see how this app's pieces interact with one another. The `index.html` file loads the `main.jsx` file as the entry point to our React application, which itself renders the `App` component.

![Entry point](./assets/react-entry-point-v1.png)

## Running the development server

To start the development server and view our app in the browser, we'll use the following command:

```bash
npm run dev
```

You should see that `Vite` is available on port number 5173:

```plaintext
localhost:5173
```

Navigate there, and you should see the `Hello, world!` from our `App.jsx` component displayed! 

## Other files

Vite created a few other files and directories for us when we created this project. Some may be familiar to you, while others will not. In the project root, we have:

* `public` directory – stores static files, such as favicons and images, that Vite serves directly.
* `.oxlintrc.json` or `eslint.config.js` – configures the project’s linter. The linter checks your code and warns you about possible errors or problems.
* `.gitignore` – lists files and directories that Git should not track or send to GitHub, such as `node_modules` and `dist`.
* `vite.config.js` – contains configuration settings for Vite, including the React plugin.


You don't need to worry about the contents of these files for now, but they will be helpful down the road as you go on your React journey.

> 💡 **It's worth noting that we'll be doing the bulk of work with React in `App.jsx` along with other files we'll be creating in the future.**

<details>
  <summary>A Note on CSS</summary>

You may already notice some styling in the browser.

That styling is coming from `src/index.css`, which is imported near the top of `main.jsx`:

```jsx
import './index.css'
```

Because `index.css` is imported in `main.jsx`, its styles can affect the entire application.

We will explore CSS in React in a later lesson. For now, just remember that the default styling comes from `index.css`.


</details>