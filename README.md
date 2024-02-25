# React Usable Points

Its a repo for react points that we may have forgotten

### What is (vite) and whats different between vite and cra for create react app and also whats different between vite and webpack ?

Vite is a modern build tool and development server that aims to provide a faster and leaner development experience for modern web projects. Unlike Create React App (CRA), which uses Webpack as its build tool, Vite uses its own native build tool called esbuild for development and Rollup for production builds 12.

-- Here are the key differences between Vite and CRA :

1. Development Server : Vite provides a significantly faster development server due to its use of native ES modules and esbuild, while CRA uses the Webpack Dev Server.

2. Hot Reloading : Both Vite and CRA support hot reloading, but Vite's implementation is based on native ES modules, which leads to faster updates.

3. Build Performance : Vite is known for its efficient build performance, utilizing esbuild for pre-bundling dependencies and Rollup for producing optimized production builds.

4. Configuration : Vite offers a more flexible configuration system, allowing for customization of various aspects of the build process. CRA, on the other hand, provides a zero-configuration setup with sensible defaults.

5. Support for Modern Features : Vite has full support for modern JavaScript features like ES modules and TypeScript without requiring additional transpilation steps. CRA has limited support for pure JavaScript.

6. Code Splitting : In Vite, code splitting is manual, giving developers more control, whereas CRA handles code splitting automatically.

7. Community and Maintenance : CRA has been around longer and has a larger community, which can be beneficial for finding solutions to common problems. Vite is growing rapidly and is actively maintained.

Regarding Webpack, it is a well-established module bundler that is commonly used in many build processes. It is highly configurable and has a rich ecosystem of plugins and loaders. Vite, however, takes a different approach by focusing on speed and leveraging modern browser capabilities like ES modules. This results in a faster development experience with less configuration overhead.

-- In summary, Vite is a newer tool that offers a faster development experience and a more streamlined build process, particularly for projects that heavily rely on modern JavaScript features. CRA is a tried-and-true solution with a mature ecosystem and a no-configuration setup that is ideal for beginners or those who prefer a more established tool. Webpack is a powerful and configurable bundler that is widely used in the industry, but it may require more setup and configuration compared to Vite.

### React Lifecycle Explained

Every React component undergoes a well-defined lifecycle, encompassing four distinct phases : Mounting, Updating, Unmounting, and Error Handling. These phases are orchestrated by React itself, ensuring predictable behavior and enabling us to perform specific actions at each stage.

#### 1. Mounting Phase

- constructor() :
  This method, invoked before render(), is ideal for initializing state and binding event handlers. It receives the component's props as an argument.

  Usage :
  Initialize state using this.state = { /_ initial state object _/ };
  Bind event handlers using this.handleClick = this.handleClick.bind(this); (in class components only)

<hr>

- getDerivedStateFromProps(nextProps, prevState) (Optional) :
  This method, introduced in React 16.3, allows you to derive updates to the component's state based on changes in its props or previous state. It receives the component's nextProps and prevState as arguments and should return a new state object if necessary, or null if no state update is required.

  Usage :
  Return a new state object : return { /_ new state object _/ };
  Return null to indicate no state update : return null;

<hr>

- render() :
  This method, the heart of a React component, returns the JSX (JavaScript XML) that defines the UI elements to be rendered. React uses this output to update the DOM.

  Usage :
  Return valid JSX elements same below

```jsx
<div> Hello, world!</div>
```

<hr>

- componentDidMount() :
  This method is invoked immediately after the component is mounted (inserted into the DOM). This is the place to perform side effects such as fetching data from an API, initializing subscriptions, or integrating with third-party libraries.

  Usage :
  Fetch data : fetch('https ://api.example.com/data') .then(response => response.json()) .then(data => this.setState({ /_ update state with fetched data _/ }));`
  Set up subscriptions : this.subscription = someService.subscribe(/_ callback _/);

#### 2. Updating Phase

- getSnapshotBeforeUpdate(prevProps, prevState) (Optional) :
  This method, introduced in React 16.3, allows you to capture information from the DOM before an update occurs. It receives the component's prevProps and prevState as arguments and should return a value that will be passed as an argument to componentDidUpdate(prevProps, prevState, snapshot).

  Usage :
  Return a value to be passed to componentDidUpdate : return { /_ value to capture _/ };

<hr>

- shouldComponentUpdate(nextProps, nextState) (Optional) :
  This method, invoked before an update, allows you to control whether the component should re-render based on changes in props or state. It receives the component's nextProps and nextState as arguments and should return true if a re-render is necessary, or false otherwise. Use this method judiciously to optimize performance.

  Usage :
  Return true to re-render : return true;
  Return false to skip re-rendering : return false; (use with caution)
  getDerivedStateFromProps(nextProps, prevState) (Optional) : If present, this method is called again during the update phase to compute any state updates based on the new props and previous state. It follows the same rules and usage as described in the mounting phase.

<hr>

- render() :
  Just like in the mounting phase, render() is called to determine the updated JSX output.

<hr>

- componentDidUpdate(prevProps, prevState, snapshot) (Optional) :
  This method is invoked immediately after the component is updated (DOM changes are reflected). It is useful for performing actions that depend on DOM updates, such as manipulating DOM elements directly (use with caution) or synchronizing external state.

  Usage :
  Access DOM elements using refs : this.myRef.current.focus(); (use with caution)
  Update external state : someExternalState.update(/_ updated data _/);

#### 3. Unmounting Phase

- componentWillUnmount() :
  This method is invoked immediately before the component is unmounted (removed from the DOM). This is where you should perform cleanup tasks such as clearing subscriptions, timers, or event listeners to prevent memory leaks and avoid stale references.
