# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?

- It is important because asynchronous code allows us to make javascript appear multithreaded while only being a single threaded language. Asynchronous code is non-blocking and allows our code to keep running while making other queries.

1.  Why do you commonly see files named `index.js` in Node?

- since node will look inside a folder for an index.js file to run, we usually name the application we want to run index.js

1.  What is `module.exports`?

- module.exports is usually placed at a bottom of a file to export that whole code as an object? I know it export the whole code to allow other code files to be able to run it.

1.  What does the `require` function do?

- the require function is similar to the imports function of flask. It brings in whatever code you exported and allows you to use that code from another file there.

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

- req.params.id in the code above is the request sent from the URL in the params called id

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?

- {
  name: 'elie',
  job: 'instructor'
  }

1.  What is middleware? Give an example of some middleware you've used.

- middleware is what sits in the middle of your request and response and it will run and if depending on how it is written wil l either send you to the next middleware/code or send you to the error handler. example is we wrote our own middleware to handle authorizations for logins.

1.  What does the `next` keyword do?

- next() with nothing passed in will send your code to the next middleware or the next line of code. next('anything') will send whatever is passed in as an error and will send your code to the error handler

Given the following code:

```js
app.get('/users/:id', (req, res, next) => {
  return res.json({
    username: 'bob',
    id: req.params.id
  });
});
```

```js
async function checksRange(req, res, next) => {
  try {
    if (req.params.id > 1 && req.params.id < 100) {
      return next();
    }
  } catch (err) {
    return next({
      status: 400,
      message: "message",
      value: "Invalid"
    })
  }
}
```

Write a middleware function that checks to see if the id is between 1 and 100. If it is, move onto the next piece of middleware or function. If it is not, respond with a status code of `400` and an object with the key of `message` and value `Invalid`.

### SQL

1.  What is a Primary Key?

- primary key is unique and is is a key to identify a row of information in a table

2.  What is a Foreign Key?

- Foreign key is a way to identify and access another row of information from a different table
- usually established with another tables primary key

3.  When establishing a many to many relationship you always need a join table. Why?

- you will need a join table because the two tables will not have references or a way to identify one another.
- the join table acts as a middleman because it will have the association that links the unique identifier of each table.

4.  What columns does a join table commonly contain?

- id, primary key of table1, primary key of table2
