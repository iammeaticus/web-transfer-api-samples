# Getting Started
These samples to show how to integrate the Signiant Web Transfer API into a web application. The Signiant Web Transfer API supports transfers (upload and download) to / from:
* Amazon S3
* Microsoft Azure
* Local storage on your network

# Current Version
The current version of the transfer API is 2.7.4.

# API Key
You will require an API key to transfer files.

If you are transferring to local storage, you can get an API key from https://developer.mediashuttle.com

If you are transferring to cloud storage you can request one from http://info.signiant.com/flight-Free-Trial_1.html

# API Documentation
Visit the <a href="https://developer.signiant.com">Signiant developer site</a> for up to date documentation about the Transfer API.

## Loading Transfer API

`<script type="text/javascript" src="https://updates.signiant.com/javascript-api/2.7.1/transferapi.min.js" ></script>`

Transfer API widgets are referenced by:

`<link rel="stylesheet" href="https://updates.signiant.com/javascript-api/2.7.1/widgets/transferProgress/mediashuttledownload.css">`

`<link rel="stylesheet" href="https://updates.signiant.com/javascript-api/2.7.1/widgets/transferProgress/mediashuttletransferprogress.css" >`

`<link rel="stylesheet" href="https://updates.signiant.com/javascript-api/2.7.1/widgets/draganddrop/mediashuttlednd.css">`

`<script src="https://updates.signiant.com/javascript-api/2.7.1/widgets/draganddrop/mediashuttlednd.js" type="text/javascript"></script>`

`<script src="https://updates.signiant.com/javascript-api/2.7.1/widgets/download/mediashuttledownload.js"></script>`

`<script src="https://updates.signiant.com/javascript-api/2.7.1/widgets/transferProgress/mediashuttletransferprogress.js"></script>`


The API Key is now provided to the Transfer Object directly, rather than through the `<script>` tag. To specify an API key to use for a transfer call the following method on an Upload or Download object:

```javascript
var upload = new Signiant.Mst.Upload();
upload.setApiKey('abc123');

var download = new Signiant.Mst.Download();
download.setApiKey('abc123');`
```

Note that this replaces the line:
```javascript
transferObject.setProperty('com.signiant.interactivetransfer.engine.api_key', 'YOUR_API_KEY');
```
that may be present in your code.

# Changes
### Transfer API v2.7.4 - Monday September 25, 2017
*	Improved UX for transfer interruptions and recovery.

See <a href="change.md">Transfer API Changes</a> for earlier Transfer API changes.

# Security
Signiant Web Transfer API customers using cloud storage have the ability to generate their own API keys and increase security through the use of signatures.

Customers generate API keys and secrets using https://manage.signiant.com.

The secret and key are used to generate a signature that is used to secure requests to Web Transfer API using cloud storage. "singature_generators" contains sample code to show how to generate a signature using a variety of languages.
