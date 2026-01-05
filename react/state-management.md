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


