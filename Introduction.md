# Introduction

Get acquainted with [L³](https://github.com/lambda-lambda-lambda) before you dive dive head-first into the fire :fire:

## What is `lambda-lambda-lambda` (L³)?

L³ is an extremely simple/lightweight [Node.js](https://nodejs.org/en/about) serverless application framework that was designed to meet the following requirements:

- Lightning fast application development.
- Easy to audit (no code bloat or dependency hell - [KISS](https://en.wikipedia.org/wiki/KISS_principle))
- TDD ([test-driven development](https://en.wikipedia.org/wiki/Test-driven_development)) by design.
- Scales indefinitely at a _very low cost_.

The framework, which is nothing more than a collection of dependencies, consists of a [router](https://github.com/lambda-lambda-lambda/router) and related [middleware](https://github.com/lambda-lambda-lambda/middleware), [server](https://github.com/lambda-lambda-lambda/lambda-edge-server) emulator, and common tools (e.g. [ESLint](https://eslint.org), [JSDoc](https://jsdoc.app), [Swagger](https://swagger.io)) to further application development using latest coding standards.

### L³ framework features

- Request/Response handling [API](CommonMethods.md).
- [Routes](ComplexRouting.md#route-handler) and URI [Resource](ComplexRouting.md#resource-handler) support.
- Local/Globally scoped [Middleware](Middleware.md#scope).
- [Visual Studio Code](https://code.visualstudio.com) integration.
- Open Source, [MIT licensed](https://github.com/lambda-lambda-lambda/router/blob/master/LICENSE), FREE.
- Lightweight (**no dependencies**).

### Why would you use L³?

You want to build complex web applications that leverage both AWS [CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) caching and [Lambda@Edge](https://aws.amazon.com/lambda/edge) global accessibility without:

- Complex [CloudFormation](https://docs.aws.amazon.com/cloudformation/index.html) setups that includes fragmentation of Lambda tasks and services.
  - L³ handles HTTP path translation (i.e. [route handling](https://github.com/lambda-lambda-lambda/router#route-handler)) which maps the request to an existing Lambda function.
- [Paying through the nose](https://idioms.thefreedictionary.com/pay+through+the+nose) for idle services (e.g. EC2 servers, ElastiCache, API Gateway).
  - L³ can help minimize your application footprint without sacrificing availability or stability.
- Coupling to a single Cloud/SASS provider.
  - You can run your L³ application in your own [Node.js](https://nodejs.org) PM2 server using the [lambda-edge-server](https://github.com/lambda-lambda-lambda/lambda-edge-server) emulator.
