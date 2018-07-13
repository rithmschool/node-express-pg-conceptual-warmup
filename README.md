# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?

    Because Node is built asynchronously, asynchronous operations lets Node do more without blocking the server from executing other operations, and bugs can seem weird if you don't understand that code are not executed in the order that you would expect.

1.  Why do you commonly see files named `index.js` in Node?

    It is a convention for the starting point of the app, where Node should start the app on.

1.  What is `module.exports`?

    Is an object that contains all the variables and functions that will get exported from the file and is available for import through the require function

1.  What does the `require` function do?

    Import functions and objects from files or packages exported through modules.exports

### Express.js

1.  Given the following code, what does `req.params.id` refer to?

    Refers to whatever is passed in after /users/ in the route

```js
app.get('/users/:id', (req, res, next) => {
  return res.json({
    username: 'bob',
    id: req.params.id
  });
});
```

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?

    ```js
    {
      name: elie,
      job: instructor
    }
    ```

1.  What is middleware? Give an example of some middleware you've used.

    A middleware is a callback function that gets executed in the middle of a route. An example would be a user authentication middleware or an error handler.

1.  What does the `next` keyword do?

    Goes to the next function on the stack or the error handler depending on if there is an error passed in or not.

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
function validId(req,res,next) => {
  try {
    if(req.params.id > 100 || req.params.id < 1) {
      const invalidId = new Error('Invalid')
      invalidId.status = 400
      throw invalidId
    } else {
      return next()
    }
  } catch (e) {
    next(e)
  }
}
```

### SQL

1.  What is a Primary Key?

    A primary key is the unique identifier for a row in a table. They are typically serial integers

2.  What is a Foreign Key?

    A foreign key is a reference to a unique column in another table, usually references the primary key of the table it is referencing.

3.  When establishing a many to many relationship you always need a join table. Why?

    The join table matches the two table based on common primary keys and lets us store information about the relationships without having to put that information in either the tables that are being joined.

4.  What columns does a join table commonly contain?

    Primary key and foreign keys
