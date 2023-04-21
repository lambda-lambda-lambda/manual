# Getting Started

The easiest way to created an application, without the need to [manually install](#manual-installation) this package, is to use the [L³ Visual Studio Code extension](https://marketplace.visualstudio.com/items?itemName=Nuxy.vscode-lambda-lambda-lambda). Doing so allows you to..

- Scaffold app sources and dependencies.
- Run it locally (in [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers))
- Test code changes in realtime.
- Deploy app sources to AWS.
- Generate [JSDoc](https://jsdoc.app)/[Swagger](https://swagger.io) documentation.

## Build dependencies

If you're not using the [L³ VS Code extension](https://marketplace.visualstudio.com/items?itemName=Nuxy.vscode-lambda-lambda-lambda) and want to _run this package locally_ you must install the following dependencies:

- [AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html)
- [Node.js](https://nodejs.org)

## Manual installation

If you just looking to leverage the Request/Response handling [API](CommonMethods.md) in your Lambda functions, install this package using [NPM](https://npmjs.com).

    $ npm install @lambda-lambda-lambda/router
