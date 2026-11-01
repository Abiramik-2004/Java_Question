# 🚀 React JS Interview Preparation — Complete 60-Minute Crash Course

## ⏰ Your 60-Minute Study Plan

| Time | Topic | What you'll learn |
|---|---|---|
| 0–5 min | React Fundamentals | What React is, why it's used, JSX |
| 5–12 min | Components and JSX | How to create and reuse components |
| 12–20 min | Props and State | Passing data and updating the UI |
| 20–30 min | Events and Hooks | `useState`, event handling, conditional rendering |
| 30–38 min | Lists and Forms | `map()`, keys, controlled inputs |
| 38–45 min | `useEffect` and APIs | Side effects and fetching data |
| 45–52 min | React Coding Practice | Counter, form, list, search |
| 52–60 min | Mock Interview | Common questions and coding exercises |

**Your priority:** Components, props, state, hooks, event handling, and coding practice. These are the foundations you should be able to explain and demonstrate.

---

# 1. What Is React? (0–5 Minutes)

## Interview Question 1: What is React?

**Answer:**

React is an open-source JavaScript library used to build user interfaces, especially interactive web applications. It allows developers to create reusable UI components and update the interface when data changes.

React was originally developed at Facebook, now Meta.

### Why Do We Use React?

Imagine you're building an online shopping website.

You have:
- A navigation bar
- A product list
- Product cards
- A shopping cart
- A login form

Instead of writing all the UI in one large file, React lets you divide it into reusable components.

For example:

```text
App
 ├── Navbar
 ├── ProductList
 │    ├── ProductCard
 │    ├── ProductCard
 │    └── ProductCard
 └── Footer
```

Each component handles a specific part of the UI.

### Important React Features

| Feature | Simple explanation |
|---|---|
| Components | Reusable pieces of UI |
| JSX | Syntax for describing UI using JavaScript |
| Props | Pass data from a parent component to a child |
| State | Data that a component can manage and update |
| Hooks | Functions that let components use React features |
| Virtual DOM | An implementation concept React uses to help update the UI efficiently |
| One-way data flow | Data typically flows from parent components to children through props |

### Interview Question: Is React a Framework or a Library?

React is a **JavaScript library** focused on building user interfaces. Additional libraries are commonly used for routing, server communication, and other application needs.

---

# 2. Create Your First React Component (5–12 Minutes)

Let's begin with the most important concept: a component.

## 2.1 What Is a Component?

A component is a reusable piece of UI.

For example, a welcome message can be a component.

```jsx
function Welcome() {
    return <h1>Hello, Abirami!</h1>;
}

export default Welcome;
```

Let's understand every line.

### Line 1

```jsx
function Welcome() {
```

Creates a JavaScript function named `Welcome`.

In React, a function component typically starts with a capital letter.

### Line 2

```jsx
return <h1>Hello, Abirami!</h1>;
```

Returns the UI that React should display.

### Line 3

```jsx
export default Welcome;
```

Makes the component available for importing into another module.

### How Do You Use This Component?

In `App.jsx`:

```jsx
import Welcome from "./Welcome";

function App() {
    return (
        <div>
            <Welcome />
        </div>
    );
}

export default App;
```

Output on the webpage:

**Hello, Abirami!**

### Understand the Relationship

```text
App.jsx
   |
   v
Welcome component
   |
   v
Displays the heading
```

`App` uses `Welcome` as a child component.

### Interview Question: What Is a Functional Component?

A functional component is a JavaScript function that returns React UI, usually written using JSX.

---

## 2.2 What Is JSX?

JSX stands for **JavaScript XML**.

It allows you to write HTML-like syntax inside JavaScript.

Example:

```jsx
function App() {
    const name = "Abirami";

    return <h1>Hello, {name}</h1>;
}
```

Output:

```text
Hello, Abirami
```

Notice these curly braces:

```jsx
{name}
```

They allow you to use a JavaScript expression inside JSX.

### Example: Perform a Calculation

```jsx
function App() {
    const a = 10;
    const b = 20;

    return <h1>Sum: {a + b}</h1>;
}
```

Output:

```text
Sum: 30
```

### Important JSX Rules

**Rule 1: Return one parent element.**

Correct:

```jsx
return (
    <div>
        <h1>Hello</h1>
        <p>Welcome</p>
    </div>
);
```

You can also use a fragment:

```jsx
return (
    <>
        <h1>Hello</h1>
        <p>Welcome</p>
    </>
);
```

Incorrect:

```jsx
return (
    <h1>Hello</h1>
    <p>Welcome</p>
);
```

The second example has adjacent elements without a common parent.

**Rule 2: Use `className` instead of `class`.**

```jsx
<h1 className="title">Hello</h1>
```

**Rule 3: JavaScript expressions go inside `{}`.**

```jsx
<p>{10 + 20}</p>
```

**Rule 4: Close JSX tags.**

```jsx
<img src="/image.png" alt="Example" />
```

### Interview Question: What Is the Difference Between HTML and JSX?

HTML is a markup language used to structure web content. JSX is a syntax extension for JavaScript that lets you describe UI in a way that resembles HTML. JSX is transformed into JavaScript that React can use.

---

# 3. Props and State (12–20 Minutes)

These are among the most important React interview topics.

## 3.1 What Are Props?

Props allow a parent component to pass data to a child component.

Think of props as information supplied to a component.

### Example

```jsx
function Welcome(props) {
    return <h1>Hello, {props.name}</h1>;
}

function App() {
    return (
        <div>
            <Welcome name="Abirami" />
            <Welcome name="Priya" />
        </div>
    );
}

export default App;
```

Output:

```text
Hello, Abirami
Hello, Priya
```

### Understand the Code

This is the parent component:

```jsx
function App() {
```

It passes data to `Welcome`:

```jsx
<Welcome name="Abirami" />
```

The child receives the value through `props`:

```jsx
function Welcome(props) {
```

It displays the value:

```jsx
{props.name}
```

### A Cleaner Way: Destructuring Props

You'll often see this style in interviews and real projects.

```jsx
function Welcome({ name }) {
    return <h1>Hello, {name}</h1>;
}
```

It does the same thing.

### Interview Question: Can We Modify Props?

Props are read-only from the receiving component's perspective. A child should not directly modify its props. Instead, the parent can supply new props or pass a callback that allows the child to request an update.

**Remember:** Props are for receiving data. They are not the component's own mutable state.

---

## 3.2 What Is State?

State is data that a component manages and that can change over time.

For example:
- Counter value
- Input text
- Whether a menu is open
- Whether a user is logged in
- Whether data is loading

React provides the `useState` hook to manage state in function components.

### Example: Counter

```jsx
import { useState } from "react";

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <h1>Count: {count}</h1>

            <button onClick={() => setCount(count + 1)}>
                Increase
            </button>
        </div>
    );
}

export default Counter;
```

This is a very important program. Let's understand it carefully.

### Line 1: Import the Hook

```jsx
import { useState } from "react";
```

Imports React's `useState` hook.

### Line 2: Create State

```jsx
const [count, setCount] = useState(0);
```

This is array destructuring.

| Part | Meaning |
|---|---|
| `count` | Current state value |
| `setCount` | Function used to update the state |
| `useState(0)` | Initializes the state to `0` |

Initially:

```text
count = 0
```

When the user clicks the button:

```jsx
setCount(count + 1)
```

React schedules the state update and renders the component again with the updated value.

### What Happens When You Click?

```text
Initial state: 0
      |
      v
User clicks Increase
      |
      v
setCount(1)
      |
      v
React renders updated UI
      |
      v
Count: 1
```

The same process happens with subsequent clicks.

### Interview Question: Why Do We Use `useState`?

`useState` allows a function component to store changing data. When the state is updated, React can render the component again to reflect the new value.

### Important Rule

Don't update state by assigning directly to the state variable.

Incorrect:

```jsx
count = count + 1;
```

Correct:

```jsx
setCount(count + 1);
```

React needs to be informed about the state update through the setter.

---

## 3.3 Props vs State

Memorize this table.

| Props | State |
|---|---|
| Passed into a component | Managed by a component |
| Read-only to the receiving component | Updated using a state setter or another appropriate React mechanism |
| Used to pass information between components | Used to store changing data |
| Changes when the parent supplies new values | Changes when the component updates its state |

**Interview answer:**

Props are used to pass data from a parent component to a child, whereas state stores data that a component manages and can update over time.

---

# 4. Events, Conditional Rendering, and Hooks (20–30 Minutes)

## 4.1 Event Handling

An event is an action such as a click, typing, or form submission.

In React, you handle events using props such as `onClick` and `onChange`.

### Example

```jsx
function App() {
    function handleClick() {
        alert("Button clicked!");
    }

    return (
        <button onClick={handleClick}>
            Click Me
        </button>
    );
}

export default App;
```

### Understand This Line

```jsx
<button onClick={handleClick}>
```

It tells React to call `handleClick` when the button is clicked.

Notice that we write:

```jsx
onClick={handleClick}
```

We don't write:

```jsx
onClick={handleClick()}
```

The second version calls the function during rendering rather than passing the function as an event handler.

### Interview Question: How Does React Handle Events?

React supports event handlers such as `onClick`, `onChange`, and `onSubmit`. We pass a function to the relevant event prop, and React invokes it when the event occurs.

---

## 4.2 Conditional Rendering

Conditional rendering means displaying UI depending on a condition.

### Example: Login Status

```jsx
function App() {
    const isLoggedIn = true;

    return (
        <div>
            {isLoggedIn ? (
                <h1>Welcome Back!</h1>
            ) : (
                <h1>Please Login</h1>
            )}
        </div>
    );
}

export default App;
```

Because `isLoggedIn` is `true`, the page displays:

```text
Welcome Back!
```

### Using `&&`

You can also display something only when a condition is true.

```jsx
function App() {
    const isLoggedIn = true;

    return (
        <div>
            {isLoggedIn && <h1>Welcome Back!</h1>}
        </div>
    );
}
```

If the condition is false, the heading isn't rendered.

**Interview question:** How do you conditionally render a component?

You can use JavaScript conditional expressions such as `if`, the ternary operator, or logical `&&` inside JSX, depending on the situation.

---

## 4.3 What Are React Hooks?

Hooks are functions that let function components use React features such as state and effects.

Common hooks include:

| Hook | Purpose |
|---|---|
| `useState` | Manages state |
| `useEffect` | Synchronizes with external systems |
| `useContext` | Reads context values |
| `useRef` | Holds a value that persists across renders without causing a render when changed |
| `useMemo` | Caches a calculated value between renders when dependencies are unchanged |
| `useCallback` | Caches a function definition between renders when dependencies are unchanged |

You should understand `useState` and `useEffect` especially well.

### Rules of Hooks

1. Call hooks at the top level of a function component or custom hook.
2. Don't call hooks inside loops, conditions, or nested functions.
3. Call hooks from React function components or custom hooks, not ordinary JavaScript functions.

---

# 5. Lists, Forms, and Input Handling (30–38 Minutes)

## 5.1 Rendering Lists With `map()`

Suppose you have a list of names.

```jsx
const names = ["Abirami", "Priya", "Kavya"];
```

You want to display every name on the webpage.

### React Code

```jsx
function App() {
    const names = ["Abirami", "Priya", "Kavya"];

    return (
        <ul>
            {names.map((name, index) => (
                <li key={index}>{name}</li>
            ))}
        </ul>
    );
}

export default App;
```

Output:

- Abirami
- Priya
- Kavya

### Understand `map()`

```jsx
names.map((name, index) => (
    <li key={index}>{name}</li>
))
```

- `map()` visits each array element.
- `name` represents the current name.
- `index` represents its position.
- `<li>` creates a list item.
- `key` helps React identify elements between renders.

### Why Is `key` Important?

React uses keys to match items between renders when lists change.

In real applications, prefer a stable, unique ID from your data:

```jsx
const users = [
    { id: 101, name: "Abirami" },
    { id: 102, name: "Priya" }
];

function UserList() {
    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}
```

Here, `user.id` is a better key than the array index because the list may change.

**Interview question:** Why do we use keys in React?

Keys help React identify which list items have been added, removed, or changed, so it can update the list correctly.

---

## 5.2 Forms and Controlled Components

A controlled input is an input whose displayed value is managed by React state.

This is a very common interview coding task.

### Example: Name Input

```jsx
import { useState } from "react";

function NameForm() {
    const [name, setName] = useState("");

    return (
        <div>
            <input
                type="text"
                value={name}
                onChange={(event) => setName(event.target.value)}
                placeholder="Enter your name"
            />

            <h2>Hello, {name}</h2>
        </div>
    );
}

export default NameForm;
```

### Understand the Important Lines

```jsx
const [name, setName] = useState("");
```

Initializes the input value as an empty string.

```jsx
value={name}
```

Makes the input's value come from React state.

```jsx
onChange={(event) => setName(event.target.value)}
```

Updates the state whenever the user changes the input.

```jsx
<h2>Hello, {name}</h2>
```

Displays the current value.

### What Happens?

When you type `Abirami`:

1. The input raises a change event.
2. `event.target.value` contains the current text.
3. `setName()` updates the state.
4. React renders the updated value.
5. The greeting changes to `Hello, Abirami`.

### Interview Question: What Is a Controlled Component?

A controlled component is a form element whose value is controlled by React state, typically using a `value` prop and an event handler such as `onChange`.

---

# 6. `useEffect` and API Calls (38–45 Minutes)

## 6.1 What Is `useEffect`?

`useEffect` is a React hook used to synchronize a component with external systems, such as network connections, browser APIs, or third-party widgets.

It can also be used to fetch data from an API.

### Example

```jsx
import { useEffect } from "react";

function App() {
    useEffect(() => {
        console.log("Component rendered and effect ran");
    }, []);

    return <h1>Hello React</h1>;
}

export default App;
```

### Understand the Dependency Array

```jsx
useEffect(() => {
    // Effect code
}, []);
```

The empty dependency array means React doesn't rerun this effect because of changes to ordinary component state or props. It runs after the initial mount in production; development Strict Mode may run an additional setup-and-cleanup cycle to help detect problems.

Here's the basic comparison:

| Syntax | Meaning |
|---|---|
| `useEffect(() => {})` | Runs after every committed render |
| `useEffect(() => {}, [])` | Runs on mount, with a possible extra development Strict Mode cycle |
| `useEffect(() => {}, [count])` | Runs on mount and when `count` changes |

**Important:** The dependency array should include the reactive values used by the effect that need to trigger synchronization.

### Interview Question: What Is the Difference Between `useState` and `useEffect`?

`useState` manages component state. `useEffect` synchronizes the component with external systems after rendering, such as by fetching data or setting up an event subscription.

---

## 6.2 Fetch Data From an API

Suppose an API returns a list of users.

We'll use a public testing endpoint.

```jsx
import { useEffect, useState } from "react";

function Users() {
    const [users, setUsers] = useState([]);
    const [loading, setLoading] = useState(true);
    const [error, setError] = useState("");

    useEffect(() => {
        async function fetchUsers() {
            try {
                const response = await fetch(
                    "https://jsonplaceholder.typicode.com/users"
                );

                if (!response.ok) {
                    throw new Error("Failed to fetch users");
                }

                const data = await response.json();

                setUsers(data);
            } catch (err) {
                setError(err.message);
            } finally {
                setLoading(false);
            }
        }

        fetchUsers();
    }, []);

    if (loading) {
        return <p>Loading...</p>;
    }

    if (error) {
        return <p>{error}</p>;
    }

    return (
        <ul>
            {users.map(user => (
                <li key={user.id}>{user.name}</li>
            ))}
        </ul>
    );
}

export default Users;
```

Let's simplify this into five steps.

1. `useState([])` stores the users.
2. `useEffect()` starts the request when the component mounts.
3. `fetch()` sends the HTTP request.
4. `response.json()` parses the JSON response.
5. `setUsers(data)` updates state, causing the UI to render the user list.

We also manage loading and error states so the UI responds appropriately.

### Interview Question: How Do You Fetch API Data in React?

I can use `fetch()` or a library such as Axios inside an effect when the request should run as part of synchronizing the component with external data. I manage the loading, success, and error states using React state.

---

# 7. Practical React Coding Questions (45–52 Minutes)

These are the programs you should practise writing without looking at the answers.

## Coding Question 1: Counter App

**Requirement:** Create a button that increases a number whenever it is clicked.

### Solution

```jsx
import { useState } from "react";

function Counter() {
    const [count, setCount] = useState(0);

    return (
        <div>
            <h1>{count}</h1>

            <button onClick={() => setCount(c => c + 1)}>
                Increment
            </button>
        </div>
    );
}

export default Counter;
```

### What You Must Understand

- `useState(0)` initializes the counter.
- `count` stores the current value.
- `setCount(c => c + 1)` updates it based on the previous value.
- `onClick` handles the button click.

**Interview follow-up:** How would you add a decrement button?

Add another button:

```jsx
<button onClick={() => setCount(c => c - 1)}>
    Decrement
</button>
```

How would you reset the counter?

```jsx
<button onClick={() => setCount(0)}>
    Reset
</button>
```

If you understand this program, you already know the fundamentals of state and events.

---

## Coding Question 2: Todo List

**Requirement:** Let the user enter a task and add it to a list.

### Solution

```jsx
import { useState } from "react";

function TodoApp() {
    const [task, setTask] = useState("");
    const [tasks, setTasks] = useState([]);

    function addTask() {
        if (task.trim() === "") {
            return;
        }

        setTasks(previousTasks => [
            ...previousTasks,
            task.trim()
        ]);

        setTask("");
    }

    return (
        <div>
            <h1>Todo List</h1>

            <input
                value={task}
                onChange={event => setTask(event.target.value)}
                placeholder="Enter a task"
            />

            <button onClick={addTask}>
                Add Task
            </button>

            <ul>
                {tasks.map((item, index) => (
                    <li key={index}>{item}</li>
                ))}
            </ul>
        </div>
    );
}

export default TodoApp;
```

### Three Important Concepts in This Code

**1. State for input**

```jsx
const [task, setTask] = useState("");
```

Stores the current input.

**2. State for the list**

```jsx
const [tasks, setTasks] = useState([]);
```

Stores the tasks.

**3. Spread syntax**

```jsx
setTasks(previousTasks => [...previousTasks, task.trim()]);
```

Creates a new array containing the existing tasks and the new task.

React state should generally be updated immutably rather than modifying the existing array directly.

For example, avoid:

```jsx
tasks.push(task);
```

A production-ready todo list should assign each task a stable unique ID instead of using its array index as the key. Index keys are sufficient for understanding this basic example, but are less appropriate when items can be inserted, deleted, or reordered.

---

## Coding Question 3: Search an Array

**Requirement:** Display only the names that contain the entered search text.

```jsx
import { useState } from "react";

function SearchApp() {
    const [search, setSearch] = useState("");

    const names = [
        "Abirami",
        "Priya",
        "Arun",
        "Kavya"
    ];

    const filteredNames = names.filter(name =>
        name.toLowerCase().includes(search.toLowerCase())
    );

    return (
        <div>
            <input
                value={search}
                onChange={event => setSearch(event.target.value)}
                placeholder="Search names"
            />

            <ul>
                {filteredNames.map(name => (
                    <li key={name}>{name}</li>
                ))}
            </ul>
        </div>
    );
}

export default SearchApp;
```

### Understand the Logic

1. Store the search input in state.
2. Use `filter()` to find matching names.
3. Use `includes()` to check for the search text.
4. Use `map()` to display the matching names.

If you type `a`, the list shows names containing `a`, ignoring capitalization.

This combines state, events, arrays, functions, and JSX in one program.

---

# 8. Top React Interview Questions and Answers

Revise these quickly before your interview.

### 1. What is React?

React is a JavaScript library for building user interfaces using reusable components.

### 2. What is JSX?

JSX is a JavaScript syntax extension that allows developers to describe UI using HTML-like syntax.

### 3. What is a component?

A component is a reusable piece of UI.

### 4. What are props?

Props are read-only inputs passed to a component, usually from its parent.

### 5. What is state?

State is data managed by a component that can change over time and trigger a re-render.

### 6. What is `useState`?

`useState` is a hook that lets a function component manage state.

### 7. What is `useEffect`?

`useEffect` synchronizes a component with external systems after rendering.

### 8. What is the Virtual DOM?

The Virtual DOM is a commonly used term for React's in-memory representation of UI. React uses its rendering and reconciliation process to determine the necessary updates to the host environment.

### 9. What is conditional rendering?

Displaying different UI depending on a condition.

### 10. What is the purpose of keys?

Keys help React identify elements in a list across renders.

### 11. What is a controlled component?

A form element whose value is managed by React state.

### 12. What is the difference between `map()` and `filter()`?

`map()` transforms every element into a corresponding result. `filter()` selects elements that satisfy a condition.

### 13. What is prop drilling?

Prop drilling means passing props through multiple intermediate components to reach a deeply nested component.

### 14. How do you avoid prop drilling?

Depending on the application, you can use Context, component composition, or a state-management library.

### 15. What is React Router?

React Router is a routing library used to manage navigation between views in React applications.

### 16. What is the difference between React and React DOM?

React provides the core component and rendering model. React DOM provides integration for rendering React applications into the browser DOM.

### 17. What is a fragment?

A React Fragment groups multiple elements without adding an extra DOM element.

```jsx
<>
    <h1>Hello</h1>
    <p>Welcome</p>
</>
```

### 18. Why shouldn't we directly mutate state?

Direct mutation can prevent React from recognizing the intended state change and can cause inconsistent rendering. Use the appropriate state setter and immutable updates.

### 19. What is a custom hook?

A custom hook is a JavaScript function whose name begins with `use` and that can reuse stateful React logic between components.

### 20. What is the difference between `onClick={handleClick}` and `onClick={handleClick()}`?

The first passes the function to be called when the event occurs. The second calls the function immediately during rendering.

---

# 9. Final Revision: What You Must Be Able to Write

| Interview task | Concepts required |
|---|---|
| Create a welcome page | Component, JSX |
| Display a username | Props |
| Increment a counter | `useState`, events |
| Show or hide a message | State, conditional rendering |
| Display a list | Arrays, `map()`, keys |
| Search names | State, `filter()` |
| Create a form | Controlled inputs, events |
| Fetch data from an API | `useEffect`, `fetch`, `async/await` |
| Add a todo item | State, input handling, spread syntax |
| Share data across components | Props, lifting state, Context |

## How to Answer When the Interviewer Asks You to Write Code

Suppose the interviewer says:

"Create a React component that displays a button and increases the count whenever the button is clicked."

Don't immediately start typing.

First, say:

"I'll use a functional component and the `useState` hook to maintain the counter value. I'll initialize the count to zero and update the state using an event handler when the button is clicked."

Then write the code.

This shows the interviewer that you understand the solution before implementing it.

**One important thing:** You don't need to know every React concept to write a basic program. Most beginner React coding exercises can be approached by identifying the component, the data it needs, the events that change that data, and how the resulting UI should be rendered.

---

# 🎯 Abirami, Now Let's Practise Your Interview

You've covered the basics. The best use of your remaining preparation time is to practise writing the code yourself.

I'll act as your React interviewer and ask you one question at a time. I'll check your answer, correct mistakes, and explain the reasoning.

### Interview Question 1 — React State

**Write a React component that displays a counter starting at `0` and has a button to increment the count by `1` whenever the user clicks it.**

Expected initial display:

```text
Count: 0

[Increment]
```

After one click:

```text
Count: 1

[Increment]
```

**Your turn:** Try writing the complete React component, including the import statement. Don't worry if you make a mistake; I'll help you correct it.