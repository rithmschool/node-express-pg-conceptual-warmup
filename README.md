# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?
1.  What is the purpose of `index.js` files?
1.  How do Common.js modules work? What is a module in Common.js?

### Express.js

1.  Given the following code, what does `req.params.id` refer to?

```js
app.get("/users/:id", (req, res, next) => {
  return res.json({
    username: "bob",
    id: req.params.id
  });
});
```

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?
1.  What is middleware? Give an example of some middleware you've used.
1.  What does the `next` keyword do?

Given the following code:

```js
app.get("/users/:id", (req, res, next) => {
  return res.json({
    username: "bob",
    id: req.params.id
  });
});
```

Write a middleware function that checks to see if the id is between 1 and 100. If it is, move onto the next piece of middleware or function. If it is not, respond with a status code of `400` and an object with the key of `message` and value `Invalid`.

### SQL

1.  What is a Primary Key?
2.  What is a Foreign Key?
3.  When establishing a many to many relationship you always need a join table. Why?
4.  What columns does a join table commonly contain?
