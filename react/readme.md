##### What is React and why is it used for frontend development?

React is a JavaScript library developed by Facebook (now Meta) for building user interfaces (UIs) — especially single-page applications (SPAs) where parts of the page update dynamically without reloading. React provide fast rendering, React updates only the parts of the UI that change, instead of reloading the whole page.

---

`🧱 The Problem with Plain HTML, CSS, JS:`
When apps become complex:

- You have to manually update the DOM (like showing/hiding elements or changing text).
- Managing UI state (like forms, modals, and toggles) becomes messy.
- The same code (like buttons or cards) gets repeated on many pages.
- When data changes, it’s hard to keep the UI in sync.
- Adding new features can break existing ones due to spaghetti code.

---

| Aspect           | HTML/CSS/JS                                            | React                                                                                                 |
| ---------------- | ------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| **What happens** | Browser just loads static files — HTML, CSS, JS.       | React loads JavaScript bundle → parses → builds UI using Virtual DOM.                                 |
| **Result**       | ✅ Usually **faster initial load** (less JS to parse). | ⚠️ Slightly **slower initial load** because React needs to load and run its library + component tree. |
| **Why**          | Directly rendered by browser.                          | Needs JS runtime + Virtual DOM creation.                                                              |

---

##### Can a React component return multiple elements?

Yes, a React component can return multiple elements, but there’s one important rule: A React component must return a single parent element.

`why : React’s rendering engine needs one root node to efficiently track updates in the Virtual DOM. So if you try to return two sibling elements directly, you’ll get an error.`

##### What is the Virtual DOM and how does React use it?

The Virtual DOM (VDOM) is a lightweight copy of the real DOM (Document Object Model). It’s a JavaScript object that represents the UI structure of your app.

##### How React Uses the Virtual DOM

When something changes (like a state update), React creates a new Virtual DOM tree.

- It compares the new Virtual DOM with the old one using a process called diffing.
- React then finds only the parts that changed.
- It updates only those parts in the real DOM — not the entire page.
  This process is called reconciliation. Reconciliation is the algorithm React uses to efficiently update the Real DOM by comparing the new and previous Virtual DOM trees.

---

| Feature        | **Props**                            | **State**                                                 |
| -------------- | ------------------------------------ | --------------------------------------------------------- |
| **Definition** | Data passed **from parent to child** | Data **managed inside a component**                       |
| **Mutability** | **Immutable** (cannot change)        | **Mutable** (can be changed with `setState` / `useState`) |
| **Ownership**  | Controlled by **parent component**   | Controlled by **the component itself**                    |
| **Usage**      | For **configuring** components       | For **handling dynamic behavior or data**                 |

---

`React Hooks are special functions that let you use React features (like state, lifecycle, and context) inside functional components — without needing class components.`

##### Difference between useMemo and useCallback hook

useMemo : useMemo is a Hook that remembers (caches) the result of a calculation so React doesn’t have to recalculate it every time the component re-renders. It saves the result of an expensive function (like a big calculation) and only recalculates it when its inputs change.

useCallback is a Hook that remembers a function so React doesn’t recreate it every time the component renders.

| Hook            | Remembers                             | Used For                          |
| --------------- | ------------------------------------- | --------------------------------- |
| **useMemo**     | The **value/result** of a calculation | Optimizing heavy computations     |
| **useCallback** | The **function itself**               | Preventing unnecessary re-renders |

---

##### What Does “Lifting State Up” Mean?

When two or more components need to share the same data, you move (lift) that shared state to their nearest common parent component.

##### Why Do We Lift State Up?

Because in React, data flows only one way — from parent to child (unidirectional data flow). So if two child components need to sync with each other, they can’t directly communicate, they must share data through their parent.

##### Can a child send props to a parent?

Directly — No,
but indirectly — Yes (through callback functions).

##### How to Send Data from Child → Parent

We do it indirectly, by passing a callback function from the parent down to the child.
Then the child calls that function with the data it wants to send up.

##### What is the Context API in React?

The Context API is a built-in React feature that allows you to share data across the entire component tree without passing props manually at every level. It provides a way to create global data, that can be accessed by any component — no matter how deep it is.

---

| Cause                   | Triggers Re-render? | Example                  |
| ----------------------- | ------------------- | ------------------------ |
| `useState` / `setState` | ✅ Yes              | State change             |
| Props change            | ✅ Yes              | New props from parent    |
| Parent re-render        | ✅ Yes              | Implicit child re-render |
| Context value change    | ✅ Yes              | New context value        |
| Normal variable change  | ❌ No               | `let x = 10`             |
| Ref value change        | ❌ No               | `ref.current` update     |
| Same state value set    | ❌ No               | `setState(prev =prev)`   |

---

##### Preventing Unnecessary Re-renders — Quick Points

- Use React.memo() → skips re-render if props don’t change.
- Use useCallback() → memoize functions so they keep the same reference.
- Use useMemo() → memoize expensive calculations or object/array props.
- Keep state local → avoid putting all state in parent components.
- Split big components → smaller components re-render less.
- Avoid creating objects/arrays inline → use useMemo for stable references.
- Use stable keys → never use array indexes as list keys.
- Optimize Context → memoize provider values or split contexts.
- Check useEffect dependencies → avoid state updates inside effects unnecessarily.
- Use list virtualization (e.g., react-window) for large lists.

##### What is PureComponent in React?

React.PureComponent is a base class for class components that automatically implements a shallow comparison of props and state to decide whether to re-render. PureComponent re-renders only if props or state have changed.

##### what are synthetic events?

Synthetic Events in React are React’s own wrapper around the browser’s native events. They provide a consistent and cross-browser compatible way of handling events — so you don’t have to worry about differences between browsers (like Chrome, Firefox, etc.).

##### what is useTransition() and useDeFerredValue() hook of react ?

useTransition() lets you mark some updates as “non-urgent” — so React can keep the UI responsive while doing heavy work in the background. useTransition() helps prevent lag by letting urgent updates (like typing) happen immediately and delaying slower ones (like filtering).

useDeferredValue() lets you delay a value’s update until React has time — useful when you’re passing a changing value to an expensive component.

##### HOC !

A Higher-Order Component (HOC) is a function that takes a component and returns a new component with extra functionality.
It’s a pattern for reusing logic between components.

##### What is the Render Props Pattern?

The Render Props pattern is when a component uses a function prop to decide what to render.

##### What is the Compound Component Pattern?

The Compound Component Pattern allows multiple components to work together under a shared parent — communicating implicitly via React context or props.

##### what is useActionState() and useOptimistic()?

useActionState() : A hook that helps handle form submissions or async actions with loading and error states — built for Server Actions. useActionState() manages pending, success, and error states automatically when using Server Actions.

Lets you show instant UI updates (optimistic UI) before the server confirms the change.

##### What is react fragment, useSate, useEffect, error boundary?

Fragments allow grouping multiple elements without adding extra nodes to the DOM.

useEffect handles side effects like data fetching, subscriptions, and DOM updates in functional components.

useState allows functional components to store and update local state.

Error boundaries catch JavaScript errors in child components and prevent the whole app from crashing. They do not catch errors in event handlers or async code.

##### Why should we not mutate state directly?

Direct mutation prevents React from detecting changes, leading to unexpected behavior.

##### What is the cleanup function in useEffect?

A cleanup function runs before the effect re-runs or component unmounts. It is used to remove subscriptions and avoid memory leaks.

##### What happens if you update state inside render?

It causes an infinite re-render loop. State updates must be done in effects or handlers.

##### Why are Hooks called at the top level?

Hooks must run in the same order on every render. This allows React to track hook state correctly.

##### How does batching work in React?

Batching groups multiple state updates into a single render. It is used to improve performance and reduce unnecessary re-renders.

##### What is Concurrent Rendering?

Concurrent rendering allows React to pause, resume, or abandon renders. It improves UI responsiveness for complex applications.

##### Why is key not recommended as array index?

Index keys break identity when items reorder. This can cause incorrect UI updates and state bugs.

##### What is Compound Component Pattern?

A pattern where components share state implicitly. It improves API flexibility and readability.

##### What is Ref Forwarding?

Ref forwarding passes a ref through a component. It allows parent components to access child DOM nodes.

##### What happens during the React build process?

The React build process converts developer-friendly source code into optimized static assets that browsers can run efficiently.

- Transpilation
- Bundling
- Minification
- Asset Optimization
- Source Maps
- Environment Configuration
- code splitting

##### Difference between Development and Production build in React

| Aspect         | Development Build | Production Build |
| -------------- | ----------------- | ---------------- |
| Purpose        | Debugging         | Performance      |
| Bundle size    | Large             | Small            |
| Error messages | Detailed          | Minimized        |
| Hot Reload     | Enabled           | Disabled         |
| Source maps    | Full              | Limited          |
| Performance    | Slower            | Optimized        |
| React warnings | Enabled           | Removed          |

##### Vite vs Turbopack

| Feature             | Vite               | Turbopack      |
| ------------------- | ------------------ | -------------- |
| Language            | JS + Rollup        | Rust           |
| Framework focus     | Framework-agnostic | Next.js        |
| Dev speed           | Very fast          | Extremely fast |
| Production maturity | Stable             | Still evolving |

Vite and Turbopack significantly reduce development build times by avoiding full rebundles and leveraging modern module systems.

##### Understand why functional components dominate

- Simpler and more readable than class components
- No this binding issues
- Hooks enable state and lifecycle logic cleanly
- Less boilerplate compared to classes
- Better logic reuse via custom hooks
- Better logic reuse via custom hooks
- Easier testing and composition

##### What enables interruptible rendering?

Answer: Fiber architecture breaks rendering into incremental units that can be scheduled and prioritized.

##### Why do large lists hurt performance?

Answer: Too many DOM nodes increase memory usage and slow reconciliation.

##### Why does fetch not reject on 404/500?

Answer: Because fetch only rejects on network failure; HTTP errors are still valid responses and must be handled manually.

<!--
1. Advanced API architecture patterns

2. Real-time updates with WebSockets

3. Offline-first strategies

4. Scalable state management architecture

5. Micro-frontend architecture

6. Monorepo structure

7. Enterprise-level React patterns

8. CI/CD integration for React apps

9. Concurrent rendering

10. Suspense for data fetching

11. Error boundaries

12. Portals

13. HOCs vs hooks
-->
