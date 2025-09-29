---
duration: 1h
---

# Libraries and frameworks | with React and Next.js

## Library vs Framework

- **Libraries** are building blocks that can be used anywhere (like bricks)
- **Frameworks** dictate how your project will be structured (like frames)

![Library vs Framework](image/library-vs-framework.png)

## Points of using a framework

- Reuse essential building blocks:
  - avoid reinventing the wheel
  - focus on business logic
- Provide common guidelines and processes based on best-practices

Disadvantages

- Frameworks start lean and mean with a small surface area before becoming complex monsters
- Hard to extend and customize
- New frameworks come and go implying maintenance burden and technical debt
- Design architecture doesn't need to last for centuries
- See [Using a Framework will harm the maintenance of your software](https://berk.es/2022/09/06/frameworks-harm-maintenance/) - ([HN](https://news.ycombinator.com/item?id=33185010))

## Popular JavaScript front-end libraries and frameworks

- jQuery (2006), simplified HTML DOM tree traversal and manipulation
- AngularJS (2010), created by Google, complete framework for building web applications
- React (2013), created by Facebook, unlike AngularJS, library focused on building UI components
- Angular (2016), complete rewrite of AngularJS
- Vue.js (2014), inspired by AngularJS and React, progressive framework for building user interfaces

Today, you may also encounter:

- Svelte, a compiler that generates minimal and optimized JavaScript code
- Solid, inspired by React, but with a different reactivity model (signals)

## React

### What is React?

- JavaScript library - one of the most popular ones
- Not a framework (unlike Angular, which is more opinionated)
- Open-source project created by Facebook
- Used to build user interfaces (UI) on the front end
- The view layer of an MVC application (Model View Controller)

### DOM (Document Object Model)

- Programming interface for web documents
- Represents the document as nodes and objects
- Can be modified with JavaScript
- Browsers create DOM when a web page is loaded
- Constructed as a tree of Objects

![The HTML DOM Tree of Objects](image/html-to-dom.png)

### How React works?

- Isolates pieces of code in "components"
- Virtualizes the entire DOM and uses JavaScript to render actual HTML in the form of React Components
- Reactively keeps the DOM in sync with the updates to the current state
- If something has changed, React updates that part of the virtual DOM and re-renders the element

Follow the [official documentation](https://reactjs.org/docs/getting-started.html).

### React main concepts: Components

- Independent and reusable pieces of UI
- Can be nested, managed, and handled separately
- Two types of components:
  - Class components (older way)
  - Function components (modern way, with hooks)

Example of a function component:

```js
function MyComponent() {
  return (
    <div>
      <a href="https://impots.gouv.fr" target="_blank">
        Click me
      </a>
    </div>
  )
}
```

### React main concepts: JSX

- JavaScript Syntax Extension or JavaScript XML.
- Provides in-line ersatz HTML in JavaScript.
- Replaces `React.createElement()` calls.
- When React compiles, it uses a library called a transpiler (like [Babel](https://babeljs.io/)) to generate `createElement()` statements from the JSX.
- JSX is never rendered directly.

Previous example using `React.createElement()`:

```js
const MyComponent = React.createElement(
  'div',
  null,
  React.createElement(
    'a',
    { href: 'https://impots.gouv.fr', target: '_blank' },
    'Click me'
  )
)
```

### React main concepts: attaching components to the DOM

- React components are not HTML elements
- They need to be attached to the DOM using `ReactDOM.render()`

Example:

```js
import ReactDOM from 'react-dom'
import MyComponent from './MyComponent'

ReactDOM.render(<MyComponent />, document.getElementById('root'))
```

### React main concepts: State, props and hooks

- **State**: data that changes over time and affects what is rendered. Each component can have its own state.
- **Props**: short for properties, are a way of passing data from parent to child components. Props are read-only.
- **Hooks**: special functions that let you "hook into" React features. The most common hooks are `useState` (for state management) and `useEffect` (for side effects like data fetching).

Example of a component with state and props:

```js
import { useState } from 'react'

function Counter({ initialCount }) {
  const [count, setCount] = useState(initialCount)

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  )
}

function App() {
  return <Counter initialCount={0} />
}
```

## Frameworks

### Building Blocks of a Web Application

When building modern applications, you need to consider:

- **User Interface** - how users will consume and interact with your application.
- **Routing** - how users navigate between different parts of your application.
- **Data Fetching** - where your data lives and how to get it.
- **Rendering** - when and where you render static or dynamic content.
- **Integrations** - what third-party services you use (CMS, auth, payments, etc) and how you connect to them.
- **Infrastructure** - where you deploy, store, and run your application code (Serverless, CDN, Edge, etc).
- **Performance** - how to optimize your application for end-users.
- **Scalability** - how your application adapts as your team, data, and traffic grow.
- **Developer Experience** - your team’s experience building and maintaining your application.

[Read more](https://nextjs.org/learn/foundations/about-nextjs)

### Problems when building a web application with React from scratch

When building with React, you need to consider:

- Code has to be bundled using a bundler like [webpack](https://webpack.js.org/) and transformed using a compiler like [Babel](https://babeljs.io/).
- You need to do production optimizations such as code splitting.
- You might want to statically pre-render some pages for performance and SEO. You might also want to use server-side - rendering or client-side rendering.
- You might have to write some server-side code to connect your React app to your data store.

A framework can solve these problems.

[Read more](https://nextjs.org/learn/basics/create-nextjs-app)

### React-based frameworks

- [Next.js](https://nextjs.org/)
- [Remix](https://remix.run/)
- [React Router](https://reactrouter.com/)
- [Gatsby](https://www.gatsbyjs.com/)
- [Tanstack Start](https://tanstack.com/start/)

### Next.js

- Feature-rich React-based framework
- One of the most popular ones
- Gives you building blocks to create web applications

### Next.js features

- An intuitive page-based routing system (with support for dynamic routes)
- Pre-rendering, both static generation (SSG) and server-side rendering (SSR) are supported on a per-page basis
- Automatic code splitting for faster page loads
- Client-side routing with optimized prefetching
- Built-in CSS and Sass support, and support for any CSS-in-JS library
- Development environment with Fast Refresh support
- API routes to build API endpoints with Serverless Functions
- Fully extendable

## Demo

Task: Create a simple HTML page with a click counter - a button that increments the counter each time you click it.

- [Demo 1. "Old-school" way with native JavaScript](demo/demo-1)
- [Demo 2. Using React with `React.createClement()`](demo/demo-2)
- [Demo 3. Using React with JSX and Next.js framework](demo/demo-3)

---

*The content of this document, including all text, images, and associated materials, is the exclusive property of Adaltas and is protected by applicable copyright laws. Unauthorized distribution, reproduction, or sharing of this content, in whole or in part, is strictly prohibited without the express written consent of the author(s). Any violation of this restriction may result in legal action and the imposition of penalties as prescribed by law.*
