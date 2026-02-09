**What is React.memo?**
React.memo is a higher-order component that memoizes a functional component, preventing unnecessary re-renders if props haven’t changed.

**_key points :_** Only works for functional components, Performs shallow comparison of props by default, Helps optimize performance in large apps

```js
import React, { useState, memo } from "react";

// Memoized child component
const Child = memo(({ count }) => {
  console.log("Child rendered");
  return <div>Child count: {count}</div>;
});

export default function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("");

  return (
    <div>
      <h1>Parent Component</h1>

      <button onClick={() => setCount(count + 1)}>Increment Count</button>
      <input
        type="text"
        placeholder="Type something"
        value={text}
        onChange={(e) => setText(e.target.value)}
      />

      {/* Child will only re-render when `count` changes */}
      <Child count={count} />
    </div>
  );
}
```

**_follow up questions_**
Does React.memo prevent all re-renders? : No. It only prevents re-renders when props are unchanged. State changes inside the component or context changes still trigger a render.

Can React.memo help with context re-renders? : Not directly — context changes still re-render all consumers. You can optimize by splitting context or using useMemo/useCallback.

---

**What is useCallback?**
useCallback is a React hook that memoizes a function so that it maintains the same reference between renders unless its dependencies change.

```js
import React, { useState, useCallback } from "react";

const Child = React.memo(({ handleClick }) => {
  console.log("Child rendered");
  return <button onClick={handleClick}>Click Me</button>;
});

export default function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("");

  // useCallback ensures the same function reference unless `count` changes
  const handleClick = useCallback(() => {
    console.log("Clicked!");
    setCount((prev) => prev + 1);
  }, [count]);

  return (
    <div>
      <h1>Count: {count}</h1>
      <input
        type="text"
        placeholder="Type something"
        value={text}
        onChange={(e) => setText(e.target.value)}
      />

      {/* Child will only re-render if handleClick reference changes */}
      <Child handleClick={handleClick} />
    </div>
  );
}

//Without useCallback, the Child would re-render on every parent render.
```

Can useCallback improve performance in all cases?
Not always. Memoization has a cost. Use it only when passing functions to memoized children or heavy re-renders occur.

What happens if you don’t provide a dependency array?
The function is recreated on every render, same as normal functions.

How is useCallback related to React.memo?
useCallback ensures a stable function reference, which prevents unnecessary re-renders in memoized children.

---

**What is useMemo?**
useMemo is a React hook that memoizes the result of a computation, recomputing it only when its dependencies change. It helps optimize expensive calculations by avoiding unnecessary recalculations on every render. Returns a memoized value

```js
import React, { useState, useMemo } from "react";

export default function App() {
  const [count, setCount] = useState(0);
  const [text, setText] = useState("");

  // Expensive computation
  const factorial = (n) => {
    console.log("Calculating factorial...");
    return n <= 0 ? 1 : n * factorial(n - 1);
  };

  // useMemo memoizes the result unless `count` changes
  const fact = useMemo(() => factorial(count), [count]);

  return (
    <div>
      <h1>
        Factorial of {count}: {fact}
      </h1>
      <button onClick={() => setCount(count + 1)}>Increment Count</button>
      <input
        type="text"
        placeholder="Type something"
        value={text}
        onChange={(e) => setText(e.target.value)}
      />
    </div>
  );
}
```

Does useMemo guarantee optimization?
No. It only avoids recomputation if dependencies haven’t changed. Memoization has some cost, so use it for heavy calculations, not for trivial ones.

What happens if you provide an empty dependency array []?
The computation runs once on mount and never recomputes.

Can useMemo prevent child re-renders?
Not directly. But if the child receives a memoized value as a prop, it can help React.memo avoid unnecessary re-renders.

---

**What is useActionState()?**
useActionState is a React hook in Next.js that lets you track the state of a Server Action call (loading, error, success) directly in your client component.

**_key points:_** Works only with Server Actions, reduce boilerplate code.

```js
const [state, formAction, isPending] = useActionState(submitData, {
  success: false,
  message: "",
});
```

---

**What is useOptimistic()?**
Implements optimistic UI updates — update the UI immediately before the server action completes.

**_key points_** : Updates local state first, then reconciles when the server responds

```js
"use client";
import { useOptimistic } from "next/experimental";
import { addTodo } from "./actions/todoActions";

export default function TodoApp() {
  const [todos, addOptimistic] = useOptimistic([], (prev, newTodo) => [...prev, newTodo]);

  const handleAdd = (title: string) => {
    addOptimistic({ title });
    addTodo({ title }); // server action
  };

  return (
    <div>
      <button onClick={() => handleAdd("New Task")}>Add Task</button>
      <ul>
        {todos.map((todo, idx) => (
          <li key={idx}>{todo.title}</li>
        ))}
      </ul>
    </div>
  );
}
```

Behavior: UI shows new todo immediately, Server call runs in the background, If the server fails, you may need to rollback