<h1>
  <span class="headline">Styling in React</span>
  <span class="subhead">Inline Styles</span>
</h1>

**Learning objective:** By the end of this lesson, students will be able to add static and dynamic inline styles to JSX elements.

## Inline styles

Inline styles let us add CSS directly to a JSX element.

In HTML, an inline style looks like this:

```html
<h1 style="color: blue">Task List</h1>
```

In JSX, the `style` attribute receives a JavaScript object:

```jsx
<h1 style={{ color: 'blue' }}>Task List</h1>
```

The outer curly braces let us use JavaScript inside JSX.

The inner curly braces create an object containing the styles:

```jsx
style={{ color: 'blue' }}
```

## CSS properties use camel case

CSS properties containing a dash must be written in camel case.

For example, `background-color` becomes `backgroundColor`:

```jsx
<h1
  style={{
    color: 'white',
    backgroundColor: 'navy'
  }}
>
  Task List
</h1>
```

Other examples include:

```text
font-size        → fontSize
text-align       → textAlign
border-radius    → borderRadius
text-decoration  → textDecoration
```

Values that include a unit are normally written as strings:

```jsx
<section
  style={{
    maxWidth: '500px',
    margin: '0 auto',
    padding: '20px'
  }}
>
  {/* Content */}
</section>
```

## Dynamic inline styles

Because the style object is JavaScript, its values can change based on data.

The following code adds a line through completed tasks:

```jsx
{tasks.map((task) => (
  <li
    key={task.id}
    style={{
      textDecoration: task.done ? 'line-through' : 'none'
    }}
  >
    {task.text}
  </li>
))}
```

When `task.done` is `true`, `textDecoration` receives the value `'line-through'`.

When it is `false`, it receives `'none'`.

## Shorthand

```jsx
style={{ textDecoration }}
```

is shorthand for:

```jsx
style={{ textDecoration: textDecoration }}
```

The variable name becomes the CSS property, and its current value becomes the property's value.

> 💡 **Inline styles are useful when a style depends on data. We will continue to use CSS files for most layout and visual styling.**
