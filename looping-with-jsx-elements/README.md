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
  'Learn JavaScript',
  'Learn JSX',
  'Learn HTML',
  'Learn CSS',
  'Learn React',
]
```

We can use `map()` to turn each task into an `<li>` element:

```jsx
  {tasks.map((task) => (
    <li>{task}</li>
  ))}
```

Check the browser. Each task should appear as a list item.

Replace the `tasks` array of strings with an array of objects (this more closely resembles the data we'll be working with in the future):

```jsx
const tasks = [
  { id: 1, text: 'Learn JavaScript', done: true },
  { id: 2, text: 'Learn JSX', done: false },
  { id: 3, text: 'Learn HTML', done: true },
  { id: 4, text: 'Learn CSS', done: true },
  { id: 5, text: 'Learn React', done: false }
]
```

We can contineu tp use `map()` to turn each task into an `<li>` element:

```jsx
  {tasks.map((task) => (
    <li>{task.text}</li>
  ))}
```

We should wrap this with a `<ul>`:

```jsx
<ul>
  {tasks.map((task) => (
    <li>{task.text}</li>
  ))}
</ul>
```

Check the browser. Each task should appear as a list item.

### Add a key

React needs a unique `key` for each element created with `map()`.
<details>
  <summary>Why?</summary>

    Keys help React identify each item in a list.

    When the list changes, React uses the keys to determine which items were added, removed, or updated.

    Without keys, React may have trouble matching each item to the correct element.

    Use a unique and stable value, such as an ID.

    Avoid using the array index when a unique ID is available.

    ❌👇
    
    {tasks.map((task, idx) => (
      <li key={idx}>{task.text}</li>
    ))}
    

</details>

<br />

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
