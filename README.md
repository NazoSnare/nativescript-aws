# NativeScript AWS plugin

> Never check in your AWS keys! Bots scan public repos and will create server instances you'll get billed for.

## Q & A
#### Q. Why this module and not use the AWS JS SDK directly?
A. Because you can't due to dependencies on Node and/or the browser (crypto, path, DOMParser, etc). Both of which are not available in a NativeScript context. 

#### Q. So is this plugin not using the AWS JS SDK then?
A. Oh yes it is but upon installation the plugin will modify a few bits in the AWS SDK so it's NativeScript-compatible.

#### Q. But doesn't browserify / Webpack solve this for us?
A. Not in this case, at least not without further modifications. Feel free to submit a PR for a nicer implementation, but this is the best I could think of.

#### Q. Not bad actually, can we use this approach for other npm modules that depend on node built-ins?
A. Thanks. And good point. Most of this should apply to more generic usages so expect me to release some universal plugin this one will depend on.


## Installation
From the command prompt go to your app's root folder and execute:

```
tns plugin add nativescript-aws
```

Make sure you use TypeScript (as our demo app does), because this plugin exposes the AWS SDK's
TypeScript definitions so you'll have an easier time interacting with Amazons services.

## Demo app
Really, check [the demo](demo)! It shows how to interact with S3 and Dynamo,
but you should be able to interact with all other AWS services as well.

Run the demo app from the root of the project: `npm run demo.ios` or `npm run demo.android`.

### iOS & Android screenshots
<img src="https://raw.githubusercontent.com/EddyVerbruggen/nativescript-aws/master/screenshots/ios-s3-list.png" width="225px" height="400px"/>
<img src="https://raw.githubusercontent.com/EddyVerbruggen/nativescript-aws/master/screenshots/android-s3-list.png" width="225px" height="400px"/>

## API
100% equal to [the `aws-sdk` module](https://www.npmjs.com/package/aws-sdk). Look at their docs and use TypeScript to make your life easier.

## Disclaimer
I've tried to iron out all compatibility issues between AWS and NativeScript,
but you may use some service that throws an error at runtime because it's requiring some
unsupported node module. Please open an issue in that case and I'll take a look!