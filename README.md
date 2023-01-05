# TODO

- add in console logging of actual sql commands
  - consider refactorying pool into db.query
- add in dotenv with prod, test, dev
- Add in testing
  - Talk about mocha vs jest for mongoose

# Description

This is a template project. It implements a minimal React frontend with Redux, express backend, postgresql database interface, and OAuth authentication.

Start the frontend with `npm run frontend`
Start the backend with `npm run backend`

# Notes on design decisions

## .env and secrets.js

You can store environment variables in either `.env` or `secrets.js`. Each method comes with advantages and disadvantages:

The advantage of .env is:

- You can specify .env variables when running bash scripts. This because important during testing, when we want to switch from `MODE=dev` to `MODE=test` on the fly without editing secrets.js

The advantage of `secrets.js` is:

- You can do logic such as concatenating a password to a URI.
- You can declar non-string variables (bools, functions, etc.)

When using .env, to access `process.env` you will need the following:
`require('dotenv').config();`

## Babel

For more information on babel setup: https://www.robinwieruch.de/minimal-node-js-babel-setup/

Babel is required to enable uncoming javascript features in node (such as import), as well as browser transpilation (typescript, etc.)

Babel configuration is done within ".babelrc" instead of package.json because this is considered best practice (reasons below):

- .babelrc is specific to babel and reduces clutter in package.json. Imagine doing webpack, ESLint, Babel configuration all within package.json and how difficult it would be to read.
- .babel is more modular and makes it easier to share Babel configurations

## Webpack

For more information on webpack setup: https://www.robinwieruch.de/webpack-setup-tutorial/

I decided on webpack over vite. Why?
