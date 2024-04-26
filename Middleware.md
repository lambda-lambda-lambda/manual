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

const {RouterError} = require('@lambda-lambda-lambda/router/src/router/Error.js');

/**
 * Middleware to define session state, if exists.
 */
module.exports = async (req, res, next) => {
  if (await checkSession()) {

    // Passed down the Router stack.
    req.plugin('session', true);

  } else {

    // Write to CloudWatch, continue..
    throw new Error('Output to console');
  }

  // next() should be omitted
};
```

See [L³ middleware](https://github.com/lambda-lambda-lambda/middleware) for more complex use cases.

## Handling exceptions

| Exception type          | Description                                                              |
|-------------------------|--------------------------------------------------------------------------|
| `throw new RouterError` | When called will immediately _exit the middleware stack_ and write the exception to [CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html) logs. |
| `throw new Error`       | When called will write the exception to [CloudWatch](https://docs.aws.amazon.com/AmazonCloudWatch/latest/logs/AnalyzingLogData.html) and _run the subsequent handler in middleware stack_. |
| `Promise.reject()`      | Same as `throw new Error` with no exception thrown.                      |
