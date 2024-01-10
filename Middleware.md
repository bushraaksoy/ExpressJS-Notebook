# Middleware

Middleware are an essential part of express, they go between the request and response, so:
 ### request -> middleware -> response

Middleware are basically some functions that we specify and pass on to our methods such as get or post, in order to execute a functionality such as authorization ect.
They are functions that have access to the request object (req), the response object (res), and the next function in the application’s request-response cycle. The next function is a function in the Express router which, when invoked, executes the middleware succeeding the current middleware.

Middleware functions can perform the following tasks:

* Execute any code.
* Make changes to the request and the response objects.
* End the request-response cycle.
* Call the next middleware in the stack.

for example if we want a middleware for console.logging the req method and path everytime we make a request, we can create a middleware to do that:

```js
const logger = (req, res, next) => {
  const method = req.method;
  const path = req.path;

  console.log(method, path)
  next()
}

module.exports = logger
```

We can create this function in a different logger.js folder and then import it to app.js and use like this:

```js
const logger = require('logger')
// then we pass the middleware as a parameter to the method.

app.get('api/products', logger, (req, res) => {
 res.json(products)
})
```
So now everytime we call the above methods to the specified url, the logger will be called.

if we want to implement this middleware function to all the other methods too, we can do this:

## app.use()
```js
app.use(logger)
```
app.use() essentially mounds our app with the middleware specified
using the app.use() function will apply this middleware to all the next methods specified, wihtout having to individually add it to each one.
and if you want to specify multiple middlewares in the app.use(), you can mention all of them in one array.
