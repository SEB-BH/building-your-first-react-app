<h1>
  <span class="headline">Building Your First React App</span>
  <span class="subhead">JSX Fundamentals</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to write JSX inside a React component.

## JSX fundamentals

JSX lets us write HTML-like markup inside JavaScript.

We will continue working inside `TaskList.jsx`.

### Return one parent element

A component must return one parent element.

This will cause an error:

```jsx
return (
  <h1>Task List</h1>
  <p>Tasks I want to complete</p>
)
```

The `<h1>` and `<p>` are separate elements.

We can wrap them in a React Fragment:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {
  return (
    <>
      <h1>Task List</h1>
      <p>Tasks I want to complete</p>
    </>
  )
}

export default TaskList
```

Fragments are written using:

```jsx
<>
</>
```

They group elements without adding another HTML element to the page.

### Close every tag

Every JSX tag must be closed.

Elements without content use a `/`:

```jsx
<hr />
```

Add an `<hr />` to the component:

```jsx
const TaskList = () => {
  return (
    <>
      <h1>Task List</h1>
      <p>Tasks I want to complete</p>
      <hr />
    </>
  )
}

export default TaskList
```

### Use `className`

In HTML, we use `class` ❌:

```html
<section class="task-list"></section>
```

In JSX, we use `className` ✅:

```jsx
<section className="task-list"></section>
```

We can use a `<section>` as the parent element instead of a Fragment:

```jsx
// src/components/TaskList.jsx

const TaskList = () => {
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