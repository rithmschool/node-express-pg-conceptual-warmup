# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?
    Node is asyncrhonous by default. //

2.  Why do you commonly see files named `index.js` in Node?
    If, in requiring a file, you provide the path to a directory that contains an index.js file, and you don't specify the file, Node will find and use that index.js file by default. This also applies to starting the Node (or nodemon) server -- if you just type 'node' or 'nodemon' in terminal, it will run an index.js if present without having to specify.
3.  What is `module.exports`?
    In Node, when a file is required and assigned to a variable, the `module.exports` line in the required file determines what is actually imported/required (and assigned to that variable).

4.  What does the `require` function do?
    It assigns the module.exports content of another file to a variablr. So in `const userRoutes = require('./routes/userRoutes.js')`, a variable userRoutes will now point to the `module.exports` line of `userRoutes.js`.

### Express.js

1.  Given the following code, what does `req.params.id` refer to?
    `req.params` refers to any wildcards in the route. `req.params.id` refers to the part of the route represented by `:id`, which is not literally `:id` but stands for whatever follows `/users/` in the route.

```js
app.get('/users/:id', (req, res, next) => {
  return res.json({
    username: 'bob',
    id: req.params.id
  });
});
```

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?
    { name: `elie`, job: `instructor`}

2.  What is middleware? Give an example of some middleware you've used.
    Middleware is a function that runs before a given route, an is often broken out into separate file to avoid repetition, and keep a given .js file easier to follow and read. It can be written as part of a project, but it can also be installed from an external source (via npm) and used by others. We've written our own middleware, like in auth.js for the LinkedList project, but we've also imported several in each Node project. body-parser is one such example, and runs as middleware on every request regardless of route, taking the req and providing a legible req.body object.

3.  What does the `next` keyword do?
    Exits the current route and runs the next matching route (given its path and verb). If something is passed to next (`return next(err)` rather than `return next()`), whatever is passed to `next()` is passed as an error to the first error handling route (a route which takes (err, req, res, next) rather than just (req, res, next)). So the keyword determines what gets passed as an error, and whether an error gets passed.

4.  Given the following code:

```js
app.get('/users/:id', (req, res, next) => {
  return res.json({
    username: 'bob',
    id: req.params.id
  });
});
```

Write a middleware function that checks to see if the id is between 1 and 100. If it is, move onto the next piece of middleware or function. If it is not, respond with a status code of `400` and an object with the key of `message` and value `Invalid`.

```js
app.use('', (req, res, next) => {
  let id = +req.params.id;
  if (id <= 100 && if >= 1) {
    return next());
  }
  return res.status(400).json({message: `Invalid`})
})
```

### SQL

1.  What is a Primary Key?
    For each row in a table, the Primary Key is the data which serves as a unique identifier for that row.
2.  What is a Foreign Key?
    A foreign key is the primary key of another table, used to establish relationships between data in different tables. For example, if you have a `users` table (and each user has an id # as a primary key), and you have a `companies` table (and each company also has an id # as a primary key), the `users` table could also have a foreign key table that had data corresponding to the `companies` table. You could ask SQL what the `company_id` of the user with `id` 1 is, and if their `company_id` value was, say, 4, then you could look up the company with `id` 4 in the `companies` table. In this example, `company_id` is the foreign key.

3.  When establishing a many to many relationship you always need a join table. Why?
    The join table allows you to link one row from table A to several rows from table B, and one row form table B to several rows from table A, whereas the foreign key example above is only one way (one company, many users).

4.  What columns does a join table commonly contain?
    A foreign key pointing to the primary key of company A, a foreign key pointing to the primary key of company B, and its own primary ID column. The primary ID column lets you reference individual relationships in the join table.
