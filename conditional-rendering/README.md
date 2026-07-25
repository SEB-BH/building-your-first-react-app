<h1>
  <span class="headline">Building Your First React App</span>
  <span class="subhead">Conditional Rendering</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to use a ternary expression to conditionally display JSX.

## Conditional rendering

Conditional rendering means displaying different content based on a condition.

Our task has a `done` property:

```jsx
const task = {
  text: 'Learn React',
  done: true
}
```

We want completed tasks to include the words `Task Completed`.

We cannot place an `if...else` statement directly inside JSX.
<details>
  <summary>Why?</summary>

JSX only accepts JavaScript expressions inside curly braces.

An expression produces a value:

<code>
{task.done ? 'Complete' : 'Incomplete'}
</code>

An `if...else` is a statement. It performs an action, but it does not return a value directly inside JSX.

You can still use `if...else` before the `return`, then display the result in JSX.

</details>

<br />

Instead, we can use a ternary expression `condition ? valueIfTrue : valueIfFalse`:

```jsx
{task.done ? 'Complete' : 'Incomplete'}
```

Use `task.done` as the condition:

```jsx
<p>{task.done ? `✅ ${task.text}`: task.text}</p>
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

      <p>{task.done ? `✅ ${task.text}`: task.text}</p>
    </section>
  )
}

export default TaskList
```

When `task.done` is `true`, the page displays:

```text
Task Completed: Learn React
```

When `task.done` is `false`, the page displays:

```text
Learn React
```



<details>
  <summary>What does this code look like without a ternary?</summary>


<code>
const TaskList = () => {

    const task = {
        text: 'Learn React',
        done: true
    }

    let taskDisplay = '' 

    if (task.done === true) {
        taskDisplay = `✅ ${task.text}`
    } else {
        taskDisplay = task.text
    }

    return (
        <>
            <section className="taskList">
                <h1>Task List</h1>
                <p>{taskDisplay}</p>
                <hr />
            </section>
        </>
    )
}

export default TaskList
</code>

</details>