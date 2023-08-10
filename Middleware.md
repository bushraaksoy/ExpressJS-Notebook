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
  const path = rew.path;

  console.log(method, path)
  next()
}
```
