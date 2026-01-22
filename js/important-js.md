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

**Difference between normal functions and arrow function**
| Feature | Arrow Function | Regular Function |
| ----------- | -------------- | ---------------- |
| `this` | Lexical | Dynamic |
| `arguments` | Not available | Available |
| Constructor | ❌ | ✅ |
| Hoisting | ❌ | ✅ |
