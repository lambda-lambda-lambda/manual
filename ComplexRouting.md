# Complex routing

When constructing a routing handler the following methods/aliases are supported which can be used interchangeably when defining [Route](#route-handler) or [Resource](#resource-handler) handlers.

| Handler Method | Alias  |
|----------------|--------|
| get            | index  |
| post           | submit |
| put            | create |
| patch          | update |
| delete         | N/A    |

## Route handler

```javascript
// .. appName/src/routes/foo.js

'use strict';

// Load module.
const contentTypeHeader = require('middleware/ContentTypeHeader');

/**
 * @export {Object}
 */
module.exports = {
  middleware: [contentTypeHeader], // Locally scoped to /api/foo

  /**
   * GET /api/foo
   */
  index (req, res) {
    res.status(200).send('Lambda, Lambda, Lambda');
  },

  /**
   * PUT /api/foo
   */
  create (req, res) {
    res.status(201).send();
  },

  /**
   * PATCH /api/foo
   */
  update (req, res) {
    res.status(204).send();
  },

  /**
   * DELETE /api/foo
   */
  delete (req, res) {
    res.status(410).send();
  },

  /**
   * POST /api/foo
   */
  submit (req, res) {
    res.status(200).send();
  }
};
```

## Resource handler

```javascript
// .. appName/src/routes/foo/bar.js

'use strict';

/**
 * @export {Object}
 */
module.exports = {
  resource: true, // Everything is a resource.

  /**
   * GET /api/foo/bar/<resourceId>
   */
  get (req, res, id) {
    res.setHeader('Content-Type', 'application/json');
    res.status(200).json({and: 'Omega Mu'});
  },

  /**
   * PUT /api/foo/bar/<resourceId>
   */
  put (req, res, id) {
    res.status(201).send();
  },

  ..
};
```

## Mixed Route/Resource handler

```javascript
// .. appName/src/routes/foo.js

'use strict';

/**
 * @export {Object}
 */
module.exports = {
  resource: ['put'], // Limit to resource.

  /**
   * GET /api/foo
   */
  index (req, res) {
    res.setHeader('Content-Type', 'text/html');
    res.status(200).send('Lambda, Lambda, Lambda');
  },

  /**
   * PUT /api/foo/<resourceId>
   */
  put (req, res, id) {
    res.setHeader('Content-Type', 'application/json');
    res.status(200).json({and: 'Omega Mu'});
  },

  ..
};
```

## Asynchronous handler

When using an explicit `Promise` that returns a promised event, always declare your handler method as `async` function (see examples below).

```javascript
// .. appName/src/routes/foo.js

'use strict';

/**
 * @export {Object}
 */
module.exports = {
  resource: ['get', 'patch'],

  /**
   * GET /api/foo
   */
  async index (req, res) {
    res.setHeader('Content-Type', 'text/html');
    res.status(200).send('Lambda, Lambda, Lambda');
  },

  /**
   * GET /api/foo/<resourceId>
   */
  async get (req, res, id) {
    return asyncOperation(id)
      .then(function(result) {
        res.setHeader('Content-Type', 'text/html');
        res.status(200).send(result || 'No result');
      })
      .catch(function() {
        res.status(500).send();
      });
  },

  /**
   * PATCH /api/foo/<resourceId>
   */
  async patch (req, res, id) {
    try {
      const result = await asyncOperation(id);

      res.setHeader('Content-Type', 'text/html');
      res.status(200).send(result || 'No result');
    } catch(err) {
      res.status(500).send();
    }
  },

  ..
};
```
