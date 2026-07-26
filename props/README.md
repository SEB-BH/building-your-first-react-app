<h1>
  <span class="headline">Building Your First React App</span>
  <span class="subhead">Props</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to pass props to a component, destructure props, and spread an object into props.

## Props

Props let a parent component send information to a child component.

We will create a `Task` component and use it inside `TaskList`.

Our component structure will look like this:

```text
App
└── TaskList
    └── Task
```

## Create the `Task` component

Inside `src/components`, create a new file:

```text
Task.jsx
```

Add a `Task` component:

```jsx
// src/components/Task.jsx

const Task = () => {
  return (
    <li>Task</li>
  )
}

export default Task
```

## Pass a prop

Import `Task` into `TaskList.jsx`:

```jsx
// src/components/TaskList.jsx

import Task from './Task.jsx'
```

We can pass information to the component using an attribute:

```jsx
<Task text="Learn React" />
```

Here, `text` is a prop.

## Receive props

React collects the props into an object and passes it to the component:

```jsx
// src/components/Task.jsx

const Task = (props) => {
  console.log(props)

  return (
    <li>{props.text}</li>
  )
}

export default Task
```

The `props` object looks like this:

```js
{ text: 'Learn React' }
```

We use dot notation to access the `text` prop:

```jsx
{props.text}
```

## Destructure props

Instead of repeatedly writing `props.text`, we can destructure the props object:

```jsx
const Task = (props) => {
  const { text } = props

  return (
    <li>{text}</li>
  )
}
```

We can make this shorter by destructuring directly in the function parameters:

```jsx
// src/components/Task.jsx

const Task = ({ text }) => {
  return (
    <li>{text}</li>
  )
}

export default Task
```


## Use props with `.map()`

Our `TaskList` component has an array of tasks:

```jsx
const tasks = [
  { id: 1, text: 'Learn JavaScript', done: true },
  { id: 2, text: 'Learn JSX', done: false },
  { id: 3, text: 'Learn React', done: false }
]
```

We can use `.map()` to render a `Task` component for each object:

```jsx
// src/components/TaskList.jsx

import Task from './Task.jsx'

const TaskList = () => {
  const tasks = [
    { id: 1, text: 'Learn JavaScript', done: true },
    { id: 2, text: 'Learn JSX', done: false },
    { id: 3, text: 'Learn React', done: false }
  ]

  return (
    <section className="task-list">
      <h1>Task List</h1>

      <ul>
        {tasks.map((task) => (
          <Task
            key={task.id}
            text={task.text}
            done={task.done}
          />
        ))}
      </ul>
    </section>
  )
}

export default TaskList
```

Each `Task` receives its own `text` and `done` values.

We can destructure more than one prop:

```jsx
const Task = ({ text, done }) => {
  return (
    <li>
      {done ? '✅' : '⬜'} {text}
    </li>
  )
}
```

## Spread props

The properties in each task object have the same names as our props:

```js
{
  id: 1,
  text: 'Learn JavaScript',
  done: true
}
```

Instead of passing each property separately, we can spread the object:

```jsx
<Task
  key={task.id}
  {...task}
/>
```

The spread syntax passes each property as a separate prop.

This:

```jsx
<Task
  text={task.text}
  done={task.done}
/>
```

can be shortened to:

```jsx
<Task {...task} />
```

Update `TaskList`:

```jsx
// src/components/TaskList.jsx

import Task from './Task.jsx'

const TaskList = () => {
  const tasks = [
    { id: 1, text: 'Learn JavaScript', done: true },
    { id: 2, text: 'Learn JSX', done: false },
    { id: 3, text: 'Learn React', done: false }
  ]

  return (
    <section className="task-list">
      <h1>Task List</h1>

      <ul>
        {tasks.map((task) => (
          <Task
            key={task.id}
            {...task}
          />
        ))}
      </ul>
    </section>
  )
}

export default TaskList
```

The `Task` component can destructure the props it needs:

```jsx
// src/components/Task.jsx

const Task = ({ text, done }) => {
  return (
    <li>
      {done ? '✅' : '⬜'} {text}
    </li>
  )
}

export default Task
```

> 💡 The `key` is used by React to track the list item. It is not passed to `Task` as a regular prop.

## Props flow in one direction

**Props are passed from a parent component to a child component:**

```text
TaskList → Task
```

The child component can use its props, but it should not change them.
