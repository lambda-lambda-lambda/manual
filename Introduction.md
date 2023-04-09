# Introduction

Get acquainted with [L³](https://github.com/lambda-lambda-lambda) and dive head first into the fire.

## What is `lambda-lambda-lambda`?

L³ is an extremely simple/lightweight [Node.js](https://nodejs.org/en/about) serverless application framework that was designed to meet the following requirements:

- Lightning fast application development.
- Easy to audit (no bloat or dependency hell, [KISS](https://en.wikipedia.org/wiki/KISS_principle)).
- Promotes [test-driven development](https://en.wikipedia.org/wiki/Test-driven_development).
- Scales indefinitely at a _very low cost_.

## Why would you use L³?

You want to build complex web applications that leverage both AWS [CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html) caching and [Lambda@Edge](https://aws.amazon.com/lambda/edge) accessibility without:

- Complex [CloudFormation](https://docs.aws.amazon.com/cloudformation/index.html) setups that includes fragmentation of application Lambda functions.
  - L³ handles path translation (i.e. [route handling](https://github.com/lambda-lambda-lambda/router#route-handler)) in a single Lambda function.
- Coupling to a single SASS provider.
  - You can run your L³ application in your own PM2 server using the [lambda-edge-server](https://github.com/lambda-lambda-lambda/lambda-edge-server) emulator.
- [Paying through the nose](https://idioms.thefreedictionary.com/pay+through+the+nose) for idle services (e.g. EC2 servers, ElastiCache, API Gateway).
  - L³ can help minimize your application footprint without sacrificing availability or stability.
