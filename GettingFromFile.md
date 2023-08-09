# Getting our page from a file

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
