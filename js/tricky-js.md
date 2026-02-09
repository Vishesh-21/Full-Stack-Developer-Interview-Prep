1. ```js
   var x = 1;
   function foo() {
     console.log(x);
     var x = 2;
   }
   foo();
   ```

---

2. ```js
   const obj = {
     name: "JS",
     show() {
       console.log(this.name);
     },
   };
   const fn = obj.show;
   const { show } = obj;
   fn();
   ```

---

3. ```js
   const obj = {
     name: "JS",
     show() {
       console.log(this.name);
     },
   };
   const fn = obj.show;
   fn();
   // fn() is called without an object, so this is undefined in strict mode (or window in non-strict).
   ```

---

4. ```js
   const a = {};
   a.__proto__.x = 10;
   console.log(a.x);
   ```

---

5. ```js
   function A() {}
   A.prototype.x = 10;

   const a = new A();
   a.x = 20;

   console.log(a.x);
   ```

---

6. ```js
   function A() {}
   A.prototype.x = 10;
   const a = new A();
   delete a.x;
   console.log(a.x);
   ```

---

7. ```js
   for (var i = 0; i < 3; i++) {
     ((i) => {
       setTimeout(() => console.log(i), 0);
     })(i);
   }
   ```

---

8. ```js
   Promise.resolve().then(() => {
     console.log(1);
     Promise.resolve().then(() => console.log(2));
   });
   ```

---

9. ```js
   async function test() {
     await console.log(1);
     await console.log(2);
   }
   test();
   console.log(3);
   ```

---

10. ```js
    Promise.resolve(1)
      .then((x) => x + 1)
      .then((x) => Promise.resolve(x + 1))
      .then(console.log);
    ```

---

11. ```js
    console.log([] + []);
    console.log([] + {});
    console.log(!!"false" == !!"true");
    console.log(parseInt("10px"));
    console.log(parseInt("010"));
    // parseInt reads number from the start of string until it hits a non-digit.
    console.log(null == undefined); // null is only loosely equal to undefined and nothing else.
    console.log(null == 0);
    console.log(null == "");
    console.log(null == false);
    console.log(false == ""); // With loose equality, JavaScript converts operands to numbers when comparing boolean or string values with numbers
    console.log(null === undefined);
    console.log(Object.is(NaN, NaN));
    console.log(false == "0");
    console.log(NaN == NaN);
    console.log((0 && 1) || 2); // && return first falsy value 0 , || return first truthy value 2.
    //?. : If object is null or undefined, it returns undefined instead of throwing.
    console.log(Object.getPrototypeOf(Object.prototype));

    console.log([] == []);
    console.log([] == []); // both are false ,Arrays are objects, and objects are compared by reference.

    console.log("" == []); //true , [] is converted to a primitive. [].toString() → ""
    console.log("" === []); //false ,
    ```

---

12. ```js
    const obj = {
      x: 10,
      show() {
        setTimeout(function () {
          console.log(this.x);
        }, 0);
      },
    };
    obj.show();

    // inside show(), this is obj. But the function passed to setTimeout is a regular function, so it does not inherit this from show(). Regular functions get this from how they are called. setTimeout(function(){...}) → called by window/global → this ≠ obj.
    ```

---

13. ```js
    function A() {
      this.x = 10;
      return { x: 20 };
    }
    console.log(new A().x);

    //result = 20  --| When a constructor returns an object or function, that object is returned instead of this.

    //reason : Functions are first-class objects → can be assigned to variables, passed as arguments, or returned from other functions.
    ```

---

**Difference between Object.seal and Object.freeze**
| Feature | `Object.seal(obj)` | `Object.freeze(obj)` |
| ---------------------------------- | ------------------ | -------------------- |
| Can modify existing properties? | ✅ Yes | ❌ No |
| Can add new properties? | ❌ No | ❌ No |
| Can delete properties? | ❌ No | ❌ No |
| Makes object completely immutable? | ❌ No | ✅ Yes |

---

14. ```js
    function test(a) {
      arguments[0] = 10;
      console.log(a);
    }
    test(5);
    ```

---

15. ```js
    function test(a) {
      arguments[0] = 10;
      console.log(a);
    }
    test(5); // 10

    //In non-strict mode, arguments and named parameters are linked. In strict mode, arguments and parameters are not linked.
    ```

---

16. ```js
    const foo = function bar() {
      bar = 20;
      console.log(typeof bar);
    };
    foo();

    //bar is the function name, read-only inside the function. bar = 10 → ignored or throws in strict mode.
    ```

---

17. ```js
    async function test() {
      return await 10;
    }
    test().then(console.log);
    ```

---

18. ```js
    var a = 10;
    function test() {
      console.log(a);
      var a = 20;
    }
    test();
    ```

---

19. ```js
    const items = document.getElementsByClassName("item");
    document.body.removeChild(items[0]);
    console.log(items.length); //1

    const itemA = document.querySelectorAll(".item");
    document.body.removeChild(itemA[0]);
    console.log(itemA.length);
    ```

---

20. ```js
    <button id="btn">Click</button>
    <script>
      btn.addEventListener("click", () => {
        console.log("clicked");
      });
      btn.innerHTML = "New";
      btn.click();
      </script>
    ```

---

21. ```js
    <div id="box" style="display:none">Hello</div>

    <script>
      console.log(box.innerText);
      console.log(box.textContent);
    </script>
    ```

---

22. ```js
    const el = document.createElement("div");
    document.body.append(el);

    Promise.resolve().then(() => {
      el.textContent = "Updated";
    });
    console.log(el.textContent);
    ```

---

23. ```js
    var a = 10;
    console.log(delete a);
    console.log(a);


    <!-- follow up -->

    a = 10;
    console.log(delete a);
    console.log(a);

    // When a variable is assigned without using var, let, or const in non-strict mode, JavaScript creates it as a configurable property on the global object. Because it is configurable, the delete operator can remove it. After deletion, accessing it results in a ReferenceError.
    ```

> Note : When we manually reduce the length property of an array, JavaScript truncates the array and removes elements beyond that length

---

24. ```js
    function test(a, b) {
      arguments[1] = 20;
      console.log(b);
    }
    test(5);

    function test(a, b) {
      b = 50;
      console.log(arguments[1]);
    }
    ```

---

25. ```js
    console.log(null instanceof Object);
    setTimeout("console.log(1)", 0);
    //When a string is passed to setTimeout, JavaScript internally evaluates it using eval. So "console.log(1)" is treated like executable code and runs after the delay.
    ```

---

26. ```js
    function show() {
      console.log(this.x);
    }

    const obj = { x: 5 };
    const bound = show.bind(obj);

    bound.bind({ x: 10 })();
    ```

---

27. ```js
    box.style.width = "100px";
    console.log(box.offsetWidth);
    box.style.width = "200px";
    ```

---

28. ```js
      <div class="outer">
      <div class="inner"></div>
      </div>
      <script>
      console.log(
        document.querySelector(".inner")
        .closest(".outer")
        .className
      );
    </script>
    //closest searches upward.
    ```

---

29. ```js
    Promise.resolve(1)
      .then((x) => x + 1)
      .then((x) => Promise.resolve(x + 1))
      .then(console.log);

    //When you return a Promise inside .then(), JavaScript automatically unwraps it. So the next .then() receives 3, not a Promise.

    Promise.reject("err")
      .catch((err) => {})
      .then(() => console.log("done"));
    ```

---

30. ```js
    async function test() {
      await setTimeout(() => console.log(1), 0);
      console.log(2);
    }
    test();
    ```

---

31. ```js
    function test() {
      [1, 2, 3].forEach((x) => {
        if (x === 2) return;
        console.log(x);
      });
    }
    test();

    //❌ cannot break nor continue, return only exits the callback, not the loop

    //map() skips empty slots in sparse arrays.
    ```

---

32. ```js
    const arr = [1, , 3];
    const res = arr.map((x) => x * 2);
    console.log(res);
    console.log(1 in arr);
    console.log(1 in res);
    ```

---

33. ```js
    function A() {}
    const a = new A();
    console.log(a instanceof A);
    A.prototype = {};
    console.log(a instanceof A);
    ```

---

34. ```js
      <button id="btn">Click</button>
        <script>
          btn.onclick = () => console.log(1);
          btn.onclick = () => console.log(2);
        </script>
    ```
---

35. ```js 
      
