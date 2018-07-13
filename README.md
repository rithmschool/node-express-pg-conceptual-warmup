# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?
    - it's bacause everything in Node.js development is runinng asychronously, it means the website doesnt have to wait for one feature to complete in order to load other features. It can run everthing at the same time, and which can makes the website load faster.
1.  Why do you commonly see files named `index.js` in Node?
    - it's bacause `index.js` and `app.js` are reserved names in Node. If you are trying to require a path without a specific file name then the system will look for those file with the reserved name.
1.  What is `module.exports`?
    - `module.exports` is way to export a specific function or object for other file to use. Without that other files cannnot access other file's functions.
1.  What does the `require` function do?
    - If you want to use a specific file or module, then you have to tell the file to require that. By doing so, you have to use the `require` function to do that.

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

- it refers to the user id, which is the `id` in the end of the url in this case.

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?

```js
{
  "name" : "elie",
  "job" : "instructor"
}
```

1.  What is middleware? Give an example of some middleware you've used.
    - a middleware is something that run in between the request and response. For example, if a user sumbit a form with the data. We can have a middleware to check for the data. If there's a error in the data then server can send the error to the user instead of the real reponse.
1.  What does the `next` keyword do?
    - the `next` keyword is to tell the server to run the next route or middleware that has the same relative path.

Given the following code:

```js
app.get('/users/:id', (req, res, next) => {
  if (req.params.id > 1 || req.params.id < 100) {
    const err = new Error('Invalid');
    err.status = 400;
    next(err);
  }
  return res.json({
    username: 'bob',
    id: req.params.id
  });
});

app.use((err, req, res, next) => {
  res.status(err.status || 500);
  return res.json({
    message: err.message,
    error: err
  });
});
```

Write a middleware function that checks to see if the id is between 1 and 100. If it is, move onto the next piece of middleware or function. If it is not, respond with a status code of `400` and an object with the key of `message` and value `Invalid`.

### SQL

1.  What is a Primary Key?
    - a Primary key is a key that cannot be change and it can increment by itself.
2.  What is a Foreign Key?
    - a Foreign Key is key that make a connection between tables
3.  When establishing a many to many relationship you always need a join table. Why?
    - it's because tables may not have the relationship between each other. You cannot access other table by just knowing one table. With the join table, You need combine the tables in to one then you can access other table's info.
4.  What columns does a join table commonly contain?
    - a join table commonly contain ids of the table.
