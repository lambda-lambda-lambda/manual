# Common methods

The following methods are supported based on the class context.  For further information please refer to the [JSDoc](Developers.md#cli-options) generated [documentation](https://lambda-lambda-lambda.github.io/doc) which includes method `arguments`/`return` types and general usage examples.

## Router

The class methods below should _always be declared_ within the main Lambda function scope.

| Method                                                                                | Description                               |
|----------------------------------------------------------------------------------------------|-------------------------------------------|
| [`setPrefix(path)`](https://lambda-lambda-lambda.github.io/doc/Router.html#setPrefix) | Set URI path prefix.                      |
| [`use(func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#use)             | Load the Route (e.g. [Middleware](./Middleware.md)) handler. |
| [`get(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#get)       | Handle HTTP GET requests.                 |
| [`put(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#put)       | Handle HTTP PUT requests.                 |
| [`patch(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#patch)   | Handle HTTP PATCH requests.               |
| [`post(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#post)     | Handle HTTP POST requests.                |
| [`delete(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#delete) | Handle HTTP DELETE requests.              |
| [`default(func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#default)     | Set router fallback (default route).      |
| [`response()`](https://lambda-lambda-lambda.github.io/doc/Router.html#response)       | Return the AWS response object.           |

### Example

```javascript
'use strict';

// Load module.
const Router = require('lambda-lambda-lambda');

/**
 * @see AWS::Serverless::Function
 */
exports.handler = (event, context, callback) => {
  const {request, response} = event.Records[0].cf;

  const router = new Router(request, response);
  router.methodName();

    ..
```

## Request

The class methods below are accessible within the [Route](https://github.com/lambda-lambda-lambda/manual/blob/master/ComplexRouting.md#route-handler), [Resource](https://github.com/lambda-lambda-lambda/manual/blob/master/ComplexRouting.md#resource-handler), or [Middleware](https://github.com/lambda-lambda-lambda/manual/blob/master/Middleware.md) handler function scope as `req` argument.

| Request Method                                                                                    | Description                                       |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------|
| [`is(mimeType)`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#is)            | Check `Accept` matches the given value.           |
| [`header(name)`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#header)        | Return value for given HTTP header name.          |
| [`getHeaders()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#getHeaders)    | Return the headers of the request.                |
| [`method()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#method)            | Return the HTTP method of the request.            |
| [`uri()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#uri)                  | Return the relative path of the requested object. |
| [`clientIp()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#clientIp)        | Return the HTTP client IP (remote address).       |
| [`param(name)`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#param)          | Return the HTTP request parameters or name/value. |
| [`queryString()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#queryString)  | Return the serialized query parameters.           |
| [`body()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#body)                | Return the base64-encoded body data.              |
| [`plugin(name, value)`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#plugin) | Set/Get value passed down the application stack.  |

### Example

```javascript
function (req, res, next) {
  req.methodName();

    ..
```

## Response

The class methods below are accessible within the [Route](https://github.com/lambda-lambda-lambda/manual/blob/master/ComplexRouting.md#route-handler), [Resource](https://github.com/lambda-lambda-lambda/manual/blob/master/ComplexRouting.md#resource-handler), or [Middleware](https://github.com/lambda-lambda-lambda/manual/blob/master/Middleware.md) handler function scope as `res` argument.

| Response Method                                                                                          | Description                     |
|----------------------------------------------------------------------------------------------------------|---------------------------------|
| [`setHeader(name, value)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#setHeader) | Set HTTP response header.       |
| [`status(code).send(body)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#status)   | Send the HTTP response (`Array`, `Buffer`, `Object`, `String`). |
| [`status(code).data(buffer)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#status) | Send binary data with HTTP response. |
| [`status(code).json(obj)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#status)    | Send the HTTP response as JSON. |
| [`status(code).text(str)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#status)    | Send the HTTP response as text. |

### Example

```javascript
function (req, res, next) {
  res.methodName();

    ..
```
