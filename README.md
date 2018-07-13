# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?

Node.js is asynchronous by default.

1.  Why do you commonly see files named `index.js` in Node?

'index.js' is commonly seen in Node because when you run the server any file with that title will be assumed the file to run.

1.  What is `module.exports`?

'module.exports' is included at the end of a file mainly to export routes to your main index.js file.

1.  What does the `require` function do?

'require' is used to import various modules and middleware into files.

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

This is refering to the id entered into the route path manually.

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?

{
"name": "elie",
"job": "instructor"
}

1.  What is middleware? Give an example of some middleware you've used.

Middleware is software that works between the application and the machine for some purpose. Some examples include, morgan and body-parser.

1.  What does the `next` keyword do?

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

function checkCorrectIdLength(req, res, next) {
try {
if (lengthOf(req.body.id) > 1 && lengthOf(req.body.id) < 100) {
return next();
} else {
} catch (err) {
return next(new APIError(400, { "message": "Invalid" } )
}
}

### SQL

1.  What is a Primary Key?

A Primary key is a unique identifier.

2.  What is a Foreign Key?

A Foreign key references a key from a foreign table in a one to many or many to many relationship between tables in a database.

3.  When establishing a many to many relationship you always need a join table. Why?

You always need a join table in a many to many relationship because without it there could only be a one to many
relationship.

4.  What columns does a join table commonly contain?

The primary key from one table and the primary key from a different table.
