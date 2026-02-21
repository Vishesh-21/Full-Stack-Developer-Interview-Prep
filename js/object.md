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

**Function to deep clone an object**

**How do you compare two object in javascript**
objects are compared by reference, not by value. This means that even if two objects have the same properties and values, they are considered different objects in memory. Therefore, using the strict equality operator (===) or the equality operator (==) will return false when comparing two different objects, even if their contents are identical.
//function to compare the object

**How do you check is object is empty or not**

**How do you find duplicates object in array**

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