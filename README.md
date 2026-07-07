# MEN STACK NOTES

| CRUD Action | RESTful Action | HTTP Method | Definition |
| ----------- | -------------- | ----------- | ------------------------ |
| Create | `new` | `GET` | Show a form to create a new item |
| Create | `create` | `POST` | Add a new item to the database |
| Read | `index` | `GET` | Show all items |
| Read | `show` | `GET` | Show one specific item |
| Update | `edit` | `GET` | Show a form to edit an existing item |
| Update | `update` | `PUT` | Save changes to an existing item |
| Delete | `delete` | `DELETE` | Remove an item from the database |

## SETUP
- Create a directory
- Create server file `touch server.js`
- Create a `.gitignore` file
- Initialize a node project with `npm init -y`
- Install express and morgan `npm i express morgan`

### Add `node_modules` to `.gitignore`

.gitignore
```bash
node_modules
```

### Write Server Boilerplate

server.js
```js
const express = require("express");
const morgan = require("morgan");

const app = express();

app.use(morgan("dev"));

app.listen(3000, () => {
    console.log("Listening on port 3000");
});
```

Run the server with `nodemon server.js`

Navigate to `localhost:3000` to view the server.

Use `ctrl + c` to stop the server in the terminal.

### Creating a Test Route
```js
app.get("/test", (req, res) => {
    res.send("<h1>This is a test route</h1>");
});
```
Navigate to `localhost:3000/test`

### Using request paramaters

```js
app.get("/greet/:name", (req, res) => {
    res.send(`Hello, <strong>${req.params.name.toUpperCase()}</strong>`);
});
```
Navigate to `localhost:3000/greet/yourname`

<img width="437" height="107" alt="image" src="https://github.com/user-attachments/assets/3e3d803c-8f4b-462b-aaea-6224127e8280" />

## Rendering EJS

- Install ejs with `npm i ejs`
- Create a `views` directory
- Create an `.ejs` file like `home.ejs` inside it
- Add html biolerplate with `!`

home.ejs

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Home</title>
    </head>
    <body>
        <h1>We are rendering and EJS page 🚀</h1>
    </body>
</html>
```

- Render `ejs` page using a controller like this one:

```js
app.get('/', (req, res) => {
  res.render("home.ejs")
});
```
<img width="706" height="177" alt="image" src="https://github.com/user-attachments/assets/1a324161-8b7b-4ea8-bfe7-ea20ce71f1d2" />

### EJS Syntax

To use JS in an ejs file, I need a scriplet tage: 
```ejs
<% let user = "Husain"%>
```

To display javaScript values from an ejs file, I need an output tag:
```ejs
<%= user %>
```

### Pass data from the controller

Use the locals object insdie the render method:
```js
res.render("home.ejs", {
    title: "Home Page"
});
```

Now I can use the `title` varibale in my `home.ejs` file.

home.ejs
```ejs
<h1><%= title %></h1>
```

### Using `forEach` in `ejs`
```ejs
  <ul>
    <% inventory.forEach(item => { %>
    <li><%= item.name %> : <%= item.qty %></li>
    <% }) %>
  </ul>
```

### Creating dynamic links to `show` page

`item.name` is dynamically showing up. The link is also dynamically changing with the item. (see `forEach` above)
```ejs
<a href="/<%= item.id %>"> <%= item.name %> </a>
```
We should see the URL change in the browser.
