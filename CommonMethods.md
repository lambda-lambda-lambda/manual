# Common methods

The following methods are supported based on the class context.  For further information please refer to the [JSDoc](Developers.md#cli-options) generated [documentation](https://nuxy.github.io/lambda-lambda-lambda/doc) which includes method `arguments`/`return` types and general usage examples.

| Router Method                                                                                | Description                               |
|----------------------------------------------------------------------------------------------|-------------------------------------------|
| [`router.setPrefix(path)`](https://lambda-lambda-lambda.github.io/doc/Router.html#setPrefix) | Set URI path prefix.                      |
| [`router.use(func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#use)             | Load the Route (e.g. [Middleware](./Middleware.md)) handler. |
| [`router.get(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#get)       | Handle HTTP GET requests.                 |
| [`router.put(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#put)       | Handle HTTP PUT requests.                 |
| [`router.patch(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#patch)   | Handle HTTP PATCH requests.               |
| [`router.post(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#post)     | Handle HTTP POST requests.                |
| [`router.delete(path, func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#delete) | Handle HTTP DELETE requests.              |
| [`router.default(func)`](https://lambda-lambda-lambda.github.io/doc/Router.html#default)     | Set router fallback (default route).      |
| [`router.response()`](https://lambda-lambda-lambda.github.io/doc/Router.html#response)       | Return the AWS response object.           |

| Request Method                                                                                    | Description                                       |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------|
| [`req.is(mimeType)`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#is)            | Check `Accept` matches the given value.           |
| [`req.header(name)`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#header)        | Return value for given HTTP header name.          |
| [`req.getHeaders()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#getHeaders)    | Return the headers of the request.                |
| [`req.method()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#method)            | Return the HTTP method of the request.            |
| [`req.uri()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#uri)                  | Return the relative path of the requested object. |
| [`req.clientIp()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#clientIp)        | Return the HTTP client IP (remote address).       |
| [`req.param(name)`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#param)          | Return the HTTP request parameters or name/value. |
| [`req.queryString()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#queryString)  | Return the serialized query parameters.           |
| [`req.body()`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#body)                | Return the base64-encoded body data.              |
| [`req.plugin(name, value)`](https://lambda-lambda-lambda.github.io/doc/RouterRequest.html#plugin) | Set/Get value passed down the application stack.  |

| Response Method                                                                                          | Description                     |
|----------------------------------------------------------------------------------------------------------|---------------------------------|
| [`res.setHeader(name, value)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#setHeader) | Set HTTP response header.       |
| [`res.status(code).send(body)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#status)   | Send the HTTP response (`Array`, `Buffer`, `Object`, `String`). |
| [`res.status(code).data(buffer)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#status) | Send binary data with HTTP response. |
| [`res.status(code).json(obj)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#status)    | Send the HTTP response as JSON. |
| [`res.status(code).text(str)`](https://lambda-lambda-lambda.github.io/doc/RouterResponse.html#status)    | Send the HTTP response as text. |
