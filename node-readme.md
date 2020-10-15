# Intro to Node

## Installing Node

`npm i -g nodemon`

## Initializing a Node Project

#### 1. Create a new folder for your node project.

`mkdir my-first-proj`

CD into the project folder

#### 2. Initialize Node inside the project folder.

```text
npm init
```

You will be prompted to enter values for a number of fields to set up the node project. Press enter to accept the default value on each field

To skip this step in the future \(and accept all default values at once\), type `npm init -y`.

#### 3. Make your entry point.

Create your entry point file, Node will look for a file called `index.js` unless different name was specified\(check the `main` value in `package.json`\).

`touch index.js`

Write a console to check that it's working.

#### 4. Run your program!

To run a file in node via the command line, type `node [file name here]`.

`node index.js`