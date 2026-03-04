**Number of ways to create object in js**

1. Object Literals
2. new Keyword
3. Object.create()
4. Object.assign()
5. Using a constructor function
6. Using a class
7. Using ES6's Object.setPrototypeOf()

**Difference between own properties and inherited properties**
Own properties are directly defined on the object itself, while inherited properties are inherited from the object's prototype chain. Own properties can be accessed directly on the object, while inherited properties are accessed through the prototype chain.

**How does hasOwnProperty() work?**
The hasOwnProperty() method is used to check if an object has a specific property as its own property (not inherited). It returns true if the property exists directly on the object, and false if it is inherited from the prototype chain. This method is useful for distinguishing between own properties and inherited properties when iterating over an object's properties.

**What is the difference between enumerable and non-enumerable properties?**
Enumerable properties show up in loops like for...in and in Object.keys(). Non-enumerable properties exist but are hidden from iteration. By default, properties added to an object are enumerable, but you can make them non-enumerable using Object.defineProperty() method. Non-enumerable properties are typically used for internal or private data that should not be exposed during enumeration.

**How do you compare two object in javascript**
objects are compared by reference, not by value. This means that even if two objects have the same properties and values, they are considered different objects in memory. Therefore, using the strict equality operator (===) or the equality operator (==) will return false when comparing two different objects, even if their contents are identical.
//function to compare the object

**Check if the specific property exist in object or not**
using in and hasOwnProperty, hasOwn
difference : in checks = object + property while hasOwnProperty only checks objects property.

**merge object with the same id,Count Occurrences of Each ID**

**What is proto**
**_proto_** is an accessor property on JavaScript objects that points to the object’s internal prototype. 👉 It links an object to another object for inheritance.

```js
const obj = {};
console.log(obj.__proto__ === Object.prototype); // true
```

**Difference between prototype and proto**
| Feature | prototype | **proto** |
| ------- | ----------------------------------- | ------------------------ |
| Used by | Functions | Objects |
| Purpose | Property used when creating objects | Link to parent prototype |
| Example | `Person.prototype` | `obj.__proto__` |

Difference between freeze, seal and preventExtensions
| Method | Add | Delete | Modify Existing |
| ----------------- | --- | ------ | --------------- |
| preventExtensions | ❌ | ✔ | ✔ |
| seal | ❌ | ❌ | ✔ |
| freeze | ❌ | ❌ | ❌ |

> Object.freeze() is shallow.

> Default works only if value is undefined, not null.

**How to deep freeze an object**

**Why can it be slow?**

JavaScript engines (like V8):

Optimize objects using hidden classes

When you delete a property → object shape changes

Engine de-optimizes object → slower performance

**What new does internally**

- Creates empty object
- Sets its prototype to Object.prototype
- Binds this to that object
- Returns the object

**Object.Create** : Creates a new object with a specified prototype. It helps use or we can say this is cleanest way to do pure prototypal inheritance.

**structuredClone(obj)** : can handles Objects, Arrays, Map, Set, Date, Regex, Typed Arrays but don't function , dom nodes.

**JSON.stringify(obj)** : can't handles functions, undefined, Fails on circular references, losses date object type.

**Nullish Coalescing (??)** : Returns right-hand value only if left-hand side is: null, undefined. Else Use ?? when 0, false, or "" are valid values.

**Dynamic Imports** : Used for code splitting, Return a promise. Dynamic imports reduce initial bundle size and improve performance metrics like LCP.

**Garbage Collection** : Mark-and-Sweep Algorithm

1. Start from root references (global scope, stack)
2. Mark all reachable objects
3. Sweep (remove) unmarked objects

**Object Problems**

- Function to deep copy an object
- function to deep compare an object
- function to merge two objects
- function to count occurrences of each ID in an array of objects
- function to check if a specific property exists in an object or not
- function to create an object with a specific prototype
- function to freeze an object and prevent modifications
- function to seal an object and prevent adding or removing properties
- function to prevent extensions on an object and allow modifications to existing properties
- function to check if an object is frozen, sealed, or extensible
- function to list all own properties of an object
- function to list all inherited properties of an object
- function to check the given object is empty or not
- function to find duplicate objects from array
- function to delete property from object
- What’s the difference between comparing objects using == vs ===?
- How does Object.create() differ from {} or new Object()?
- What is the difference between dot notation and bracket notation?
- How do you use computed property names in objects?
- How can you dynamically add or access object properties?
- How do you find the object with the maximum/minimum value in an array?
- How do you group an array of objects by a property (e.g., age)?
- How do you remove duplicates from an array of objects?
- How do you sort an array of objects by a key?
- Explain spread/rest operators with objects.
- What is Object.hasOwn() and how is it different from hasOwnProperty?
- How would you merge multiple nested objects without losing nested data?
- How would you deeply clone an object that has arrays and nested objects?
- How would you count the occurrences of a value inside an array of objects?
- How would you convert an array of key-value pairs into an object?
- How do you remove duplicate objects from an array?
- What is immutability in objects?
- How does garbage collection work with objects?
- How does JS handle object references in memory?
- Flatten a nested object.
- Convert object to query string.
- Group array of objects by a key.
- Count frequency of properties in object.
- Convert object keys from camelCase to snake_case.