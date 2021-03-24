# fastify-error

![CI](https://github.com/fastify/fastify-error/workflows/CI/badge.svg)
[![NPM version](https://img.shields.io/npm/v/fastify-error.svg?style=flat)](https://www.npmjs.com/package/fastify-error)
[![Known Vulnerabilities](https://snyk.io/test/github/fastify/fastify-error/badge.svg)](https://snyk.io/test/github/fastify/fastify-error)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://standardjs.com/)

A small utility, used by Fastify itself, for generating consistent error objects across your codebase and plugins.

### Install
```
npm i fastify-error
```

### Usage

The module exports a function that you can use consistent error objects, it takes 4 parameters:

```
createError(code, message [, statusCode [, Base]])
```

- `code` (`string`, required) - The error code, you can access it later with `error.code`. For consistency, we recommend to prefix the plugins error codes with `FST_`
- `message` (`string`, required) - The error message. You can also use interpolated strings for formatting the message.
- `statusCode` (`number`, optional) - The status code that Fastify will use if the error is sent via http.
- `Base` (`Error`, optional) - The base error object that will be used. (eg `TypeError`, `RangeError`)

```js
const createError = require('fastify-error')
const CustomError = createError('ERROR_CODE', 'message')
console.log(new CustomError())
```

How to use an interpolated string:
```js
const createError = require('fastify-error')
const CustomError = createError('ERROR_CODE', 'Hello %s')
console.log(new CustomError('world')) // error.message => 'Hello world'
```

## License

Licensed under [MIT](./LICENSE).
