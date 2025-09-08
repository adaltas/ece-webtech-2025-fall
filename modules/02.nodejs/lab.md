---
duration: 2h
---

# Lab: getting started with Node.js & Git

## Objectives

- Getting up and ready with Node.js
- Project and repository initialization
- Web server in Node.js

## Tasks

1. Start a project
1. Create a simple Node.js script
1. Create a simple HTTP server
1. Integrate Nodemon
1. Create a basic application with multiple routes
1. Reading from a JSON file
1. Publish your project to GitHub

## Notes

The lab starts a new Node.js project which serves as the basis for the following courses. Every week, incremental features are completed toward the creation of a working application.

In the end, it becomes the basis for your final project. The final grade reflects the delivered project, as well as its Git history.

## Prerequisites: Node.js installation

- Linux / macOS, don't use the installer or your package manager.
- We want to be able to switch between multiple Node.js versions.
- We want Node.js to be installed inside your home directory, with administrative permissions (no `sudo`).
- Use [`n-install`](https://github.com/mklement0/n-install), a script to install [`n`](https://github.com/tj/n).

## Create a simple Node.js script

### Start working with a text editor

Now, we start using a text editor or IDE (Atom, VS Code, WebStorm, or up to your choice).

Open a project folder in your editor. You also can use bash commands for opening it. Being under the root of the project directory, run one of the commands:

```bash
# For VS Code
code .
# For power users
vim .
```

### Create a script

Create a file `index.js` with the following content:

```js
console.log("Hello Node.js!")
```

Run the Node.js script in the terminal:

```bash
node index.js
```

It will print the message `Hello Node.js!`.

### Initialize a Node.js project

Run the command:

```bash
npm init
```

It will create a `package.json` file for you. Later, you can manually modify the content respecting the [JSON format](https://en.wikipedia.org/wiki/JSON). For example, these values:

- `author`
- `description`

### Define an NPM script

Add the script `start` to the `package.json` file like this:

```json
{
  ...
  "scripts": {
    "start": "node index.js"
  },
  ...
}
```

Run the NPM script with the command:

```bash
npm run start
# or
npm start
```

It will do the same as in step 2.

### Initialize a Git repository

Run the command:

```bash
git init
```

It will create a `.git` folder for you.

Create a `.gitignore` file to avoid committing unnecessary files like:

```txt
.DS_Store
/node_modules
```

Perform the first commit:

```bash
git add .
git commit -m "Initial commit"
```

## Create an HTTP server

### Basic HTTP server implementation

Modify the `index.js` file with the following content

```js
// Import a module
const http = require('http')

// Declare an http server
http.createServer(function (req, res) {

  // Write a response header
  res.writeHead(200, {'Content-Type': 'text/plain'})

  // Write a response content
  res.end('Hello World\n')

// Start the server
}).listen(8080)
```

Read and understand each line in this code using the [`http` Node.js official module documentation](https://nodejs.org/api/http.html).

### Run HTTP server

Run the command:

```bash
npm run start
```

It will start a web server accessible on <http://localhost:8080>:

- open it in a browser
- or `curl localhost:8080` in a terminal to get the home page content

### Define callback function

Rewrite the code to define a callback function

```js
const serverHandle = function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'})
  res.end('Hello World\n')
}

http
.createServer(serverHandle)
.listen(8080)
```

Don't forget to restart the server. To terminate a blocking process in the terminal use the combination of keys `Ctrl + C`. Start it again with `npm start`.

### Sending back HTML

Change the content type & response content:

```js
// Define a string constant concatenating strings
const content = '<!DOCTYPE html>' +
'<html>' +
'    <head>' +
'        <meta charset="utf-8" />' +
'        <title>ECE AST</title>' +
'    </head>' + 
'    <body>' +
'       <p>Hello World!</p>' +
'    </body>' +
'</html>'

const serverHandle = function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/html'})
  res.write(content)
  res.end()
}

http
.createServer(serverHandle)
.listen(8080)
```

### Get the current path

A path is the part of the URL that comes after the domain name. For example, in `http://localhost:8080/my/path`, the path is `/my/path`.

Enrich the previous code with the following:

```js
// Import Node url module
const url = require('url')

const serverHandle = function (req, res) {
  // Retrieve and print the current path
  const path = url.parse(req.url).pathname
  console.log(path)

  res.writeHead(200, {'Content-Type': 'text/html'})
  res.write(path)
  res.end()
}

http
.createServer(serverHandle)
.listen(8080)
```

Access to your local website by different URLs like `localhost:8080` and `localhost:8080/my/path` and see what is printed in the terminal.

### Get query parameters

Web URLs can be enriched with query parameters, which come after the `?` and are separated by `&`, formatted as `key=value`.

```txt
http://my.site/my/page.html?username=toto&password=lulu
```

These parameters can be parsed with Node's `querystring` module on the URL's query property.

Enrich the previous code with the following:

```js
const url = require('url')
const qs = require('querystring')

const serverHandle = function (req, res) {
  // Retrieve and print the queryParams
  const queryParams = qs.parse(url.parse(req.url).query)
  console.log(queryParams)

  res.writeHead(200, {'Content-Type': 'text/html'})
  res.write(content)
  res.end()
}

http
.createServer(serverHandle)
.listen(8080)
```

Access your local website by different URLs like `localhost:8080/?name=John&email=john@email.com`, and see what is printed in the terminal.

### Basic routing example

Enrich the previous code with the following:

```js
const url = require('url')
const qs = require('querystring')

const serverHandle = function (req, res) {
  const route = url.parse(req.url)
  const path = route.pathname 
  const params = qs.parse(route.query)

  res.writeHead(200, {'Content-Type': 'text/plain'})

  if (path === '/hello' && 'name' in params) {
    res.write('Hello ' + params['name'])
  } else {
    res.write('Hello anonymous')
  }
  
  res.end()
}
```

Access to your local website by different URLs like `localhost:8080/hello?name=John`.

### Organize the source code in a module

Create `handles.js` and `index.js` files and reorganize the previous code like:

```js
// ./handles.js
// Necessary imports
module.exports = {
  serverHandle: function (req, res) {
    // ...
  } 
}
```

```js
// ./index.js
const http = require('http')
const handles = require('./handles')

http
.createServer(handles.serverHandle)
.listen(8080)
```

## Integrate Nodemon

Tired of restarting your webserver after every modification of the source code? Let's fix it!

Nodemon is a simple utility that watches your development files and restarts the server automatically upon saving, eliminating the need to restart the server manually.

### Install Nodemon

Run:

```bash
npm install nodemon
# or
yarn add nodemon
# then
npx nodemon index.js
# npx avoids running `./node_modules/.bin/nodemon index.js`
```

Now, it will restart the web server when the file is updated. There is no need to restart it manually to apply modifications of code. Just refresh the page in a browser.

> Note! Don't forget to define a `.gitignore` to prevent committing the `node_modules` folder.

### Define an NPM script in `package.json`

Enrich your `scripts` in `package.json` with:

```json
"scripts": {
  ...
  "dev": "nodemon index.js"
  ...
}
```

And then always run when developing:

```bash
npm run dev
```

## Create a basic application with multiple routes

Create an application with 3 routes:

1. `/` explains how `/hello` works (containing the links)
2. `/hello` takes a `name` query parameter and:
    - random names reply `hello [name]`
    - your own name replies with a short intro of yourself
3. Any other path replies a 404 code with a not found message

## Reading from a JSON file

1. Create a subfolder with the name `content` and create a JSON file `about.json` inside it with the example content like this:

    ```json
    {
      "title": "About",
      "content": "Example content here.",
      "author": "Your Name",
      "date": "27/09/2022"
    }
    ```

1. Create the route `/about` displaying the content of this JSON file:

    - use `require()` method to access a file
    - chose a proper `Content-Type` for displaying JSON

1. Create dynamic routing.

Parse the path and verify if a JSON file exists in the `content` folder. If yes, print its content. If no, redirect to the 404 error page.

## Publish your project to GitHub

### Document your project

Update the `README.md` file. It should at least contain:

- Project title
- Short introduction
- Prerequisites
- Installation instructions
- Usage instruction with simple (and advanced) examples
- List of contributors

### Push it to GitHub

Commit your changes, use your **PRIVATE** group repository on GitHub, and push it.
Create a tag `lab1` for the last commit and also push it.

## Cultivate yourself

- [Learn Markdown](https://www.markdownguide.org/)
- [How to write README](https://dev.to/scottydocs/how-to-write-a-kickass-readme-5af9)
