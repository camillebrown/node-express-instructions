# Layouts and Controllers

#### 1. Create a new project

#### 2. Initialize Node

#### 3. Install Dependencies

* express
* ejs

#### 4. Set up Express

* `index.js` file
* require express
* create an instance of express
* tell the app which port to listen to

#### 5. Set up EJS

* set view engine to ejs
* create a `views` folder

## EJS Layouts

Adding partials can dry up the code a bit, but [EJS Layouts](https://www.npmjs.com/package/express-ejs-layouts) can take this modularity even farther and make a big diffence with large applications.

EJS layouts is a node package that allows us to create a boilerplate that we can inject content into based on which route is reached. Layouts normally include header and footer content that you want to display on every page \(navbar, sitemap, logo, etc.\).

### Install EJS Layouts

#### Step 1: Install EJS layouts

Install `express-ejs-layouts` via npm

npm i express-ejs-layouts

#### Step 2: Set up EJS layouts

Require the module and add it to the app.

_**index.js**_

```javascript
var express = require('express');
var app = express();
var ejsLayouts = require('express-ejs-layouts');

app.set('view engine', 'ejs');
app.use(ejsLayouts);

app.listen(3000)
```

#### Step 3: Create a Layout

In the root of the `views` folder, add a layout called `layout.ejs`. It _must_ be called `layout.ejs`, as mandated by `express-ejs-layouts`.

**layout.ejs**

```markup
<!DOCTYPE html>
<html>
<head>
  <title>Love It or Leave It</title>
</head>
<body>
  <%- body %>
</body>
</html>
```

This layout will be used by all pages, and the content will be filled in where the `<%- body %>` tag is placed. `<%- body %>` is a special tag used by `express-ejs-layouts` that cannot be renamed.

#### Step 4: Use the Layout

In the views folder, create a `index.ejs` file:

_**index.ejs**_

```markup
<h1>This is the home page!</h1>
```

Now create a index route in `index.js` below the middleware:

```javascript
app.get('/', (req, res) => {
  res.render('index.ejs');
});
```