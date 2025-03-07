API Reference
React Reference Overview
This section provides detailed reference documentation for working with React. For an introduction to React, please visit the Learn section.

The React reference documentation is broken down into functional subsections:

React 
Programmatic React features:

Hooks - Use different React features from your components.
Components - Built-in components that you can use in your JSX.
APIs - APIs that are useful for defining components.
Directives - Provide instructions to bundlers compatible with React Server Components.
React DOM 
React-dom contains features that are only supported for web applications (which run in the browser DOM environment). This section is broken into the following:

Hooks - Hooks for web applications which run in the browser DOM environment.
Components - React supports all of the browser built-in HTML and SVG components.
APIs - The react-dom package contains methods supported only in web applications.
Client APIs - The react-dom/client APIs let you render React components on the client (in the browser).
Server APIs - The react-dom/server APIs let you render React components to HTML on the server.
Rules of React 
React has idioms — or rules — for how to express patterns in a way that is easy to understand and yields high-quality applications:

Components and Hooks must be pure – Purity makes your code easier to understand, debug, and allows React to automatically optimize your components and hooks correctly.
React calls Components and Hooks – React is responsible for rendering components and hooks when necessary to optimize the user experience.
Rules of Hooks – Hooks are defined using JavaScript functions, but they represent a special type of reusable UI logic with restrictions on where they can be called.
API Reference
Built-in React Hooks
Hooks let you use different React features from your components. You can either use the built-in Hooks or combine them to build your own. This page lists all built-in Hooks in React.

State Hooks 
State lets a component “remember” information like user input. For example, a form component can use state to store the input value, while an image gallery component can use state to store the selected image index.

To add state to a component, use one of these Hooks:

useState declares a state variable that you can update directly.
useReducer declares a state variable with the update logic inside a reducer function.
function ImageGallery() {
  const [index, setIndex] = useState(0);
  // ...
Context Hooks 
Context lets a component receive information from distant parents without passing it as props. For example, your app’s top-level component can pass the current UI theme to all components below, no matter how deep.

useContext reads and subscribes to a context.
function Button() {
  const theme = useContext(ThemeContext);
  // ...
Ref Hooks 
Refs let a component hold some information that isn’t used for rendering, like a DOM node or a timeout ID. Unlike with state, updating a ref does not re-render your component. Refs are an “escape hatch” from the React paradigm. They are useful when you need to work with non-React systems, such as the built-in browser APIs.

useRef declares a ref. You can hold any value in it, but most often it’s used to hold a DOM node.
useImperativeHandle lets you customize the ref exposed by your component. This is rarely used.
function Form() {
  const inputRef = useRef(null);
  // ...
Effect Hooks 
Effects let a component connect to and synchronize with external systems. This includes dealing with network, browser DOM, animations, widgets written using a different UI library, and other non-React code.

useEffect connects a component to an external system.
function ChatRoom({ roomId }) {
  useEffect(() => {
    const connection = createConnection(roomId);
    connection.connect();
    return () => connection.disconnect();
  }, [roomId]);
  // ...
Effects are an “escape hatch” from the React paradigm. Don’t use Effects to orchestrate the data flow of your application. If you’re not interacting with an external system, you might not need an Effect.

There are two rarely used variations of useEffect with differences in timing:

useLayoutEffect fires before the browser repaints the screen. You can measure layout here.
useInsertionEffect fires before React makes changes to the DOM. Libraries can insert dynamic CSS here.
Performance Hooks 
A common way to optimize re-rendering performance is to skip unnecessary work. For example, you can tell React to reuse a cached calculation or to skip a re-render if the data has not changed since the previous render.

To skip calculations and unnecessary re-rendering, use one of these Hooks:

useMemo lets you cache the result of an expensive calculation.
useCallback lets you cache a function definition before passing it down to an optimized component.
function TodoList({ todos, tab, theme }) {
  const visibleTodos = useMemo(() => filterTodos(todos, tab), [todos, tab]);
  // ...
}
Sometimes, you can’t skip re-rendering because the screen actually needs to update. In that case, you can improve performance by separating blocking updates that must be synchronous (like typing into an input) from non-blocking updates which don’t need to block the user interface (like updating a chart).

To prioritize rendering, use one of these Hooks:

useTransition lets you mark a state transition as non-blocking and allow other updates to interrupt it.
useDeferredValue lets you defer updating a non-critical part of the UI and let other parts update first.
Other Hooks 
These Hooks are mostly useful to library authors and aren’t commonly used in the application code.

useDebugValue lets you customize the label React DevTools displays for your custom Hook.
useId lets a component associate a unique ID with itself. Typically used with accessibility APIs.
useSyncExternalStore lets a component subscribe to an external store.
useActionState allows you to manage state of actions.
Your own Hooks 
