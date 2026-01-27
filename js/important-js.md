**What are closures and what is use of closures?**
A closure is a feature where a function remembers and can access variables from its outer (lexical) scope, even after the outer function has finished executing.

**Use Cases:**

- Data Privacy
- Maintain State
- Function Factories

> When exactly is a closure created : Whenever a function is created inside another function and it uses variables from the outer function.

---

**What is IIEF? What is the use of IIFE?**
IIFE stands for Immediately Invoked Function Expression. It is a function that runs as soon as it is defined.

**Use cases**

- Avoid Global Variable Pollution
- Create Private Scope
- Run Code Only Once

> Note : !function () {}();

---

NaN !== anything (even NaN)
null == undefined (only this case)
Arrays & Objects → reference comparison
== converts types
=== does NOT

---

**How js code execute?**
A js engine has

- memory heap - where variables and objects are stored
- call stack - where function execution context is managed

**Two phases of code execution in js**

- **creation phase (compilation)**
  - creation global context execution (GCE
  - setup memory for variables and functions
  - hoisting of var and function declarations
  - set value of this
- **execution phase**
  - code execution line by line
  - assign values to variables
  - execute function calls
- **execution context**
  - Every time a function is called, a new execution context is created with: Variable Environment, Scope Chain, this keyword

> Microtasks always execute before macrotasks.

---

**Temporal Dead Zone** : The Temporal Dead Zone is the phase where a let or const variable is hoisted but not initialized, so accessing it before declaration throws a ReferenceError.

`example

```javascript
console.log(a); // ❌ ReferenceError
let a = 10;
```

- The scope is entered
- a exists in memory
- But it is uninitialized
- Accessing it before declaration triggers TDZ

`

---

**Prototype inheritance** is the mechanism by which JavaScript objects share properties and methods through an internal linkage called the prototype chain.

**Prototype** : Every JavaScript object has an internal reference called [[Prototype]] (accessible via **proto** or Object.getPrototypeOf()).

`How property looks up in javascript?`

- JavaScript looks on the object itself
- If not found, it looks on its prototype
- Continues up the prototype chain
- Stops at null (end of chain)

> note : **proto** is an accessor, not the prototype itself, Arrow functions do not have prototypes, Prototype inheritance ≠ class inheritance

---

**Inversion of control** : Control is handed over to another entity (framework, library, or function), which calls your logic. This is IoC.

```javascript
setTimeout(() => {
  console.log("Executed later");
}, 1000);
```

- You provide a function
- JavaScript runtime decides when to execute it

---

**async/await is syntactic sugar over Promises that makes asynchronous code easier to read and maintain, while Promises provide the core abstraction for async operations.**

---

**Execution Context :** An execution context is the environment created by JavaScript to execute code, containing variables, scope, and the this keyword.

Types of execution context:

- global ec
- function ec
- eval ec

**Phases of execution context**
Each execution context is created into two phases

- creation(memory allocation) : Allocates memory for variables and functions, variables declaration, store function declaration, set value of this.

- execution phase : code execute line by line, function invoked and variable receive values.

Note > Execution context is managed by the call stack.

---

**Difference between normal functions and arrow function**
| Feature | Arrow Function | Regular Function |
| ----------- | -------------- | ---------------- |
| `this` | Lexical | Dynamic |
| `arguments` | Not available | Available |
| Constructor | ❌ | ✅ |
| Hoisting | ❌ | ✅ |

---

**Prototype Inheritance** : is the mechanism by which JavaScript objects share properties and methods through an internal linkage called the prototype chain.JavaScript does not use classical class-based inheritance internally; it uses prototype-based inheritance.

**_what is prototype?_**
Every JavaScript object has an internal reference called [[Prototype]] (accessible via **proto** or Object.getPrototypeOf()). This reference points to another object from which properties and methods can be inherited.

**_How property lookup works?_**
JavaScript looks on the object itself, If not found, it looks on its prototype, Continues up the prototype chain, Stops at null (end of chain)

**Why use prototype inheritance?**

- memory efficient, Dynamic and flexible, core foundation of js.

> Arrow functions do not have prototypes

**How prototype and class inheritance differ form each other.**

- how inheritance work:
  - Prototype inheritance: Objects inherit directly from other objects via [[Prototype]].
  - Class inheritance: Classes inherit from other classes (a blueprint-to-blueprint model).

- Nature:
  - Prototype: Dynamic — you can change the prototype at runtime and all linked objects see it.
  - Class: Static — inheritance structure is mostly fixed after definition.

- Creation model:
  - Prototype: Objects are created first, then linked.
  - Class: Class is defined first, then objects (instances) are created.

> JS has no real classes internally. class syntax is just syntactic sugar over prototypes.

---

**If JavaScript already works, why add TypeScript at all?**

- We use TypeScript because it adds type safety to JavaScript, catches errors before runtime, and improves code readability and maintainability.
- It scales better for large applications.
- In the end, it compiles to JavaScript but gives a much better developer experience and reliability.

Note = Javascript is dynamical typed (bugs appear at the runtime means only encounter bugs when the code runs), typescript catches bugs before running the code.
**TypeScript = JavaScript + extra safety**

**Why typescript compiled to javascript?**

- Browser and nodejs only understand javascript not typescript, So typescript act like a development time safety layer, not a runtime language.

**Role of Typescript on large teams**

- Intelligent autocomplete
- Accurate refactoring
- Better documentation through types
- Safer code navigation
- solve the problem of Hard to know what data looks like
- Makes code review easier

**Does TypeScript add runtime overhead?**
No, Types are removed during compilation, Final JS is plain JavaScript, Performance is the same

In real analogy - js lets you write anything but ts make sure what you write actually make sense.

---

**Lexical Environment :** Lexical Environment in JavaScript is the internal memory space where variables and functions are stored based on where the code is written (lexical = location in code). It decides what variables a function can access.

---

**Why js is simple threaded\***
JavaScript is single-threaded, meaning it can execute only one task at a time on the call stack.

***Core Reason: Browser Safety***
JavaScript was designed to: Manipulate the DOM, Handle user interactions
If multiple threads modified the DOM simultaneously: Race conditions would occur, UI state would become unpredictable

so Single-threading ensures safe and consistent DOM updates.

***Simplicity & Predictability***
Avoids deadlocks, Makes debugging easier, Avoids complex thread synchronization

