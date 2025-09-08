---
duration: 1h
---

# Getting started with JavaScript, Node.js, and Asynchronous Programming

## Web development languages and frameworks

Langage / Framework | Start | Used for
--- | --- | ---
Perl / CGI | 1990s | Initial CGI scripts
PHP | 1995 | Dynamic sites, WordPress, CMS
Java / Servlets, Spring | 1999 / 2002 | Enterprise apps, RESTAPI
Ruby on Rails | 2005 | Rapid MVPs, startups
Python / Django | 2005 | Full‑stack apps, auto‑generated admin
Python / Flask | 2010 | Microservices, lightweight APIs
Python / FastAPI | 2019 | High-performance APIs, async
Javascript / Node.js + Express | 2009 | Event-driven apps, real‑time, full‑stack JS

### Why using JavaScript for this course?

- Industry standard: JavaScript is the most widely used language for web development
- Full-stack JavaScript: Same language for front-end and back-end
- Rich ecosystem: npm, frameworks (Express, Next.js, etc.) and community support
- TypeScript: Optional static typing for better tooling and maintainability

Highlights:

- No relation to Java
- Multi-paradigm: scripting, object-oriented, functional, imperative, event-driven
- Single-threaded and synchronous (asynchronous I/O with event loop)
- Runs natively in web browsers

### A brief history of JavaScript

- 1995: Created by Brendan Eich at Netscape (in 10 days)
- Named Mocha, then LiveScript, then JavaScript
- 1996: Shipped with IE3 in 1996 as JScript (as Netscape owned the JavaScript trademark)
- 1996: Standardized as ECMAScript (ES) by ECMA International
- 1997: ES1 released
- 2009: Node.js created by Ryan Dahl
- 2010: npm (Node Package Manager) introduced
- 2015: ES6 released, major update with classes, modules, arrow functions, promises
- 2020: Node.js 14.0.0 released, with native ES modules
- Since ES6, a new version is released every year

## JavaScript Runtime and Node.js

- JavaScript: Originally a client-side scripting language for web browsers
- Engine: Executes JavaScript code, implementation of ECMAScript (ex: V8, SpiderMonkey, JavaScriptCore)
- Runtime: Engine + API and libraries for additional functionality (ex: Chrome, Firefox, Node.js)
- Node.js: JavaScript runtime built on Chrome's V8 engine, allows running JavaScript on the server side
  - Provides APIs for file system, networking, and more

## Javascript modules

- Modules: Reusable pieces of code that can be imported and exported
- Node.js introduced its own module system before ES Modules were standardized:
  - CommonJS: Module system used in Node.js (uses `require` and `module.exports`)
  - ES Modules: Standardized module system (uses `import` and `export`)

### CommonJS vs ES Modules

- CommonJS:
  - Synchronous loading
  - Uses `require()` to import modules
  - Uses `module.exports` or `exports` to export modules
  - Example:

    ```js
    // math.js
    function add(a, b) {
      return a + b;
    }
    module.exports = { add };

    // main.js
    const { add } = require('./math');
    console.log(add(2, 3)); // 5
    ```

- ES Modules:
  - Asynchronous loading
  - Uses `import` to import modules
  - Uses `export` to export modules
  - Example:

    ```js
    // math.js
    export function add(a, b) {
      return a + b;
    }

    // main.js
    import { add } from './math.js';
    console.log(add(2, 3)); // 5
    ```

## Javascript packages

- What we call a library in other languages
- A directory that contains one or more `.js` files
- A directory that contains a `package.json` file at its root, describing:
  - General informations: `name`, `description`, `version`, `license`
  - Is the project private: `private`
  - Scripts and commands: `scripts`
  - Dependencies: `dependencies` and `devDependencies`
  - Full properties list: <https://docs.npmjs.com/files/package.json>
- Use the `npm init` command to create a new package

Package structure example:

```txt
ece-webtech/
├── index.js
└── package.json
```

### `package.json` file

It stores a package's information:

- `name`, `description`, `version`, `license` and `private`
- `dependencies` and `devDependencies`
- scripts and commands

```json
{
  "name": "ece-webtech",
  "description": "Node.js project for ECE class",
  "version": "0.0.0",
  "license": "UNLICENSED",
  "private": false,
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {},
  "devDependencies": {}
}
```

## Dependencies

- Packages can depend on other packages (dependencies)
- Declared in the `package.json` file under `dependencies` and `devDependencies`
- Installed using a package manager (e.g., npm, yarn, pnpm)
- Installed dependencies are stored in the `node_modules` directory
- Each dependency can also possess its own set of dependencies, leading to a hierarchy.

### Declare dependencies

In the `package.json` file:

- `dependencies`: Essential for the app to operate.
- `devDependencies`: Required only during development like test runners or documentation tools.

Example of declaration in package.json:

```js
{ "dependencies": {
  "foo": "^1.0.0", // dependency with a version constraint
  "baz": "file:/path/to/file", // local dependency
  "bar": "http://web.site/my.tar.gz" // remote dependency
  },
  "devDependencies": {
    "test": "1.0.0"
  }
}
```

Refer to [package.json documentation](https://docs.npmjs.com/files/package.json) for more details.

### Package managers

- Tools that automate the process of installing, upgrading, configuring, and removing packages.
- Help manage project dependencies efficiently.
- Ensure consistent environments across different setups.
- Main package managers for JavaScript:
  - NPM (Node Package Manager): Shipped with Node.js, most widely used.
  - Yarn: Developed by Facebook to address some NPM issues. Since then, both are quite similar.
  - pnpm: Manages dependencies differently, more efficient in some cases.

#### Example installation with NPM

Initialize a new Node.js project:

```sh
npm init -y
```

Install two packages:

```sh
npm install package1 package2
```

The project structure will look like this:

```txt
ece-webtech/
├── index.js
├── node_modules/
│   ├── package1/
│   │   ├── index.js
│   │   └── package.json
│   └── package2/
│       ├── index.js
│       └── package.json
├── package.json
└── package-lock.json (or yarn.lock, or pnpm-lock.yaml)
```

In the `package.json` file:

```json
{
  "name": "ece-webtech",
  "description": "Node.js project for ECE class",
  "version": "0.0.0",
  "license": "UNLICENSED",
  "private": false,
  "scripts": {
    "start": "node index.js"
  },
  "dependencies": {
    "package1": "^1.0.0",
    "package2": "^2.0.0"
  },
  "devDependencies": {}
}
```

### Versioning with Semver

Semantic Versioning (Semver) is a convention to version packages.

- Version format is `X.Y.Z`
  - X: Major - introduces breaking changes.
  - Y: Minor - adds new features while maintaining backward compatibility.
  - Z: Patch - primarily for bug fixes.
- Version 0.Y.Z indicates initial development and might be unstable.

Use the following syntax to specify a version in the `package.json` file:

- `1.2.3` - exact version
- `~1.2.3` - major and minor versions must match
- `^1.2.3` - major version must match
- `>1.2.3` - any superior to 1.2.3
- `1.2.x` - any 1.2 version

Learn more about [Semantic Versioning](https://semver.org/).

Using conventional commit messages and tools like [semantic-release](https://semantic-release.gitbook.io/semantic-release/) can help automate versioning.

### Deterministic installs with lock files

- Lock files, such as package-lock.json for NPM and yarn.lock for YARN, ensure consistent dependency versions across installations.
- Helps avoid discrepancies between developer environments, preventing the "but it works on my computer!" issue.

## Asynchronous programming

- Synchronous: Blocking, sequential execution (e.g., traditional function calls)
- Asynchronous: Non-blocking, allows other code to run while waiting for operations (e.g., I/O operations)

<!-- ## JavaScript event loop

- Event loop: Mechanism that allows JavaScript to perform non-blocking I/O operations
- Call stack: Where function calls are executed
- Callback queue: Holds functions to be executed after the current call stack is empty
- Microtask queue: Holds promises and other microtasks to be executed after the current task but before the next event loop iteration
- Example: When an I/O operation is initiated, the event loop allows the program to continue executing other code while waiting for the I/O operation to complete. Once the operation is done, the callback is added to the callback queue, and the event loop processes it -->

### Asynchronous patterns: callbacks

Callbacks: Functions passed as arguments to be executed later (e.g., `setTimeout`, event listeners).

```js
function fetchDataCallback(callback) {
  setTimeout(() => {
    // first arg is error (null if OK), second is result
    callback(null, { id: 1, name: 'Alice' });
  }, 500);
}

// Usage:
fetchDataCallback((err, user) => {
  if (err) {
    console.error('Error:', err);
    return;
  }
  console.log('User fetched (callback):', user);
});
```

#### Asynchronous patterns: callback hell

Callback hell: A situation where multiple nested callbacks make code hard to read and maintain.

```js
// reuse fetchDataCallback() from above

// Fetch user
fetchDataCallback((err, user) => {
  if (err) {
    console.error('Error:', err);
    return;
  }
  console.log('User fetched (callback):', user);
  // Fetch posts for the user
  fetchDataCallback((err, posts) => {
    if (err) {
      console.error('Error:', err);
      return;
    }
    console.log('Posts fetched (callback):', posts);
    // Fetch comments for the first post
    fetchDataCallback((err, comments) => {
      if (err) {
        console.error('Error:', err);
        return;
      }
      console.log('Comments fetched (callback):', comments);
    });
  });
});
```

### Asynchronous patterns: promises

Promises: Objects representing the eventual completion (or failure) of an asynchronous operation, providing a cleaner way to handle asynchronous code.

Promises flatten the nesting and let chain `.then()` calls.

```js
function fetchDataPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => resolve({ id: 1, name: 'Alice' }), 500);
  });
}

// Usage:
fetchDataPromise()
  .then(user => {
    console.log('User fetched (promise):', user);
    return user.id;
  })
  .then(id => {
    // another async step
    return new Promise(res => setTimeout(() => res(id * 10), 300));
  })
  .then(result => {
    console.log('Final result (promise):', result);
  })
  .catch(err => {
    console.error('Error:', err);
  });
```

### Asynchronous patterns: async/await

Async/await: Syntactic sugar built on top of promises, allowing asynchronous code to be written in a more synchronous style, improving readability.

```js
// reuse fetchDataPromise() from above

async function run() {
  try {
    const user = await fetchDataPromise();
    console.log('User fetched (async/await):', user);

    // another async step:
    const computed = await new Promise(res =>
      setTimeout(() => res(user.id * 10), 300)
    );
    console.log('Final result (async/await):', computed);

  } catch (err) {
    console.error('Error:', err);
  }
}

run();
```
