# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?

- Because in development with Node.js, most of the functions you write will need to be asynchronous to create a non-blocking application.

1.  Why do you commonly see files named `index.js` in Node?

- Because it is a convention, and a lot of app are default at taking index.js as the default root file to run.

1.  What is `module.exports`?

- Exporting variables that you want other files/application to use by importing/requiring the exporting file.

1.  What does the `require` function do?

- Importing variables from the file you are requiring that would have "module.exports' at the end of the file to export the variables.

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

- 'id' in the route path.

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?

- {name: 'elie', job : 'instructor'}

1.  What is middleware? Give an example of some middleware you've used.

- middilewares are functions that intercept your function, process it, and pass it on to the next middleware or function. Some common middlewares I have used are morgan, body-parser and such.

1.  What does the `next` keyword do?

- continue to the next middleware/function, sometimes with varibales.

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

- function middleware(req, res, next){
  if(req.params.id >= 1 && req.params.id <= 100)
  {
  return next();
  }
  else
  {
  return res.status(400).send({message: 'Invalid'})
  }
  }

To use this middleware function:

app.get('/users/:id', middleware, (req, res, next) => {
return res.json({
username: 'bob',
id: req.params.id
});
});

### SQL

1.  What is a Primary Key?

- Primary key is an attribute column of the sql table that it can be used to identified a particular row of the table. The values of primary keys are unique.

2.  What is a Foreign Key?

- Foreign Key is an attribute column of the sql table that it can be used by other tables to reference the columns of their tables.

3.  When establishing a many to many relationship you always need a join table. Why?

- A join table is essential in a many to many relationship because it can be used to reference and specify the dependencies of the tables of both sides of the many to many relationship.

4.  What columns does a join table commonly contain?

- Most of the time, one column that references, often the primary key column of one table in the many to many relationshp, and one column that references, also often the primary key column of the other table in the many to many relationship. Sometimes it would havve its own unique primary key column.
