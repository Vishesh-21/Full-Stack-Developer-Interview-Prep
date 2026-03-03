1. Callback - A callback is a function passed as an argument to another function, which is then executed later (usually after some operation finishes).

---

2. Inversion of control or Callback Hell - Callback inversion happens when you give control of when and how your callback is executed to another function or library, rather than controlling it yourself.
   `When you have many async tasks depending on each other, callback inversion can lead to deeply nested callbacks and confusing code and make It’s hard to manage and debug.`

---

3. Debouncing : delays function execution until a certain time has passed since the last event — helping optimize performance and prevent unnecessary work. `The function only runs after a certain amount of time has passed since the last time the event was triggered.`

---

4. Throttling : is a technique used to limit how often a function executes over time —
   even if an event (like scroll, resize, or mouse move) fires continuously. `In throttling, the function runs at most once every X milliseconds.`

---

5. Synchronous programming : means tasks are executed one after another, in sequence.
   Each task must finish before the next one starts. It has blocking nature.

---

6. Asynchronous programming means tasks don’t block each other. A task can start, and while it’s waiting (for example, for data from a server), other tasks can run.

---

`JavaScript is single-threaded, meaning it can only execute one piece of code at a time.
But with asynchronous programming, it can preform many operation at a time without freezing the UI or blocking the main thread.`

---

> NodeJs is single threaded for javaScript execution, but multi threaded internally.

**Event loops** : Event Loop is a mechanism that allows JavaScript (Node.js) to run non-blocking asynchronous code on a single thread.

**How does event loop works**

1. Call Stack executes synchronous code.
2. Async tasks (setTimeout, fs, API) go to: web apis, libuv
3. When finished → callback goes to Callback Queue.
4. Event Loop checks: If Call Stack is empty → move callback to stack.
5. Execute callback.

---

7. Event bubbling : means when you click on an element, the event also moves up (bubbles) to its parent elements.

---

8. Event delegation : means you put one event listener on a parent element to handle events from all its child elements — instead of adding listeners to each child.

---

9. Currying : means breaking a function with multiple arguments into a series of functions, each taking one argument at a time.
   use:
   - Helps reuse functions easily.
   - Makes functions more flexible and modular.

> Infinite currying : means creating a function that can be called repeatedly with one argument at a time, without a fixed number of parameters — until you decide to stop it.

---

10. Closures : A closure is when a function keeps access to variables from its parent function, even after the parent function has finished running. Closure is needed to preserve state and create private variables in JavaScript.

---

11. Execution Context: The environment in which JS code runs (includes variables, this, and scope).

---

12. Call Stack: A stack where JS keeps track of function calls — last function in, first one out (LIFO).

---

13. Hoisting : JavaScript moves variable and function declarations to the top of their scope before execution. That’s why you can call a function before it’s defined.

> Variable declarations (var, let, const) are hoisted, but only var is initialized with undefined.

---

14. Generators : Functions that can pause and resume execution.

```javascript
function* counter() {
  yield 1;
  yield 2;
  yield 3;
}
const c = counter();
console.log(c.next().value); // 1
console.log(c.next().value); // 2
```

---

15. Temporal Dead Zone : The time between entering a scope and the actual declaration where accessing let/const throws an error.

---

16. First class functions : In JavaScript, a first-class function means functions are treated as values — they can be assigned to variables, passed as arguments, or returned from other functions.

---

17. Module Pattern : The Module Pattern allows you to create private and public members inside an object by using a function that returns an object.

```javascript
const CounterModule = (function () {
  // Private variable
  let count = 0;

  // Public methods (returned object)
  return {
    increment: function () {
      count++;
      console.log(count);
    },
    decrement: function () {
      count--;
      console.log(count);
    },
    getCount: function () {
      return count;
    },
  };
})();
```

---

18. Memoization : Memoization is a specific type of caching used to store results of function calls based on their input parameters, so if the same inputs occur again, the stored result is returned instead of recalculating. It’s an optimization technique for expensive or repetitive computations.

---

19. Function what thats any functions and then convert it into curried form.

```javascript
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn(...args);
    } else {
      return function (...nextArgs) {
        return curried(...args, ...nextArgs);
      };
    }
  };
}
```

---

22. globalThis is a universal global object in JavaScript introduced to solve the problem of accessing the global scope in any environment (browser, Node.js, Web Workers, etc.).

**NOTE** : Regular function inside setTimeout loses object context.

---

**Lexical Environment :** A lexical environment is the place where a function or block keeps track of its variables, along with a reference to its outer environment. Lexical environment enables scopes and closures in javascript.
