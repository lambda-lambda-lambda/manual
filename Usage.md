# Usage

Unless your application requires [complex routing](./ComplexRouting.md), route handlers can be defined within the [Lambda function scope](https://docs.aws.amazon.com/lambda/latest/operatorguide/global-scope.html).  Otherwise [route handlers](./ComplexRouting.md#route-handler) are loaded from `appName/src/routes` directory in hierarchical order, starting with the default handler `appName/src/app.js` as described below.

## Synchronous example

```javascript
// .. appName/src/app.js

'use strict';

// Load module.
const Router = require('lambda-lambda-lambda');

/**
 * @see AWS::Serverless::Function
 */
exports.handler = (event, context, callback) => {
  const {request, response} = event.Records[0].cf;

  const router = new Router(request, response);
  router.setPrefix('/api'); // optional, default /

  // Globally scoped to /api/*
  router.use(function(req, res, next) {
    if (req.method() === 'CONNECT') {
      res.status(405).send();
    } else {
      next(); // Run subsequent handler
    }
  });

  // Send root response.
  router.get('/', function(req, res) {
    res.status(501).send();
  });

  // .. everything else.
  router.default(function(req, res) {
    res.status(404).send();
  });

  callback(null, router.response());
};
```

## Asynchronous example

```javascript
// .. appName/src/app.js

'use strict';

// Load module.
const Router = require('lambda-lambda-lambda');

/**
 * @see AWS::Serverless::Function
 */
exports.handler = async (event) => {
  const {request, response} = event.Records[0].cf;

  const router = new Router(request, response);

    // .. Router Methods

  return await router.response();
};
```
