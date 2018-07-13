# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?
    The entire Node.js framework runs asynchronously, which means code is executed in a non-blocking manner and functions will execute differently than vanilla js or other synchronous frameworks.
1.  Why do you commonly see files named `index.js` in Node?
    Node will automatically run a file named index.js if none other is specified
1.  What is `module.exports`?
    It's a way to send out code from a specific file to be used in other files.
1.  What does the `require` function do?
    Imports code from frameworks/libraries or other files

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

      It refers to the ':id' part (parameter) of the path, so if the path was '/users/4' the req.params.id would be 4 (as a string)

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?
    {name: elie, job: instructor}
1.  What is middleware? Give an example of some middleware you've used.
    Middleware is code that runs in between the server request and the server response. It can be an imported library such as morgan or a custom built file with middleware functions that can help do things like authenticate.
1.  What does the `next` keyword do?
    Moves onto the next function. If something is passed as a parameter to it such as next(err), it will move on to the next error handler expecting four parameters (error, req, res, next);

Given the following code:

```js
app.get('/users/:id', (req, res, next) => {
  return res.json({
    username: 'bob',
    id: req.params.id
  });
});
```

function checkNum(req, res, next) => {
try {
if(+req.params.id < 100 && req.params.id > 1) return next();
} catch(err) {
console.log(err);
return res.status(400).json({ message: 'Invalid' })
}
}

Write a middleware function that checks to see if the id is between 1 and 100. If it is, move onto the next piece of middleware or function. If it is not, respond with a status code of `400` and an object with the key of `message` and value `Invalid`.

### SQL

1.  What is a Primary Key?
    The main reference for a line of data in the table. Needs to be unique, never null, and should be immutable. It is usually an integer
2.  What is a Foreign Key?
    A reference to another table's primary key
3.  When establishing a many to many relationship you always need a join table. Why?
    You can establish a one:many relationship without a join table by adding a foreign key, but that only allows for a one way relationship. In a m:m both tables need access to each other's data, and a join table establishes the path for that.
4.  What columns does a join table commonly contain?
    The primary ids of the two tables being joined, e.g, "users_id" and "jobs_id"
