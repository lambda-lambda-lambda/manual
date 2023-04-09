# Middleware

## Synchronous example

```javascript
// .. appName/src/middleware/ContentTypeHeader.js

'use strict';

/**
 * Middleware to send Content-Type header.
 */
module.exports = (req, res, next) => {
  res.setHeader('Content-Type', 'text/html');

  next(); // Run subsequent handler.
};
```

## Asynchronous example

```javascript
// .. appName/src/middleware/SessionCheck.js

'use strict';

/**
 * Middleware to define session state, if exists.
 */
module.exports = async (req, res, next) => {
  if (await checkSession()) {
    req.plugin('session', true); // Passed down the chain.
  } else {
    return Promise.reject('Output to console');
  }

  // next() should be omitted, use Promise.reject().
};
```

See [restfulApiHandler](https://github.com/lambda-lambda-lambda/example/tree/master/restfulApiHandler/src/middleware) example for more complex use cases.
