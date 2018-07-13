# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?
    Because with node we can run asyncronous code without blocking the rest of the program(it doesn't have to stop to complete the asyncronous part of the program). We can use async functionds and promises fr this, and node uses the event loop to manage the asyncronous part of the program.
1.  Why do you commonly see files named `index.js` in Node? If I need to reference a index.js that is inside of a folder, I can use the path to the parent folder, and node will assume I'm referencing the index.js of that folder.
1.  What is `module.exports`? it is how we send a function, or object from one file to another.
1.  What does the `require` function do? it is a module that allows to use other modules that has been installed or other files.

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

the req.params.id refers to the parameters of the Url(comes from the path of the URL), in this case the id of specific username.

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?
    {
    name: "Elie",
    job:"instructor"
    }
1.  What is middleware? Give an example of some middleware you've used.
    Middleware are function that intercept the request and performs a task, and send a reaponse to the next part of the program.
    Ex:jsonwebtoken, or my own middleware created to check if a user is loogedIn
1.  What does the `next` keyword do? in invokes the next function of the program.

Given the following code:

```js
app.get('/users/:id', checkIdOnRange, (req, res, next) => {
  return res.json({
    username: 'bob',
    id: req.params.id
  });
});
```

```
function checkIdOnRange(id){
if(+id >=1 && +id <= 100){
  return next()
}else{
   res.status(400).json({ message: "Invalid" });
}
}
```

Write a middleware function that checks to see if the id is between 1 and 100. If it is, move onto the next piece of middleware or function. If it is not, respond with a status code of `400` and an object with the key of `message` and value `Invalid`.

### SQL

1.  What is a Primary Key?
    Is a unique value that identifies each row in a table
2.  What is a Foreign Key?
    A key that references generally a primary key of another table.
3.  When establishing a many to many relationship you always need a join table. Why?
    The join table allows to have acces to the different tables involve in the many to many at the same time.
4.  What columns does a join table commonly contain?
    Two columns that reference the primary key(can also reference a different colum) of the tables involve in the many to many relationship.
