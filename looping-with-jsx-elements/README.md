<h1>
  <span class="headline">Building Your First React App</span>
  <span class="subhead">Looping with JSX</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to use `map()` to create JSX elements from an array.

## Looping with JSX

Most applications display lists of data.

Replace the single `task` object with a `tasks` array:

```jsx
const tasks = [
  { id: 1, text: 'Learn JavaScript', done: true },
  { id: 2, text: 'Learn JSX', done: false },
  { id: 3, text: 'Learn HTML', done: true },
  { id: 4, text: 'Learn CSS', done: true },
  { id: 5, text: 'Learn React', done: false }
]
```

We can use `map()` to turn each task into an `<li>` element:

```jsx
{tasks.map((task) => (
  <li>{task.text}</li>
))}
```

Add this inside a `<ul>`:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {
  const tasks = [
    { id: 1, text: 'Learn JavaScript', done: true },
    { id: 2, text: 'Learn JSX', done: false },
    { id: 3, text: 'Learn HTML', done: true },
    { id: 4, text: 'Learn CSS', done: true },
    { id: 5, text: 'Learn React', done: false }
  ]

  return (
    <section className="task-list">
      <h1>Task List</h1>

      <ul>
        {tasks.map((task) => (
          <li>{task.text}</li>
        ))}
      </ul>
    </section>
  )
}

export default TaskList
```

Check the browser. Each task should appear as a list item.

### Add a key

React needs a unique `key` for each element created with `map()`.

Our tasks already have unique IDs:

```jsx
{ id: 1, text: 'Learn JavaScript', done: true }
```

Use the task's ID as its key:

```jsx
{tasks.map((task) => (
  <li key={task.id}>{task.text}</li>
))}
```

The completed component should look like this:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {
  const tasks = [
    { id: 1, text: 'Learn JavaScript', done: true },
    { id: 2, text: 'Learn JSX', done: false },
    { id: 3, text: 'Learn HTML', done: true },
    { id: 4, text: 'Learn CSS', done: true },
    { id: 5, text: 'Learn React', done: false }
  ]

  return (
    <section className="task-list">
      <h1>Task List</h1>

      <ul>
        {tasks.map((task) => (
          <li key={task.id}>{task.text}</li>
        ))}
      </ul>
    </section>
  )
}

export default TaskList
```

A key helps React keep track of each item in the list.
