**Classes** : A class in JavaScript is a blueprint for creating objects that encapsulates data (properties) and behavior (methods). They are introduce in ES6.

> Important: JavaScript classes are syntactic sugar over the existing prototype-based inheritance system.

**component of class**

- constructor : Special method called automatically when an object is created, one per class, if not defined then js create default one.

- methods : Functions defined inside a class, store as prototype not on each object.

> Classes are hoisted but not initialized.

> super() must be called before using this

- Method Overriding : Child method replaces parent method, Can still call parent using super.greet()

- Static method : Static methods belong to the class itself, not to instances.

- Private data & methods : using #

```js
class A {
  method() {}
}

//internal become

function A() {}
A.prototype.method = function () {};
```
