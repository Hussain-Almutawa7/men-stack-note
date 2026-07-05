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
- Initialize a node project with `npm init -y`
- Install express `npm i express`

### Write Server Boilerplate

server.js
```js
const express = require("express");
const app = express();

app.listen(3000, () => {
    console.log("Listening on port 3000");
});
```

Run the server with `nodemon server.js`

Navigate to `localhost:3000` to view the server.

Use `ctrl + c` to stop the server in the terminal.
