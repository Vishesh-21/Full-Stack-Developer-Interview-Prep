1. Callback - A callback is a function passed as an argument to another function, which is then executed later (usually after some operation finishes).

---

2. Inversion of control or Callback Hell - Callback inversion happens when you give control of when and how your callback is executed to another function or library, rather than controlling it yourself.
   `When you have many async tasks depending on each other, callback inversion can lead to deeply nested callbacks and confusing code and make It’s hard to manage and debug.`

---

3. Debouncing : delays function execution until a certain time has passed since the last event — helping optimize performance and prevent unnecessary work. `The function only runs after a certain amount of time has passed since the last time the event was triggered.`

---

4. Throttling : is a technique used to limit how often a function executes over time —
   even if an event (like scroll, resize, or mouse move) fires continuously. `In throttling, the function runs at most once every X milliseconds.`Throttling ensures a function runs at most once every fixed period of time — no matter how many times the event fires.

---

5. Synchronous programming : means tasks are executed one after another, in sequence.
   Each task must finish before the next one starts. It has blocking nature.

---

6. Asynchronous programming means tasks don’t block each other. A task can start, and while it’s waiting (for example, for data from a server), other tasks can run.

---

`JavaScript is single-threaded, meaning it can only execute one piece of code at a time.
But with asynchronous programming, it can preform many operation at a time without freezing the UI or blocking the main thread.`

---

                        ┌────────────────────────────┐
                        │        JavaScript          │
                        │        (Single Thread)     │
                        └────────────┬───────────────┘
                                     │
                                     ▼
                           ┌──────────────────┐
                           │   Call Stack     │
                           │ (Executes code)  │
                           └──────────────────┘
                                     │
                   ┌─────────────────┴──────────────────┐
                   ▼                                    ▼
       ┌────────────────────┐              ┌────────────────────┐
       │    Web APIs         │              │      Node APIs     │
       │ (Browser handles)   │              │ (libuv handles I/O)│
       │ setTimeout, fetch,  │              │ fs, http, crypto,  │
       │ event listeners...  │              │ timers, etc.       │
       └──────────┬──────────┘              └──────────┬──────────┘
                  │                                    │
                  ▼                                    ▼
        ┌──────────────────┐                ┌──────────────────┐
        │  Callback Queue  │                │ Microtask Queue  │
        │ (Macrotasks)     │                │ (Promises, async)│
        │ e.g., setTimeout │                │ e.g., .then(),   │
        │ I/O callbacks    │                │   await          │
        └────────┬─────────┘                └────────┬─────────┘
                 │                                   │
                 └────────────┬──────────────────────┘
                              ▼
                    ┌──────────────────┐
                    │   Event Loop     │
                    │ (The Coordinator)│
                    └──────────────────┘
                              │
                              ▼
                Checks if Call Stack is empty
                              │
           ┌──────────────────┴──────────────────┐
           ▼                                     ▼

Executes Microtasks (Promises) Executes Macrotasks (Timeouts, I/O)
│ │
└─────────────────────────────────────┘
│
▼
Repeats the cycle ♻️

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

10. Closures : A closure is when a function keeps access to variables from its parent function, even after the parent function has finished running.

---

11. Execution Context: The environment in which JS code runs (includes variables, this, and scope).

---

12. Call Stack: A stack where JS keeps track of function calls — last function in, first one out (LIFO).

---

13. Hoisting : JavaScript moves variable and function declarations to the top of their scope before execution. That’s why you can call a function before it’s defined.

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
