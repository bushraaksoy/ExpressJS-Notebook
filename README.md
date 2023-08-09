# ExpressJS-Notebook
My digital rough notebook for ExpressJS


creating of the express app and invoking it:
```js
const express = require('express')
const app = express();
```

Here app has a few functions: 
* app.get(path, callback): Handles HTTP GET requests.
* app.post(path, callback): Handles HTTP POST requests.
* app.put(path, callback): Handles HTTP PUT requests.
* app.delete(path, callback): Handles HTTP DELETE requests.
* app.all(path, callback): Handles all HTTP methods (GET, POST, PUT, DELETE, etc.) for a specific path.

## example

```js
app.get('/', (req, res) => {
  res.send('Welcome to the home page')
})
```

here the reasponse will diaplay 'Welcome to the home page', if our path is '/'

to specify the status of the response, you can add res.status().send()

```js
app.get('/', (req, res) => {
  res.status(200).send('Welcome to the home page')
})
```

In the code above app.use() is for setting up the middleware. (express.static() is basically a built in middleware.
