---
title: React component model
description: The mental model behind React — components as pure functions of props, state as the only source of change, and rendering as a derived view.
tags:
  - programming
  - concept
  - web-development
  - react
  - architecture
author: Linus Sehn
authored_on: 2026-06-08
sources:
  - "[[full-stack-open]]"
certainty: B
certainty_notes: "Tier B — synthesised from FSO part 1–2 notes and general React training-data recall. Hooks are the post-2019 model; the older class-component lifecycle is intentionally omitted as legacy."
---

A React UI is a tree of components. Each component is a function that takes data in (props) and returns a description of what to render. The framework reconciles the description tree against the DOM and updates only what changed. State changes trigger re-renders; props changes flow downward; events flow upward via callbacks.

## Three primitives

**Component.** A function whose return value describes a piece of UI in JSX. Pure with respect to its inputs: given the same props and state, it should return the same output.

```jsx
const Button = ({ text, onClick }) =>
  <button onClick={onClick}>{text}</button>
```

**Props.** Inputs passed from parent to child. Read-only inside the child. The parent is the source of truth; the child renders whatever was given.

**State** (via `useState`). Internal mutable data owned by a component. Updating state via the setter triggers a re-render. State is local by default — sharing means lifting it to a common ancestor.

```jsx
const Counter = () => {
  const [count, setCount] = useState(0)
  return <button onClick={() => setCount(count + 1)}>{count}</button>
}
```

## Data flow

React's unidirectional data flow has two directions in practice:

- **Props down.** A parent passes data and callbacks to children. Children render.
- **Events up.** A child calls a parent-supplied callback to signal a change. The parent updates its own state. Re-render flows downward again.

This is what makes React reasonable: at any point, you can ask "what is the state, and what props derive from it?" and read the UI top-down. No part of the UI is mutable except through state updates, and state updates trigger explicit re-renders.

## Hooks discipline

`useState`, `useEffect`, `useMemo`, and the rest must be called *unconditionally* at the top level of a component function body. Never inside a loop, conditional, or nested function. The reason is mechanical: React tracks hooks by *call order*, not by name, so if a hook is sometimes skipped the indices shift and React mis-associates the next render's hooks with the previous render's slots. The rule "always call hooks in the same order" is the contract that makes the entire hook system safe.

```jsx
// Wrong — hook inside a conditional, breaks call-order tracking
if (props.showAge) { const [age, setAge] = useState(0) }

// Right — hook at top level, conditional inside the render output
const [age, setAge] = useState(0)
return props.showAge ? <span>{age}</span> : null
```

## Event handlers — pass functions, don't call them

`onClick={handleClick}` registers `handleClick` to fire on click. `onClick={handleClick()}` *calls* `handleClick` during render and registers its return value (often `undefined`). The same trap appears with state setters: `onClick={setCount(0)}` resets the counter on every render and triggers an infinite loop. Always wrap an immediate-side-effect call in an arrow function:

```jsx
<button onClick={() => setCount(0)}>reset</button>
```

The exception is when the handler legitimately *returns* a function — a closure-builder pattern useful for parameterising handlers:

```jsx
const makeGreeter = (name) => () => console.log("hello", name)
<button onClick={makeGreeter("world")}>greet</button>
```

`makeGreeter("world")` evaluates during render and returns the handler — that handler is what runs on click.

## What React is and is not

It is a rendering library. It does not prescribe routing, data fetching, state management beyond `useState`/`useReducer`, styling, or build tooling. Each of those is a separate package decision: React Router (or Next's router), TanStack Query (or RTK Query, or SWR), Redux (or Zustand, or just context), CSS-in-JS (or Tailwind, or CSS Modules), Vite (or Next, or Webpack).

This is a design choice with consequences: extreme flexibility, but no "default React app" exists. Every project picks five or six other packages, and migration between them is non-trivial.

## Adjacent

- [[spa-architecture]] — React is the most common SPA implementation
- [[rest-architecture]] — what React components most often fetch from
- [[higher-order-procedures]] — the closure-builder event-handler pattern is exactly the SICP "procedure as returned value" idea
