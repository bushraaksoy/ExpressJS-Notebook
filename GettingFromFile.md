# Getting our page from a file

```js
cosnt express = require('express')
const app = express()
```

To get a certain html file to get sent, you can use the path module and also sendFile instead of send.

first we import path
```js
const path = require('path')
```
then we implement our get

```js
app.get('/', (req, res) => {
  res.sendFile(path.resolve(__dirname, filepath))
})
```

### if we use this method, the stylesheet used in our document will not be used and we will not be seeing any styling or even js.
to solve this problem, we use:

## app.use(express.static('./public'))

here it can be any filename, but using public makes more sense.
express can then access every folder thats inside it. So if the browser needs the style.css file, it will look in the public folder and find it there.

```js
app.use(express.static('./public'))

app.get('/', (req, res) => {
    res.sendFile(path.resolve(__dirname, './index.html'));
})
```
In the code above app.use() is for setting up the middleware. express.static() is basically a built in middleware.

now we actually won't even need these lines of code:
```js
app.get('/', (req, res) => {
    res.sendFile(path.resolve(__dirname, './index.html'));
})
```
since express can just find everything in the static public page.

## Getting json data from file and displaying it on our page

lets say we have a data.js file with an array of objects of products.
```js
const products = [
  {
    "id": 1,
    "name": "shirt"
  },
  {
    "id": 2,
    "name": pants
  }
]
```

now we can get the data from the data.js file and display it the way we want based on the url.

```js
const data = require('./data')

app.get('/api/products', (req, res) => {
  res.json(products)
})
```

we can also get a specific product with it's id like this:

```js
app.get('/api/products/:productId', (req, res) => {
  const {productId} = req.params
  const singleProduct = products.find(product => {
    product.id === Number(productId)
  })
  res.json(singleProduct)
})
```
Here we are specifying a parameter by adding the :, so the word after the colon is consdered to be the parameter.
And were able to access the parameters from the requests using req.params.
