# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?

Node is single-threaded by design, and so handles concurrency using asynchronous code. Async code is therefore essential to the way Node operates.

1.  Why do you commonly see files named `index.js` in Node?

If a file is named `index.js`, it can be required indirectly by requiring the folder instead of the specific file. Additionally, `index.js` files are commonly used to group all of the modules inside a folder so that only one require statement is needed to access all of the files.

1.  What is `module.exports`?

`module.exports` is the way Node files can export code to be used in other files.

1.  What does the `require` function do?

THe `require` function imports the code that is exported from a file using `module.exports`. This allows the imported code to be used in the file which required it.

### Express.js

1.  Given the following code, what does `req.params.id` refer to?

```js
app.get('/users/:id', (req, res, next) => {
  return res.json({
    username: 'bob',
    id: req.params.id
  });
});
```

`req.params.id` refers to the `:id` in the route. When a route is accessed that matches this pattern Express will assign that value to `req.params.id`.

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?

`req.query` will be an object with the query parameters as key:value pairs. `{name: elie, job: instructor}`

1.  What is middleware? Give an example of some middleware you've used.

Middleware is any code that sits between the normal express request and response cycle. Examples of middleware include the body-parser and morgan packages.

1.  What does the `next` keyword do?

In Express, `next()` will call the next function in the middleware stack that matches the current route.

Given the following code:

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
function idCheck(req, res, next) {
  if (req.params.id >= 1 && req.params.id <= 100) {
    next();
  } else {
    res.status = 400;
    return res.json({ message: 'Invalid' });
  }
}
```

### SQL

1.  What is a Primary Key?

A Primary Key is a unique and non-null column in a table that is used to identify records.

2.  What is a Foreign Key?

A Foreign Key is a reference to a record in a different table. It is typically the primary key of the foreign table, but doesn't have to be.

3.  When establishing a many to many relationship you always need a join table. Why?

Since a record on either side of the many-to-many relationship can have multiple associations to records on the other side, a join table is needed to maintian the relationship without using a collection (like an array) in the tables.

4.  What columns does a join table commonly contain?

A join table commonly contains foreign key references to the primary keys in each of the tables being joined.
