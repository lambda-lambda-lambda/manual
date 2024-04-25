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

### Project files are assigned root priviledges

This is due to a [bug](https://github.com/microsoft/vscode-remote-release/issues/2402) in the [Remote Container](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension, not this project.  During the container build process when the local machines's UID/GID matches an existing user UID/GID in the container it assigns `root` by default.  Note, in normal circumstances the [`remoteUser`](https://containers.dev/implementors/json_reference/#remoteUser) assigned would be `vscode` which always matches the local machine's user UID/GID values.

## References

- [Setting IAM Permissions and Roles](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-edge-permissions.html)
- [Cache behavior settings](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-web-values-specify.html#DownloadDistValuesObjectCaching)
- [AWS SDK for JavaScript](https://docs.aws.amazon.com/AWSJavaScriptSDK/latest/index.html)
- [Restrictions on edge functions](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/edge-functions-restrictions.html)
- [503 Lambda Limit Exceeded](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/http-503-lambda-limit-execeeded-error.html)

## Contributions

If you fix a bug, or have a code you want to contribute, please send a pull-request with your changes. (Note: Before committing your code please ensure that you are following the [Node.js style guide](https://github.com/felixge/node-style-guide))
