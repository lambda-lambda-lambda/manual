# Developers

## Dev dependencies

- [Visual Studio Code](https://code.visualstudio.com/download)
- [Docker](https://www.docker.com/get-started)
- [Node.js](https://nodejs.org)

## CLI options

Run [ESLint](https://eslint.org) on project sources:

    $ npm run lint

Generate [Swagger](https://swagger.io) OpenAPI definitions:

    $ npm run genapi

Generate documentation using [JSDoc](https://jsdoc.app):

    $ npm run gendoc

## Known issues

### Project files are assigned incorrect priviledges

If you experience this when working between local/remote development environments this is due to the user UID [not being present during build time](https://github.com/microsoft/vscode-remote-release/issues/6834#issuecomment-1158600543). In this case the default `1000` is defined as both the UID/GID for the remote user.  You can override this behavior by updating the following project `devcontainer.json` build arguments or by exporting the UID/GID in your `.bash_profile`.

```json
"build": {
  "dockerfile": "Dockerfile",
  "args": {
    "UID": "${localEnv:UID:1234}", // Default to 1234
    "GID": "${localEnv:GID:1234}"
  }
},
```

## References

- [Setting IAM Permissions and Roles](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-edge-permissions.html)
- [Cache behavior settings](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html#DownloadDistValuesObjectCaching)
- [AWS SDK for JavaScript](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/index.html)
- [Restrictions on edge functions](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/edge-functions-restrictions.html)
- [503 Lambda Limit Exceeded](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/http-503-lambda-limit-execeeded-error.html)

## Contributions

If you fix a bug, or have a code you want to contribute, please send a pull-request with your changes. (Note: Before committing your code please ensure that you are following the [Node.js style guide](https://github.com/felixge/node-style-guide))
