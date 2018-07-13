# Node Conceptual Warmup

## Instructions

- Fork and clone this repository
- Place your answers inside of this file (you can keep these answers to a sentence or two)
- Submit a pull request to submit the assignment

## Questions

### Node.js

1.  Why is it important to understand asynchronous code to be a good Node.js developer?

A: Asynchronous code is important to being a good Node developer because the majority of functions written in the express framework are asynchronous, as they are making requests to a database or API and are promise-based. 

1.  Why do you commonly see files named `index.js` in Node?

A: files are often named index.js because you do not need to include index.js in the path to the file if you name it index.js.  this makes things a little bit faster to write out.  It's also just convention.  

1.  What is `module.exports`?

A: module.exports is a key in the module object with a value of whatever you wish to export from a  given file.  

1.  What does the `require` function do?

A: the require function imports a module into a given file

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
req.params.id refers to the dynamic id included in the users path

1.  Given the following request `http://localhost:3000/1?name=elie&job=instructor` - what will the `req.query` object look like on the server?

```js
req.query = {
				name: "elie",
				job: "instructor"
			}
```

1.  What is middleware? Give an example of some middleware you've used.


Middleware is a function that is used between the request and the response.  The user authentication functions we wrote to authenticate tokens is an example of middleware.  

1.  What does the `next` keyword do?

The next keyword returns you to the next block of code if nothing is passed into next(), or if something is passed into next, it returns an error.  

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

```js
function validateId(req, res, next) {
	try{
		const id = req.params.id;
		if(id >= 1 && id <= 100) {
			return next();
		} 
	} catch(err) {
		err.status = 400
		err.message = 'Invalid';
		return next(err);
	}
}
```


### SQL

1.  What is a Primary Key?

A: A primary key is a unique identifier for a row in a table.  It should never be changed, and it should never be reused even if a row is deleted from the table.  

2.  What is a Foreign Key?

A: A foreign key is a key that references a column in a separate table in the database.  

3.  When establishing a many to many relationship you always need a join table. Why?

A: A join table is needed to establish a many to many relationship because there can associations from a row in 'table one' to many rows in 'table two', as well as associations between one row in 'table two' with many rows in 'table one'.

4.  What columns does a join table commonly contain?

A: A join table usually has a column with an id (primary key) and columns that reference the id primary keys of at lease two other tables.  
