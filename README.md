# A backend model for NodeJS

## This was made following <a href="https://rocketseat.com.br/">RocketSeat</a> tutorials. :rocket:

### Setting up the development environment

This is a documentation about the enviroment setup to develop a nodejs backend. It was made by myself and to my future self because that's a lot to remember.

Enjoy :)

---

Init yarn:

```bash
yarn init -y
```

Install express

```bash
yarn add express
```

Create the following structure

```bash
src
├── app.js
├── routes.js
└── server.js
```

Structure the files using a class named App and then isolate the app from the routes and the server.

* app.js: contains the configs of the server.

* server.js: used to initiate app. (server.listen).

* routes.js: contain the routes(obviously).

Install sucrase and nodemon as development depencies

```bash
yarn add sucrase nodemon -D
```

At "package.json", include "scripts"

```json
"scripts": {
    "dev": "nodemon src/server.js"
  },
```

And create a file named "nodemon.js" with the following json

```json
{
    "execMap": {
        "js": "sucrase-node"
    }
}
```

---

### Setting up Eslint, Prettier & Editor config

This is used to set some rules to how your code so it can be standardized, that is important mainly when working in teams.

_Don't forget that you need Eslint and Prettier extensions installed._

Install Eslint as a developer depedency.

```bash
yarn add eslint -D
```

Exec Eslint

```bash
yarn eslint --init
```

- [x] To check syntax, find problems, and enforce code style
- [x] Javascript modules (import/export)
- [x] None of these
- [x] Node
- [x] Use a popular style guide
- [x] Airbnb
- [x] Javascript

After process completed, delete packagejson-lock and run _yarn_

Allow Eslint to automatically fix your code

```json
"eslint.autoFixOnSave": true,
    "eslint.validate": [
        {
            "language": "javascript",
            "autoFix": true
        },
        {
            "language": "javascriptreact",
            "autoFix": true
        },
        {
            "language": "typescript",
            "autoFix": true
        },
        {
            "language": "typescriptreact",
            "autoFix": true
        }
    ],
```

Some extra rules for Eslint

```json
 rules: {
    "class-methods-use-this": "off",
    "no-param-reassign": "off",
    "camelcase": "off",
    "no-unused-vars": ["error", { "argsIgnorePattern": "next" }],
  },
```

Install Prettier

```bash
yarn add prettier eslint-config-prettier eslint-plugin-prettier -D
```

Now inside .eslintrc.js

```json
 extends: [
    "airbnb-base",
    "prettier"
  ],
 plugins: ["prettier"],
```

Then, inside rules:

```json
 rules: {
    "prettier/prettier": "error",
    "class-methods-use-this": "off",
    "no-param-reassign": "off",
    "camelcase": "off",
    "no-unused-vars": ["error", { "argsIgnorePattern": "next" }],
  },
```

Create a .prettierrc file and add the following inside it

```json
{
    "singleQuote": true,
    "trailingComma": "es5"
}
```

Now your code shold be formatted beautifully :)
