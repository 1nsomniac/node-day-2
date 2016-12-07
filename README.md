# node-day-2
Notes and code from Day 2 lecture - DM16

### common data structures
- array of objects
```
var books = [{
  name: ‘Harry Potter’,
  author: ‘JK Rowling’
}, {
  name: ‘LOTR’,
  author: ‘JRR Tolkein’
}, {
  name: ‘GOT’,
  author: ‘George RR Martin’
}];
```

- other examples: movies, schools, users

### CRUD (create, read, update, delete) / module.exports

# module.exports (remember the ’s’)
```
// 1. module.exports at the top and have function declarations
module.exports = {
  getBooks: getBooks,
  updateBooks: updateBooks,
  deleteBook: deleteBook
}

// 2. module.exports and write in the object itself
module.exports = {
  create: function (req, res, next) {
  
  },
  read: function (req, res, next) {
  
  },
  update: function (req, res, next) {
  
  },
  destroy: function (req, res, next) {
  
  },
  index: function (req, res, next) {
  
  }
}

// 3. module.exports at the bottom and use function declarations OR expressions

// 4. module.exports.functionName after every function
```

### req.params (path params)
- just like Angular
- ‘/books/:id’ where :id is your req.params.id

### req.query (URL query)
- anything after the ‘?’ in the url
- key=value format. spaces get a ‘+’
- different queries are separated with ‘&’
- ‘/books?id=0&name=harry+potter’

req.query = {
  id: 0,
  name: ‘harry potter’
}

tip: if you’re not sure, console.log()

### Multiple files

- similar to Angular where you divide up code by functionality
- use module.exports to export out code from a file
- use var whateverName = require(‘/path/to/file/with/code/we/want’)

### Naming Conventions
- just be consistent and descriptive

### Chaining Functions and next()
- express does things in order
- you need to call next() to get to the next function in the chain

### Middleware
- if you use `app.use` then this will run for every single request
- if you want to only use it for some some requests, then make a function, and then add it to specific endpoints

```
app.use(iAmUsedForEveryRequest());

function onlyUsedWhenIWantMiddleware (req, res, next) {
  // do stuff
  next()
  // if you don’t call next it won’t continue
}

app.get(‘/books’, onlyUsedWhenIWantMiddleware, function(req, res, next) {
  // stuff
});
```
