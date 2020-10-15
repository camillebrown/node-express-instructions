# Templates

### EJS: Embedded Javascript

There are several javascript template engines for express, one of the most popular of which, is [EJS](https://ejs.co/), available via npm. 

#### Install EJS

npm i ejs

#### Set the view engine to EJS

Above your routes, add 
`app.set(name, value)` 
```javascript
app.set('view engine', 'ejs');
```
This tells express that we'll be using ejs as our view engine.

#### Adapt your routes to ejs

_**1.**_ Rename the .html files to .ejs files.

_**2.**_ Assign statements with `res.render(<file name>)` insde the app.get().

_**3.**_ Create a Views Folder in the parent directory of your project and add an index.ejs file within the folder

_**3.**_ Then render the index.ejs file within your index.js file

```javascript
app.get('/', (req, res)=>{
  res.render('index.ejs'); 
});
```

#### The Cool Part: Templating with Variables

_Templating with variables_ means we can pass in an object to `res.render()` and access the values stored in it as variables inside the ejs template.

**index.js**

```javascript
app.get('/', function(req, res) {
  res.render('index', {name: "Sterling Archer", age: 35});
});
```

We now have access to a _name_ variable inside our `index.ejs` file! We can access this variable by embedding it into the html using this notation: `<%= embedded js goes here %>`.


### Partials

Partials can be used to modularize views and reduce repetition. A common pattern is to move the header and footer of a page into separate views, or partials, then render them on each page.

#### Create the partials

In the main directory of your project, create a `partials` folder that includes a `header.ejs` file.

**partials/header.ejs**

```markup
  <header>
    <img src="http://placekitten.com/500/500">
  </header>
```

#### Include your partial

**index.ejs**

```markup
<!DOCTYPE html>
<html>
  <head>
    <title>Home Page</title>
  </head>
  <body>

    <%- include('../partials/header.ejs') %>

    <h1>Hello, <%= name %>!</h1>
.
.
.
```
