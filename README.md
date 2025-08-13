# 📘 React Web Essentials

> A concise guide covering the **core concepts of React** for modern web development.

---

##  Table of Contents

1.  [What is React?](#what-is-react)
2.  [Key Features](#key-features)
3.  [Web Fundamentals](#web-fundamentals)
    -   [HTML](#html)
    -   [JavaScript](#javascript)
    -   [CSS](#css)
    -   [DOM](#dom)
    -   [TypeScript](#typescript)
    -   [Local Storage](#local-storage)
    -   [Exports](#exports)
4.  [Core Concepts](#core-concepts)
    -   [1. Components](#1-components)
    -   [2. JSX](#2-jsx)
    -   [3. Props](#3-props)
    -   [4. State](#4-state)
    -   [5. Lifecycle Methods / Hooks](#5-lifecycle-methods--hooks)
    -   [6. Event Handling](#6-event-handling)
    -   [7. Conditional Rendering](#7-conditional-rendering)
    -   [8. Lists and Keys](#8-lists-and-keys)
    -   [9. Forms](#9-forms)
    -   [10. Lifting State Up](#10-lifting-state-up)
    -   [11. Context API](#11-context-api)
        -   [When to use Context](#context-when-to-use)
        -   [Problem (Prop Drilling)](#context-prop-drilling)
        -   [Solution (Context API)](#context-solution)
        -   [Benefits](#context-benefits)
    -   [12. React Router](#12-react-router-optional)
        -   [Install](#react-router-install)
        -   [Key pieces](#react-router-key-pieces)
        -   [Example](#react-router-example)
5.  [What is Vite?](#what-is-vite)
    -   [Hot reloading](#hot-reloading)
    -   [Step-by-step setup (React + Vite)](#step-by-step-setup-react-vite)
    -   [Getting started (React)](#vite-getting-started)
6.  [What is Node.js](#nodejs)
7.  [What is Next.js](#nextjs)
8.  [What is Express.js](#expressjs)
9.  [Folder Structure Tips](#folder-structure-tips)
    -   [Hooks folder](#hooks-folder)
10.  [Resources](#resources)

---

<a id="what-is-react"></a>
## 1. What is React?

React is a **JavaScript library** for building **user interfaces**, especially single-page applications. Developed by Facebook, it allows developers to create **reusable UI components** and manage dynamic data efficiently.

---

<a id="key-features"></a>
## 2. Key Features

-   **Declarative UI**: React makes it easy to design interactive UIs.
-   **Component-Based Architecture**: Build encapsulated components that manage their state.
-   **Virtual DOM**: Efficient re-rendering of the user interface.
-   **Unidirectional Data Flow**: Data flows in one direction, simplifying debugging and testing.
-   **Hooks**: Manage state and side effects in function components.

---

<a id="web-fundamentals"></a>
## 3. Web Fundamentals

<a id="html"></a>
#### HTML
- HTML is the content and structure of a webpage (like its skeleton).

<a id="javascript"></a>
#### JavaScript
- JavaScript adds behavior and interactivity to the webpage.

<a id="css"></a>
#### CSS
- CSS is used to style a webpage.

<a id="dom"></a>
#### DOM (Document Object Model)
- The DOM is a map-like structure of a webpage that represents its content and layout.
- It allows you to update parts of the page (like text or images) instantly, without reloading the whole page.

<a id="typescript"></a>
### TypeScript
- TypeScript is JavaScript with extra features like type checking to catch errors early.

<a id="local-storage"></a>
#### Local Storage
- A browser API for storing key–value data persistently, even after refresh or closing the tab.
- Useful for caching small amounts of user data (e.g., theme, tokens, preferences).

<a id="exports"></a>
#### Exports
- Named export: export multiple things by name, import with curly braces.
  - Example: `export function add() {}` then `import { add } from './math'`
- Default export: one primary export per file, import with any name.
  - Example: `export default function App(){}` then `import App from './App'`

---

<a id="core-concepts"></a>
## 📚 Core Concepts

<a id="1-components"></a>
### 1. Components

React applications are built using components. Components are the building blocks of a React app. They can be either **functional components** or **class-based components**, but functional components with hooks are preferred.

Example of a functional component:
```jsx
function Welcome() {
  return <h1>Hello, World!</h1>;
}
```

- Fragment shorthand `<>...</>`: Group multiple elements without adding an extra DOM node.
- `<nav>`: Semantic element for navigation sections like menus or links.

<a id="2-jsx"></a>
### 2. JSX  (a combination of JavaScript and Html) 

JSX (JavaScript XML) is a syntax that lets you write HTML code inside JavaScript. This makes building webpage parts faster and easier.

Example JSX code:

```jsx
const element = <h1>Welcome to React</h1>;
```

<a id="3-props"></a>
### 3. Props

Props (short for "properties") are used to pass data from a parent component to a child component. They are immutable (read-only).

Example of passing props:

```jsx
function Greeting({ name }) {
  return <p>Hello, {name}</p>;
}
```

Notes:
- Destructure props in the parameter list: `function Card({ title, children }) { ... }`
- In JSX, `{ ... }` evaluates JavaScript. To pass an object literal, wrap it in double braces: `config={{ theme: 'dark' }}`

<a id="4-state"></a>
### 4. State

State represents dynamic data in a component that can change over time. State is local to the component and can be updated using hooks like `useState()`.

Example of using state:

```jsx
const [count, setCount] = useState(0);
```

- `useState` is a React hook that adds stateful variables to function components.

<a id="5-lifecycle-methods--hooks"></a>
### 5. Lifecycle Methods / Hooks

React components have lifecycle methods that allow you to run code at specific points in a component's life (e.g., when it's mounted or updated). With Hooks like `useEffect()`, you can manage side effects like API calls, subscriptions, or timers.

Example using `useEffect` to run a function when the component mounts:

```jsx
useEffect(() => {
  console.log("Component mounted");
}, []); // Empty array means run once when the component is first mounted.
```

- `useEffect` runs code after render for side effects like fetching data or updating non-React systems.

<a id="6-event-handling"></a>
### 6. Event Handling

React uses camelCase for handling events (e.g., `onClick`, `onChange`), and you pass a function to the event handler.

Example of a click event handler:

```jsx
<button onClick={handleClick}>Click me</button>
```

preventDefault vs stopPropagation
- `e.preventDefault()` stops the browser's default action (e.g., prevents a form submit from reloading the page).
- `e.stopPropagation()` stops the event from bubbling to parent elements.
- Difference: `preventDefault` blocks the default action; `stopPropagation` blocks the event from reaching ancestors. Use them together when needed.

<a id="7-conditional-rendering"></a>
### 7. Conditional Rendering

In React, you can render components conditionally using JavaScript expressions.

Example of conditional rendering:

```jsx
{isLoggedIn ? <Dashboard /> : <Login />}
```

<a id="8-lists-and-keys"></a>
### 8. Lists and Keys

When rendering a list of items, React requires a unique key for each item to optimize rendering.

Example of rendering a list of items with keys:

```jsx
{items.map((item) => (
  <li key={item.id}>{item.name}</li>
))}
```

<a id="9-forms"></a>
### 9. Forms

In React, form elements like `<input>`, `<textarea>`, and `<select>` are controlled components, meaning their values are managed by React state.

Example of a controlled form input:

```jsx
<input 
  type="text" 
  value={name} 
  onChange={(e) => setName(e.target.value)} 
/>
```

<a id="10-lifting-state-up"></a>
### 10. Lifting State Up

If multiple components need to share state, you "lift" the state to their closest common ancestor and pass the data as props.

Example of lifting state up:

```jsx
function Parent() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <Display count={count} />
      <Incrementer onIncrement={() => setCount((c) => c + 1)} />
    </div>
  );
}

function Display({ count }) {
  return <p>Count: {count}</p>;
}

function Incrementer({ onIncrement }) {
  return <button onClick={onIncrement}>+1</button>;
}
```
**Explanation:** Think of it like a family piggy bank. Instead of each child having their own piggy bank (which gets confusing), the parent holds the real piggy bank. The `Parent` component stores the actual `count` value. `Display` gets told the current amount, and `Incrementer` can ask the parent to add money. This keeps a single source of truth so children stay in sync without duplicate or outdated state.


<a id="11-context-api"></a>
### 11. Context API

The Context API solves the "prop drilling" problem. Imagine passing a message through a chain of 10 people—by the time it reaches the end, it might get lost or changed. Context is like a radio broadcast that components can tune into directly.

**When to use Context:**
<a id="context-when-to-use"></a>
- Theme settings (dark/light mode)
- User authentication data
- Language preferences
- Any data needed by many components at different levels

Context in React (holds and shares data across components)
* allows you to share data between components without passing props manually through each level of the component tree.

Prop drilling
* is passing data from parent components to child components through props, even if intermediate components(the middle child) don't need the data.

Key APIs:
- `createContext` creates a context object and provides a `Provider` to set the value for descendants.
- `useContext(SomeContext)` reads the nearest current value of a context inside a function component without prop drilling.

<a id="context-prop-drilling"></a>
**The Problem (Prop Drilling):**
```jsx
function App() {
  const user = { name: "John", role: "admin" };
  return <Header user={user} />;
}

function Header({ user }) {
  return <Navigation user={user} />; // Just passing it through
}

function Navigation({ user }) {
  return <UserMenu user={user} />; // Still just passing it through
}

function UserMenu({ user }) {
  return <p>Welcome, {user.name}!</p>; // Finally used here!
}
```

<a id="context-solution"></a>
**The Solution (Context API):**
```jsx
// 1. Create the context
const UserContext = React.createContext();

// 2. Provide the data at the top level
function App() {
  const user = { name: "John", role: "admin" };
  
  return (
    <UserContext.Provider value={user}>
      <Header />
    </UserContext.Provider>
  );
}

// 3. Components in between don't need to know about user data
function Header() {
  return <Navigation />;
}

function Navigation() {
  return <UserMenu />;
}

// 4. Use the context where you need it
function UserMenu() {
  const user = useContext(UserContext);
  return <p>Welcome, {user.name}!</p>;
}
```

<a id="context-benefits"></a>
**Benefits:**
- No more passing props through components that don't need them
- Cleaner, more maintainable code
- Direct access to shared data from anywhere in the component tree

<a id="12-react-router-optional"></a>
### 12. React Router

<a id="react-router-install"></a>
Routing
- Install: `npm install react-router-dom`

React Router enables dynamic routing in a React application. You can handle navigation between different pages of your app without reloading the entire page.

<a id="react-router-key-pieces"></a>
Key pieces:
- `<BrowserRouter>`: Wraps your whole app to enable routing. Main router for web apps.
- `Routes`: Groups all your routes.
- `Route`: Defines a single route path.

<a id="react-router-example"></a>
Example of setting up React Router:

```jsx
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';

<Router>
  <Routes>
    <Route path="/about" element={<About />} />
    <Route path="/contact" element={<Contact />} />
  </Routes>
  </Router>
```

---

<a id="folder-structure-tips"></a>
## 📁 Folder Structure Tips

A common folder structure for a React project:

```
src/
├── components/  // Reusable UI components
├── services/    // API clients, business logic helpers
├── pages/       // Page-level components
├── hooks/       // Custom React hooks
├── contexts/    // Context API files
├── css/         // Global styles or CSS modules
├── App.js       // Main app component
├── main.js      // React entry point
```

---

<a id="hooks-folder"></a>
### Hooks folder
The `hooks/` folder contains custom React hooks — reusable functions that share stateful logic between components. Custom hooks start with "use" (e.g., `useLocalStorage`, `useFetch`, `useToggle`) and can call built-in hooks like `useState` or `useEffect`.

Example custom hook:
```jsx
// hooks/useCounter.js
import { useState } from 'react';

export function useCounter(initialValue = 0) {
  const [count, setCount] = useState(initialValue);

  const increment = () => setCount((c) => c + 1);
  const decrement = () => setCount((c) => c - 1);
  const reset = () => setCount(initialValue);

  return { count, increment, decrement, reset };
}
```

---

<a id="what-is-vite"></a>
## 4. What is Vite?

- Vite is a modern front-end fast build tool and development server that provides a faster and leaner development experience for web projects.
- Vite helps you start and run web projects quickly
- It uses native ES modules in the browser during development and bundles your app for production with lightning-fast tools under the hood (esbuild and Rollup).

Why developers like Vite:
- Instant server start with near-zero cold starts
- Hot Module Replacement (HMR) that is fast and reliable
- Minimal config to get started
- Optimized production builds

<a id="hot-reloading"></a>
Hot reloading
- is a developer tool that refreshes the page automatically when code changes.

<a id="vite-getting-started"></a>
Getting started (React):
```bash
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev
```

<a id="step-by-step-setup-react-vite"></a>
### Step-by-step setup (React + Vite)

1. Run: `npm create vite@latest`
2. Enter project name
3. Select framework: React
4. Select variant: JavaScript
5. `cd your-project-name` (note: `package.json` lists all dependencies)
6. Install deps: `npm install`
7. Start dev server: `npm run dev`
8. Ctrl+click the shown URL to open in the browser (Cmd+click on macOS)
9. Open `src/main.jsx` (entry point that mounts React)
10. Edit `src/App.jsx` (root component)
11. Create `src/components/` for reusable UI components
12. Create `src/pages/` for page-level components
13. Press `Ctrl+C` in the terminal to stop the dev server

---

<a id="nodejs"></a>
## 5. What is Node.js

Node.js is a runtime environment that allows you to run JavaScript on the server side, outside the browser. It's commonly used for backend development and building scalable network applications.

---

<a id="nextjs"></a>
## 6. What is Next.js

Next.js is a React-based web framework for building fast, SEO-friendly websites and applications. It offers features like automatic routing, server-side rendering (SSR), static site generation (SSG), and built-in SEO support.

---

<a id="expressjs"></a>
## 7. What is Express.js

Express.js is a minimal and flexible web framework for Node.js that simplifies building web servers and APIs. It provides a robust set of features for handling routing, middleware, and HTTP requests.

---

<a id="resources"></a>
## 🔗 Resources

- React Docs: https://react.dev
- React Hooks Overview: https://react.dev/reference/react
- React Router Docs: https://reactrouter.com
- Vite Docs: https://vitejs.dev/guide/
- Next.js Docs: https://nextjs.org/docs
- Node.js Docs: https://nodejs.org/en/docs
- Express.js Guide: https://expressjs.com/en/guide/routing.html
- MDN Web Docs (HTML/CSS/JS): https://developer.mozilla.org
- W3Schools (HTML/CSS/JS): https://www.w3schools.com
- W3Schools React Tutorial: https://www.w3schools.com/react/
- FreeCodeCamp React Course: https://www.freecodecamp.org/learn/front-end-development-libraries/react/
- Epic React by Kent C. Dodds: https://epicreact.dev
- UI Patterns (React + CSS): https://uipatterns.io
