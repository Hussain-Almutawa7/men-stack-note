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
