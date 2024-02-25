# React Usable Points

Its a repo for react points that we may have forgotten

### What is (vite) and whats different between vite and cra for create react app and also whats different between vite and webpack ?

Vite is a modern build tool and development server that aims to provide a faster and leaner development experience for modern web projects. Unlike Create React App (CRA), which uses Webpack as its build tool, Vite uses its own native build tool called esbuild for development and Rollup for production builds 12.

-- Here are the key differences between Vite and CRA:

1.Development Server : Vite provides a significantly faster development server due to its use of native ES modules and esbuild, while CRA uses the Webpack Dev Server.

2.Hot Reloading : Both Vite and CRA support hot reloading, but Vite's implementation is based on native ES modules, which leads to faster updates.

3.Build Performance : Vite is known for its efficient build performance, utilizing esbuild for pre-bundling dependencies and Rollup for producing optimized production builds.

4.Configuration : Vite offers a more flexible configuration system, allowing for customization of various aspects of the build process. CRA, on the other hand, provides a zero-configuration setup with sensible defaults.

5.Support for Modern Features : Vite has full support for modern JavaScript features like ES modules and TypeScript without requiring additional transpilation steps. CRA has limited support for pure JavaScript.

6.Code Splitting : In Vite, code splitting is manual, giving developers more control, whereas CRA handles code splitting automatically.

7.Community and Maintenance : CRA has been around longer and has a larger community, which can be beneficial for finding solutions to common problems. Vite is growing rapidly and is actively maintained.

Regarding Webpack, it is a well-established module bundler that is commonly used in many build processes. It is highly configurable and has a rich ecosystem of plugins and loaders. Vite, however, takes a different approach by focusing on speed and leveraging modern browser capabilities like ES modules. This results in a faster development experience with less configuration overhead.

-- In summary, Vite is a newer tool that offers a faster development experience and a more streamlined build process, particularly for projects that heavily rely on modern JavaScript features. CRA is a tried-and-true solution with a mature ecosystem and a no-configuration setup that is ideal for beginners or those who prefer a more established tool. Webpack is a powerful and configurable bundler that is widely used in the industry, but it may require more setup and configuration compared to Vite.
