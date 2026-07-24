<h1>
  <span class="headline">Building Your First React App</span>
  <span class="subhead">JavaScript in JSX</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to display JavaScript values inside JSX.

## JavaScript in JSX

Curly braces let us use JavaScript values inside JSX.

Create a `task` object inside the `TaskList` component:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {
  const task = {
    text: 'Learn React',
    done: true
  }

  return (
    <section className="task-list">
      <h1>Task List</h1>
      <p>Tasks I want to complete</p>
      <hr />
    </section>
  )
}

export default TaskList
```

We can display the task's `text` property using curly braces:

```jsx
<p>{task.text}</p>
```

Update the component:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {
  const task = {
    text: 'Learn React',
    done: true
  }

  return (
    <section className="task-list">
      <h1>Task List</h1>
      <p>{task.text}</p>
    </section>
  )
}

export default TaskList
```

React evaluates the JavaScript inside the curly braces and displays the result.

We can place JavaScript expressions inside curly braces:

```jsx
<p>{2 + 2}</p>
<p>{task.text}</p>
<p>{task.done}</p>
```

However, Boolean values such as `true` and `false` are not displayed as text on the page.
