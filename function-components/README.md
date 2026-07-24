<h1>
  <span class="headline">Building Your First React App</span>
  <span class="subhead">Function Components</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to create, export, import, and use a React function component.

## Function components

A React component is a reusable part of the user interface.

A function component is a JavaScript function that returns JSX.

In this lesson, we will create a `TaskList` component and display it inside `App`.

### Step 1: Create the component file

Inside `src`, create a new folder named `components`.

Inside that folder, create:

```text
TaskList.jsx
```

Your project should now include:

```text
src
├── components
│   └── TaskList.jsx
├── App.jsx
└── main.jsx
```

### Step 2: Define the component

Add a function named `TaskList`:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {

}
```

Component names must begin with a capital letter.

The capital `T` tells React that `TaskList` is a component.

### Step 3: Return JSX

Return the content that the component should display:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {
  return (
    <h1>Task List</h1>
  )
}
```

The JSX inside the `return` will appear on the page.

### Step 4: Export the component

Export `TaskList` so it can be used in another file:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {
  return (
    <h1>Task List</h1>
  )
}

export default TaskList
```

### Step 5: Import the component into `App`

Replace the contents of `App.jsx` with:

```jsx
// src/App.jsx

import TaskList from './components/TaskList.jsx'

const App = () => {
  return (
    <main>
      <TaskList />
    </main>
  )
}

export default App
```

This line imports the component:

```jsx
import TaskList from './components/TaskList.jsx'
```

We then display it using a self-closing component tag:

```jsx
<TaskList />
```

Open the browser. You should see:

```text
Task List
```