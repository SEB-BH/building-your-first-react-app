<h1>
  <span class="headline">Building Your First React App</span>
  <span class="subhead">Conditional Rendering in Loops</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to conditionally change each item created with `map()`.

## Conditional rendering in loops

We can combine `map()` with a ternary expression.

For each task, we will display:

* `✅` when the task is complete
* `⬜` when the task is incomplete

Add the ternary inside each `<li>`:

```jsx
{tasks.map((task) => (
  <li key={task.id}>
    {task.done ? '✅' : '⬜'} {task.text}
  </li>
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
          <li key={task.id}>
            {task.done ? '✅' : '⬜'} {task.text}
          </li>
        ))}
      </ul>
    </section>
  )
}

export default TaskList
```

Run the app and check the result. Each task should now show whether it is complete.
