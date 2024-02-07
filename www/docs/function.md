---
title: Function
description: Reference doc for the `Function` component
---

import Segment from '../../../components/tsdoc/Segment.astro';
import Section from '../../../components/tsdoc/Section.astro';
import InlineSection from '../../../components/tsdoc/InlineSection.astro';

The `Function` component is a higher level component that makes it easy to create an AWS Lambda Function.

## Examples

#### Using the minimal config
```ts
new sst.Function("MyFunction", {
  handler: "src/lambda.handler",
});
```

---

## Constructor

<Segment>
<Section type="signature">
```ts
new Function(name, args, opts?)
```
</Section>

<Section type="parameters">
#### Parameters
- <p><code class="key">name</code> <code class="primitive">string</code></p>
- <p><code class="key">args</code> [<code class="type">FunctionArgs</code>](#FunctionArgs)</p>
- <p><code class="key">opts</code> [<code class="type">ComponentResourceOptions</code>](https://www.pulumi.com/docs/concepts/options/)</p>
</Section>
</Segment>

## Properties

<Segment>
### nodes
<InlineSection>
**Type** <code class="type">Object</code>
- <p><code class="key">function</code> <code class="type">Output<[<code class="type">Function</code>](https://www.pulumi.com/registry/packages/aws/api-docs/s3/function/)></code></p>
- <p><code class="key">logGroup</code> [<code class="type">LogGroup</code>](#LogGroup)</p>
- <p><code class="key">role</code> <code class="type">Output<[<code class="type">Role</code>](https://www.pulumi.com/registry/packages/aws/api-docs/s3/role/)></code></p>
</InlineSection>
</Segment>

<Segment>
### url
<InlineSection>
**Type** <code class="type">Output<<code class="primitive">undefined</code><code class="symbol"> | </code><code class="primitive">string</code>></code>
</InlineSection>
</Segment>

## FunctionArgs
<Segment>
### architecture?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">arm64</code><code class="symbol"> | </code><code class="primitive">x86_64</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
x86_64
```
</InlineSection>
The system architectures for the function.
```js
{
  architecture: "arm64"
}
```
</Segment>
<Segment>
### bundle?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
Path to the esbuild output directory
```
</InlineSection>
Path to the source code directory for the function.
Use `bundle` only when the function code is ready to be deployed to Lambda.
Typically, omit `bundle`. If omitted, the handler file is bundled with esbuild, using its output directory as the bundle folder.
```js
{
  bundle: "packages/functions/src",
  handler: "index.handler"
}
```
</Segment>
<Segment>
### copyFiles?

<InlineSection>
**Type** <code class="type">Input<[<code class="type">FunctionCopyFilesArgs</code>](#FunctionCopyFilesArgs)[]></code>
</InlineSection>
Used to configure additional files to copy into the function bundle
```js
{
  copyFiles: [{ from: "src/index.js" }]
}
```
</Segment>
<Segment>
### description?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
No description
```
</InlineSection>
A description for the function.
```js
{
  description: "Handler function for my nightly cron job."
}
```
</Segment>
<Segment>
### environment?

<InlineSection>
**Type** <code class="type">Input<<code class="type">Record<<code class="primitive">string</code>, <code class="type">Input<<code class="primitive">string</code>></code>></code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
No environment variables
```
</InlineSection>
Key-value pairs that Lambda makes available for the function at runtime.
```js
{
  environment: {
    DEBUG: "true"
  }
}
```
</Segment>
<Segment>
### handler

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>></code>
</InlineSection>
Path to the handler for the function.
- If `bundle` is specified, the handler is relative to the bundle folder.
- If `bundle` is not specified, the handler is relative to the root of your SST application.
```js
{
  handler: "packages/functions/src/index.handler"
}
```
</Segment>
<Segment>
### injections?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>[]></code>
</InlineSection>

</Segment>
<Segment>
### link?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">any</code>[]></code>
</InlineSection>
Link resources to the function.
This will grant the function permissions to access the linked resources at runtime.
```js
{
  link: [myBucket, stripeKey],
}
```
</Segment>
<Segment>
### logging?

<InlineSection>
**Type** <code class="type">Input<[<code class="type">FunctionLoggingArgs</code>](#FunctionLoggingArgs)></code>
</InlineSection>

<InlineSection>
**Default** ```ts
Logs retained indefinitely
```
</InlineSection>
Configure function logging
</Segment>
<Segment>
### memory?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">number</code> MB<code class="symbol"> | </code><code class="primitive">number</code> GB></code>
</InlineSection>

<InlineSection>
**Default** ```ts
1024 MB
```
</InlineSection>
The amount of memory allocated for the function.
```js
{
  memory: "10240 MB"
}
```
</Segment>
<Segment>
### nodejs?

<InlineSection>
**Type** <code class="type">Input<[<code class="type">FunctionNodeJSArgs</code>](#FunctionNodeJSArgs)></code>
</InlineSection>
Used to configure nodejs function properties
</Segment>
<Segment>
### permissions?

<InlineSection>
**Type** <code class="type">Input<[<code class="type">FunctionPermissionArgs</code>](#FunctionPermissionArgs)[]></code>
</InlineSection>

<InlineSection>
**Default** ```ts
No permissions
```
</InlineSection>
Initial IAM policy statements to add to the created Lambda Role.
```js
{
  permissions: [
    {
      actions: ["s3:*"],
      resources: ["arn:aws:s3:::*"],
    },
  ]
}
```
</Segment>
<Segment>
### runtime?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">nodejs18.x</code><code class="symbol"> | </code><code class="primitive">nodejs20.x</code><code class="symbol"> | </code><code class="primitive">provided.al2023</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
nodejs18.x
```
</InlineSection>
The runtime environment for the function.
```js
{
  runtime: "nodejs20.x"
}
```
</Segment>
<Segment>
### streaming?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">boolean</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
false
```
</InlineSection>
Whether to enable streaming for the function.
```js
{
  streaming: true
}
```
</Segment>
<Segment>
### timeout?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">number</code> second<code class="symbol"> | </code><code class="primitive">number</code> seconds<code class="symbol"> | </code><code class="primitive">number</code> minute<code class="symbol"> | </code><code class="primitive">number</code> minutes<code class="symbol"> | </code><code class="primitive">number</code> hour<code class="symbol"> | </code><code class="primitive">number</code> hours<code class="symbol"> | </code><code class="primitive">number</code> day<code class="symbol"> | </code><code class="primitive">number</code> days></code>
</InlineSection>

<InlineSection>
**Default** ```ts
20 seconds
```
</InlineSection>
The amount of time that Lambda allows a function to run before stopping it.
```js
{
  timeout: "900 seconds"
}
```
</Segment>
<Segment>
### transform?

<InlineSection>
**Type** <code class="type">Object</code>
- <p><code class="key">function</code> <code class="type">Transform<[<code class="type">FunctionArgs</code>](https://www.pulumi.com/registry/packages/aws/api-docs/s3/functionargs/)></code></p>
</InlineSection>
</Segment>
<Segment>
### url?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">boolean</code><code class="symbol"> | </code>[<code class="type">FunctionUrlArgs</code>](#FunctionUrlArgs)></code>
</InlineSection>

<InlineSection>
**Default** ```ts
Disabled
```
</InlineSection>
Enable function URLs, a dedicated endpoint for your Lambda function.
```js
{
  url: true
}
```

```js
{
  url: {
    authorization: "iam",
    cors: {
      allowedOrigins: ['https://example.com'],
    }
  }
}
```
</Segment>

## FunctionCopyFilesArgs
<Segment>
### from

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>></code>
</InlineSection>
Source path relative to sst.config.ts
</Segment>
<Segment>
### to?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>></code>
</InlineSection>
Destination path relative to function root in bundle
</Segment>

## FunctionLoggingArgs
<Segment>
### retention?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">1 day</code><code class="symbol"> | </code><code class="primitive">3 days</code><code class="symbol"> | </code><code class="primitive">5 days</code><code class="symbol"> | </code><code class="primitive">1 week</code><code class="symbol"> | </code><code class="primitive">2 weeks</code><code class="symbol"> | </code><code class="primitive">1 month</code><code class="symbol"> | </code><code class="primitive">2 months</code><code class="symbol"> | </code><code class="primitive">3 months</code><code class="symbol"> | </code><code class="primitive">4 months</code><code class="symbol"> | </code><code class="primitive">5 months</code><code class="symbol"> | </code><code class="primitive">6 months</code><code class="symbol"> | </code><code class="primitive">1 year</code><code class="symbol"> | </code><code class="primitive">13 months</code><code class="symbol"> | </code><code class="primitive">18 months</code><code class="symbol"> | </code><code class="primitive">2 years</code><code class="symbol"> | </code><code class="primitive">3 years</code><code class="symbol"> | </code><code class="primitive">5 years</code><code class="symbol"> | </code><code class="primitive">6 years</code><code class="symbol"> | </code><code class="primitive">7 years</code><code class="symbol"> | </code><code class="primitive">8 years</code><code class="symbol"> | </code><code class="primitive">9 years</code><code class="symbol"> | </code><code class="primitive">10 years</code><code class="symbol"> | </code><code class="primitive">forever</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
Logs retained indefinitely
```
</InlineSection>
The duration function logs are kept in CloudWatch Logs.

When updating this property, unsetting it doesn't retain the logs indefinitely. Explicitly set the value to "forever".
```js
{
  logging: {
    retention: "1 week"
  }
}
```
</Segment>

## FunctionNodeJSArgs
<Segment>
### banner?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>></code>
</InlineSection>
Use this to insert an arbitrary string at the beginning of generated JavaScript and CSS files.
```js
nodejs: {
  banner: "console.log('Function starting')"
}
```
</Segment>
<Segment>
### esbuild?

<InlineSection>
**Type** <code class="type">Input<[<code class="type">BuildOptions</code>](https://esbuild.github.io/api/#build)></code>
</InlineSection>
This allows you to customize esbuild config.
</Segment>
<Segment>
### format?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">cjs</code><code class="symbol"> | </code><code class="primitive">esm</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
"esm"
```
</InlineSection>
Configure format
```js
nodejs: {
  format: "cjs"
}
```
</Segment>
<Segment>
### install?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>[]></code>
</InlineSection>
Packages that will be excluded from the bundle and installed into node_modules instead. Useful for dependencies that cannot be bundled, like those with binary dependencies.
```js
nodejs: {
  install: ["pg"]
}
```
</Segment>
<Segment>
### loader?

<InlineSection>
**Type** <code class="type">Input<<code class="type">Record<<code class="primitive">string</code>, [<code class="type">Loader</code>](https://esbuild.github.io/api/#build)></code>></code>
</InlineSection>
Configure additional esbuild loaders for other file extensions
```js
nodejs: {
  loader: {
   ".png": "file"
  }
}
```
</Segment>
<Segment>
### minify?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">boolean</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
true
```
</InlineSection>
Enable or disable minification
```js
nodejs: {
  minify: false
}
```
</Segment>
<Segment>
### sourcemap?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">boolean</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
false
```
</InlineSection>
Configure if sourcemaps are generated when the function is bundled for production. Since they increase payload size and potentially cold starts they are not generated by default. They are always generated during local development mode.
```js
nodejs: {
  sourcemap: true
}
```
</Segment>
<Segment>
### splitting?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">boolean</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
false
```
</InlineSection>
If enabled, modules that are dynamically imported will be bundled as their own files with common dependencies placed in shared chunks. This can help drastically reduce cold starts as your function grows in size.
```js
nodejs: {
  splitting: true
}
```
</Segment>

## FunctionPermissionArgs
<Segment>
### actions

<InlineSection>
**Type** <code class="primitive">string</code>[]
</InlineSection>
</Segment>
<Segment>
### resources

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">string</code>></code>[]
</InlineSection>
</Segment>

## FunctionUrlArgs
<Segment>
### authorization?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">none</code><code class="symbol"> | </code><code class="primitive">iam</code>></code>
</InlineSection>

<InlineSection>
**Default** ```ts
"none"
```
</InlineSection>
The authorization for the function URL
```js
{
  url: {
    authorization: "iam",
  },
}
```
</Segment>
<Segment>
### cors?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">boolean</code><code class="symbol"> | </code>[<code class="type">FunctionUrlCorsArgs</code>](#FunctionUrlCorsArgs)></code>
</InlineSection>

<InlineSection>
**Default** ```ts
true
```
</InlineSection>
CORS support for the function URL
```js
{
  url: {
    cors: true,
  },
}
```

```js
{
  url: {
    cors: {
      allowedMethods: ["GET", "POST"],
      allowedOrigins: ['https://example.com'],
    },
  },
}
```
</Segment>

## FunctionUrlCorsArgs
<Segment>
### allowCredentials?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">boolean</code>></code>
</InlineSection>
Whether to allow cookies or other credentials in requests to the function URL. The default is `false`.
</Segment>
<Segment>
### allowHeaders?

<InlineSection>
**Type** <code class="type">Input<<code class="type">Input<<code class="primitive">string</code>></code>[]></code>
</InlineSection>
The HTTP headers that origins can include in requests to the function URL. For example: `["date", "keep-alive", "x-custom-header"]`.
</Segment>
<Segment>
### allowMethods?

<InlineSection>
**Type** <code class="type">Input<<code class="type">Input<<code class="primitive">POST</code><code class="symbol"> | </code><code class="primitive">*</code><code class="symbol"> | </code><code class="primitive">DELETE</code><code class="symbol"> | </code><code class="primitive">GET</code><code class="symbol"> | </code><code class="primitive">HEAD</code><code class="symbol"> | </code><code class="primitive">OPTIONS</code><code class="symbol"> | </code><code class="primitive">PATCH</code><code class="symbol"> | </code><code class="primitive">PUT</code>></code>[]></code>
</InlineSection>
The HTTP methods that are allowed when calling the function URL. For example: `["GET", "POST", "DELETE"]`, or the wildcard character (`["*"]`).
</Segment>
<Segment>
### allowOrigins?

<InlineSection>
**Type** <code class="type">Input<<code class="type">Input<<code class="primitive">string</code>></code>[]></code>
</InlineSection>
The origins that can access the function URL. You can list any number of specific origins (or the wildcard character (`"*"`)), separated by a comma. For example: `["https://www.example.com", "http://localhost:60905"]`.
</Segment>
<Segment>
### exposeHeaders?

<InlineSection>
**Type** <code class="type">Input<<code class="type">Input<<code class="primitive">string</code>></code>[]></code>
</InlineSection>
The HTTP headers in your function response that you want to expose to origins that call the function URL.
</Segment>
<Segment>
### maxAge?

<InlineSection>
**Type** <code class="type">Input<<code class="primitive">number</code> second<code class="symbol"> | </code><code class="primitive">number</code> seconds<code class="symbol"> | </code><code class="primitive">number</code> minute<code class="symbol"> | </code><code class="primitive">number</code> minutes<code class="symbol"> | </code><code class="primitive">number</code> hour<code class="symbol"> | </code><code class="primitive">number</code> hours<code class="symbol"> | </code><code class="primitive">number</code> day<code class="symbol"> | </code><code class="primitive">number</code> days></code>
</InlineSection>
The maximum amount of time, in seconds, that web browsers can cache results of a preflight request. By default, this is set to `0`, which means that the browser doesn't cache results. The maximum value is `86400`.
</Segment>