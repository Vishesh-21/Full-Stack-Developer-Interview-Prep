**What triggers a re-render in React?**
A component re-renders when its state changes, props change, or its parent re-renders. Context value changes also trigger re-renders.

**Does calling setState with the same value cause a re-render? Why?**
Usually no. React skips the re-render if the new state value is the same as the current one.

**Reason** : React uses Object.is to compare the previous and next state. If the values are identical, React bails out to avoid unnecessary rendering. If the value is a new reference (like a new object/array), it will re-render, even if the content looks the same.

**How does React decide what to re-render?**
React creates a new Virtual DOM tree and diffs it with the previous one. Only changed nodes are updated in the real DOM.

React uses a linear-time, heuristic Virtual DOM diffing algorithm.

**What problem does the Virtual DOM actually solve?**
It minimizes expensive real DOM operations by batching and computing changes in memory first.

**Is Virtual DOM always faster than direct DOM manipulation?**
No, the Virtual DOM is not always faster.
**Why**

- Virtual DOM adds extra overhead (creating VDOM + diffing).
- For very small or simple updates, direct DOM manipulation can be faster.
- Virtual DOM shines when there are frequent, complex UI updates, because it batches changes and minimizes real DOM operations.

**Why does React rely heavily on keys during reconciliation?**
React relies on keys during reconciliation to efficiently identify which elements have changed, been added, or removed in a list.

**Why is lifting state up needed?**
When multiple components need the same data, state is moved to their closest common parent to keep data consistent.

**What problems arise if you don’t lift state up?**

- Duplicate state
- Hard to synchronize
- Prop drilling issues
- Harder to manage

**Why should you use functional updates in useState?**
Functional updates ensure you always get the latest state, especially during batching.
setCount(prev => prev + 1)

**Why do objects/functions cause repeated effects?**
In React, objects and functions cause repeated effects because of reference inequality. Every render creates new references for objects and functions. useEffect (or dependencies like [obj]) checks references with ===. Since the reference changes every render, React thinks the dependency changed, so the effect runs again.

**When does useEffect cleanup run?**
Cleanup runs before the next effect execution and when the component unmounts.

> Controlled inputs are easier to validate because React always knows the current value.

**Why is using index as key risky?**
Index keys break component identity during reordering, leading to wrong UI updates and state bugs. Use index only for static lists where items don’t change order or identity.

> Context is best for global/static data (theme, auth), not frequently changing or local state.

> Use Profiler, console logs, and React.memo to detect and confirm unnecessary re-renders.

**What problem does React.memo solve?**
It prevents re-rendering a component when props haven’t changed.

**Why doesn’t it work well with inline props?**
React doesn’t work well with inline props (like inline objects or functions) because they create new references on every render.

**Can useCallback be replaced with useMemo?**
Yes, but with caution. useCallback can be replaced by useMemo, because a function is just a value, and useMemo returns a memoized value.

**When should you NOT use useMemo/useCallback?**
When computations are cheap—overuse increases complexity without performance gain.

**What are Error Boundaries and what can’t they catch?**
They catch errors in render and lifecycle methods, but not in event handlers or async code.
Async errors must be handled with try/catch or .catch(), not Error Boundaries.

**Why does StrictMode cause double rendering in dev? or does it happen in production**
StrictMode causes double rendering only in development, not in production.

why its happens : React intentionally invokes components twice to detect:

- Impure render logic
- Side effects in render
- Missing effect cleanups

**What are React Portals used for?**
Portals render children outside the DOM hierarchy—commonly for modals, tooltips, overlays.
Events in React portals bubble according to the React tree, not the DOM tree.

**How does React handle events internally?**
React uses a Synthetic Event system to handle events efficiently and consistently.

**How it works:**

- Event delegation: React attaches one listener per event type at the root (not on every element).
- SyntheticEvent: Native browser events are wrapped in a cross-browser wrapper.
- Batched updates: State updates inside events are batched to reduce re-renders.
- Controlled lifecycle: Events flow through React’s capture → bubble phases.

**What is a common cause of infinite re-render loops?**
A common cause of infinite re-render loops is updating state during render or in an effect that depends on that same state or useEffect without dependencies.

```jsx
useEffect(() => {
  setCount(count + 1);
}, [count]);
```

to break such we have to break loops by adding conditions, fixing dependencies, or avoiding state updates in render.

**Why does passing objects/functions as props cause re-renders?**
Passing objects or functions as props causes re-renders because React compares props by reference, not by value.

> React.memo and PureComponent use shallow comparison (===).

to avoid this :

- useMemo for objects/arrays
- useCallback for functions

**How does React compare dependency values in hooks? or why doesn't react do deep comparison?**
React uses Object.is (shallow comparison), not deep comparison. React doesn’t do deep comparison because it would be too expensive and unpredictable.

**What’s the difference between mounting and rendering?**
**_Mounting_** :

- The first time a component is created and inserted into the DOM.
- Lifecycle: constructor → render → componentDidMount (class) or useEffect(() => {}, []) (functional).

**_Rendering_** :

- The process of calculating what the UI should look like.
- Happens every time state or props change, not just the first time.

**Can a component render without mounting?**
Yes, a component can render without mounting in React. bcz Rendering is the process of computing the Virtual DOM output. Mounting happens when React actually inserts the element into the real DOM. A component can render in memory (VDOM) but never reach the real DOM . 
example : {false && <Child />} // renders in React logic but never mounts

### How do you optimize a large list in React?

**When would you choose Context over Redux or Zustand?**
- Sharing static/global data: Theme, language, authentication info.
- Few updates: State doesn’t change frequently, so re-renders aren’t costly.
- Small/medium apps: No complex state logic or middleware needed.

***Avoid Context when:***
- State updates happen frequently (can trigger unnecessary re-renders).
- You need advanced features like time-travel debugging, middleware, or derived state (Redux/Zustand are better).

**What makes a React component “expensive”?**
A React component is considered “expensive” when it consumes a lot of CPU, memory, or rendering time, slowing down the app.
***Common causes:***
- Heavy rendering logic
- large DOM updates
- Frequent re-renders
- Unstable references
- Third-party components

**Why does React require keys to be stable across renders?**
Stable keys allow React to correctly match old and new elements and preserve component state. If keys change between renders, React loses the ability to match old elements with new ones, which can break the UI.

**What happens internally when setState is called?**
React schedules an update, batches it, runs reconciliation, then commits changes to the DOM.
***setState is asynchronous in most cases.*** : bcz : React does not immediately update the state when setState is called. It schedules a re-render and may batch multiple updates for performance. The state update is reflected after the next render, not instantly.

> React.memo sometimes doesn’t prevent re-renders because it only does a shallow comparison of props.

**How does React handle conditional rendering internally?**
JSX compiles to React.createElement; conditional rendering just changes what elements are created.And also Conditional rendering is cheap; the cost comes from what you render, not the condition itself.

**What is a stale closure in React hooks?**
A stale closure happens when a function captures an old state or prop value because it was created during a previous render. Common case: inside useEffect, setTimeout, or event handlers — if dependencies aren’t updated, the function keeps using outdated values.

**Why do refs not cause re-renders?**
Updating ref.current does not trigger reconciliation because refs are mutable containers. Use refs for mutable, non-UI values or DOM access; use state for values that affect rendering.

> Do not use refs for values that need to trigger UI updates, because refs don’t cause re-renders.

**What happens if you call a hook conditionally?**
Hook order breaks, causing React to associate state with the wrong hook. React tracks hooks by call order in each component; changing order or calling hooks conditionally breaks this mapping.

**Why must hooks be called at the top level?**
React relies on call order, not names, to link hook state.

**What’s the difference between layout effect and effect?**
useLayoutEffect runs before paint (synchronous), useEffect runs after paint (asynchronous). Use layout effects for DOM reads/writes that must happen before the user sees the UI.

- Layout effects are blocking, so doing expensive work in them can make the UI laggy or janky.

**What is a memory leak in React apps?**
Uncleaned subscriptions, timers, or observers causing updates after unmount.

**Virtual Dom** : Many think the VDOM is just "faster." Technically, JS objects are fast, but the VDOM's real power is Minimization. It calculates the smallest set of changes needed to sync the UI with the real DOM.

**How does the 'Diffing' algorithm handle different element types at the same position?**
***Same position, different element type***
- React unmounts the entire old subtree
- React destroys all state, refs, and event handlers
- React creates a new DOM node and subtree from scratch
If element types differ at the same position, React unmounts the old tree and mounts a new one instead of diffing.

**What is the difference between the "Render Phase" and the "Commit Phase"?**
these two are the phases of reconcilliation.
- ***Render Phase*** : The Render Phase is when React determines what needs to change (diffing). This phase is asynchronous and can be paused/interrupted.
- ***Commit Phase*** : The Commit Phase is when React applies those changes to the real DOM and runs lifecycles; this phase is synchronous and cannot be interrupted."

**Why is a "stale closure" a common issue with useEffect?**
A stale closure occurs when a function inside an effect captures a state variable from a previous render. If that variable isn't in the dependency array, the effect continues to use the old value even after the state has updated. solutions : ***useRef*** gives access to fresh values inside closures without causing re-renders or effect re-execution.

**Controlled vs. Uncontrolled components: Which is better?**
Controlled components have their state managed by React (value and onChange). Uncontrolled components let the DOM handle the data, accessed via refs. Controlled is usually preferred for instant validation, but Uncontrolled is often faster to implement for simple forms

> Uncontrolled components are better when frequent input updates would cause unnecessary re-renders and hurt performance.

**When should you use React.memo()?**
It’s a Higher Order Component that prevents a component from re-rendering unless its props change.

**What is "Component Composition" vs. "Inheritance"?**
React follows a "Has-A" relationship, not an "Is-A" relationship. React recommends Composition over Inheritance. Instead of extending classes, we build components by passing other components as props (like the children prop) or specialized props. This makes the code much more flexible and reusable.

**Why can't you call Hooks inside loops or conditions?**
React stores Hook data in an internal array. If you change the order of calls by putting a Hook inside a condition or loop, React will lose track of which state belongs to which Hook, leading to unpredictable bugs.

**Do two components using the same custom hook share the same state?**
No, each call gets its own isolated state

**React Fiber** : React Fiber is React’s internal rendering engine that breaks rendering work into small units, allowing React to pause, prioritize, and resume updates for better performance. Fiber is a re-implementation of React’s reconciliation algorithm. It enables incremental rendering, update prioritization, and interruptible work, which is why features like concurrent rendering are possible.

***What problems Fiber solves***
Old React used a stack-based reconciler → rendering was blocking
Fiber introduces a linked list of work units (fibers) → rendering can be:
- paused
- resumed
- prioritized