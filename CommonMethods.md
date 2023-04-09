# Common methods

The following methods are supported based on the class context.  For further information please refer to the [JSDoc](Developers.md#cli-options) generated [documentation](https://nuxy.github.io/lambda-lambda-lambda) which includes method `arguments`/`return` types and general usage examples.

| Router Method               | Description                               |
|-----------------------------|-------------------------------------------|
| `router.setPrefix(path)`    | Set URI path prefix.                      |
| `router.use(func)`          | Load the Route (e.g. [Middleware](./Middleware.md)) handler. |
| `router.get(path, func)`    | Handle HTTP GET requests.                 |
| `router.put(path, func)`    | Handle HTTP PUT requests.                 |
| `router.patch(path, func)`  | Handle HTTP PATCH requests.               |
| `router.post(path, func)`   | Handle HTTP POST requests.                |
| `router.delete(path, func)` | Handle HTTP DELETE requests.              |
| `router.default(func)`      | Set router fallback (default route).      |
| `router.response()`         | Return the AWS response object.           |

| Request Method            | Description                                       |
|---------------------------|---------------------------------------------------|
| `req.is(mimeType)`        | Check `Accept` matches the given value.           |
| `req.header(name)`        | Return value for given HTTP header name.          |
| `req.getHeaders()`        | Return the headers of the request.                |
| `req.method()`            | Return the HTTP method of the request.            |
| `req.uri()`               | Return the relative path of the requested object. |
| `req.clientIp()`          | Return the HTTP client IP (remote address).       |
| `req.param(name)`         | Return the HTTP request parameters or name/value. |
| `req.queryString()`       | Return the serialized query parameters.           |
| `req.body()`              | Return the base64-encoded body data.              |
| `req.plugin(name, value)` | Set/Get value passed down the application stack.  |

| Response Method                 | Description                     |
|---------------------------------|---------------------------------|
| `res.setHeader(name, value)`    | Set HTTP response header.       |
| `res.status(code).send(body)`   | Send the HTTP response (`Array`, `Buffer`, `Object`, `String`). |
| `res.status(code).data(buffer)` | Send binary data with HTTP response. |
| `res.status(code).json(obj)`    | Send the HTTP response as JSON. |
| `res.status(code).text(str)`    | Send the HTTP response as text. |
