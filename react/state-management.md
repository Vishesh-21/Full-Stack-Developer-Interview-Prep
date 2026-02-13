#### PropDrilling :

> Prop drilling means passing data (props) from a parent component down through multiple layers of child components—even when some of those components don’t need the data, but only pass it further.
> Problems occur :
>
> - Components receive props they don't need
> - Code becomes messy and harder to maintain
> - Changing data requires updating many components
> - Difficult to scale in large apps
> - Hard to reuse components

#### How Context api causes re-renders ?

> When you wrap components with a Context.Provider, Every time the value changes, all components consuming this context via useContext will re-render. Necessary to see updated data.
> Note -> React uses Object reference comparison (===) to decide if the value changed.If you pass a new object every render, all consumers re-render, even if the content is same.That’s why useMemo is recommended for objects or arrays.

#### Difference between context and redux?

> **Context** : Creates a global value ➡️ Makes it available to all consuming components ➡️ Triggers re-render of all consumers when value changes
> **Characteristics**
> State lives inside React, No rules on how state changes, No built-in optimization, No middleware or debugging tools

> **Redux** :Stores state in one central store ➡️ Updates state using pure reducer functions ➡️ Uses actions to describe what happened ➡️ Works outside React. Core principle or redux : Single source of truth, State is read-only, Changes via pure reducers

#### React Redux Tool Kit

> - Store – Holds the entire state of the app.Created with configureStore().
> - Slice – Combines state + reducers + actions in one place.Created with createSlice().
> - Actions – Functions that describe what to do (like increment, add item).Generated automatically by RTK.
> - Reducers – Functions that update the state based on actions.
> - Async Thunks – Handle asynchronous operations like API calls.Created with createAsyncThunk()

> Redux Toolkit (RTK) internally uses React Context API to connect Redux state with React components, but it adds a lot of extra machinery on top.

#### Role of Context in RTK

> React doesn’t know about Redux by default.So to make Redux state accessible in React components, RTK (or react-redux) uses Context API under the hood.
> When you wrap your app with <Provider store={store} ></Provider>: This <Provider> creates a React Context internally. It holds a reference to the Redux store. Any component using useSelector or useDispatch can access the store via that context.

#### Why Not Just Use Context API Directly?

> - Every consumer re-renders on any state change.
> - RTK/Redux allows selective updates via useSelector.
> - Built-in middleware support (thunks, logging, dev tools).
> - Predictable reducer pattern for managing complex state.
>   So RTK uses Context API internally, but adds subscription logic, selective rendering, and middleware on top.

> **NOTE : Redux enforces predictable state management using unidirectional data flow, while Redux Toolkit reduces complexity by eliminating boilerplate, handling immutability with Immer, and simplifying async logic through built-in tools like createAsyncThunk and RTK Query.**

**What performance issue does Context have? and redux solves**

- When a Context value changes, all consuming components re-render, even if they only use part of the value.
- This can slow down large apps with frequently changing global state.

**_How Redux solves it:_**

- Selective subscription: Components subscribe to specific slices of state, so unrelated updates don’t trigger re-renders.
- Optimized updates: Redux uses connect or useSelector with shallow equality checks to minimize renders.
- Middleware & batching: Allows more fine-grained control over updates.

> Context triggers all consumers on value change, causing performance hits; Redux allows selective updates, avoiding unnecessary re-renders.

#### Context vs Redux — what’s the real difference?

**_Context_** is just a way to avoid prop drilling.
It lets you share values (like theme, auth user, language) across the tree without passing props manually.

That’s it.

It is not a full state management system.

---

**_Redux_** is a complete state management solution.

It gives you:

- A single global store

- Predictable state updates

- Strict update flow (actions → reducers → store)

- DevTools, time-travel debugging

- Middleware for async logic

Redux is built for managing complex, shared, frequently changing state.

***What problem does Redux actually solve?***

When your app grows and:

- Many components need the same state

- State updates happen from different places

- Business logic becomes complex

- You need debugging visibility

- Async flows get messy

Redux gives structure and predictability. Without structure, state becomes chaos fast.

***Drawbacks of Context***

Context is fine for simple global state, but:

- Every value change re-renders all consumers

- No built-in structure for large state logic

- No middleware

- Harder to debug large state flows

- Can become messy if overused

It’s good for light stuff. Not heavy state.

***Drawbacks of Redux***

Redux can be:

- Boilerplate-heavy (though Redux Toolkit fixed a lot of that)

- Overkill for small apps

- Adds abstraction that junior devs struggle with

- Requires discipline and architecture thinking

- If your app is small, Redux is unnecessary weight.

***When to use what?***

Theme, auth info, small shared values → Context

Large app, complex state, async flows everywhere → Redux
