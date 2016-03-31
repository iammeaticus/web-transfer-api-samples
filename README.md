# Getting Started
These samples to show how to integrate the Signiant Web Transfer API into a web application. The Signiant Web Transfer API supports transfers (upload and download) to / from: 
* Amazon S3
* Microsoft Azure
* Local storage on your network

# API Key
You will require an API key to transfer files. 

If you are transferring to local storage, you can get an API key from https://developer.mediashuttle.com

If you are transferring to cloud storage you can request one from http://info.signiant.com/flight-Free-Trial_1.html

# API Documentation
The JavaScript API.pdf file contains the API documentation for the Web Transfer API. Version 2 is nearly 100% backwards compatible to v1. 

## Loading Transfer API Version 2
Change 

`<script src="https://developer.mediashuttle.com/transfer/js" type="text/javascript" id="ms-api" api-key="INSERT_API_KEY_HERE"></script>` 

to 

`<script src="https://updates.signiant.com/javascript-api/2.5.2/transferapi.min.js" type="text/javascript"></script>`

to use the version 2 web transfer API.

Transfer API widgets are referenced by:

`<link rel="stylesheet" href="https://updates.signiant.com/javascript-api/2.5.2/widgets/download/mediashuttledownload.css"></link>`

`<link rel="stylesheet" href="https://updates.signiant.com/javascript-api/2.5.2/widgets/transferProgress/mediashuttletransferprogress.css"></link>`

`<link rel="stylesheet" href="https://updates.signiant.com/javascript-api/2.5.2/widgets/draganddrop/mediashuttlednd.css"></link>`

`<script src="https://updates.signiant.com/javascript-api/2.5.2/widgets/draganddrop/mediashuttlednd.js" type="text/javascript"></script>`

`<script src="https://updates.signiant.com/javascript-api/2.5.2/widgets/download/mediashuttledownload.js" type="text/javascript"></script>`

`<script src="https://updates.signiant.com/javascript-api/2.5.2/widgets/transferProgress/mediashuttletransferprogress.js" type="text/javascript"></script>`

The API Key is now provided to the Transfer Object directly, rather than through the “<script>” tag. To specify an API key to use for a transfer call the following method on an Upload or Download object:

```javascript
var upload = new Signiant.Mst.Upload();
upload.setApiKey('abc123');
 
var download = new Signiant.Mst.Download();
download.setApiKey('abc123');`
```

Note that this replaces the line:
`transferObject.setProperty('com.signiant.interactivetransfer.engine.api_key', 'YOUR_API_KEY');`
that may be present in your code.

# Changes
### Transfer API v2.5 - January 2016
* Drag and drop is now supported with the drag and drop widget. Improved error handling when the browser cannot communicate with the app.

### TAPI v2.4 - December 2015
* Improved the reliability of the Transfer API. 

### TAPI v2.3 - November 2015
* The transfer API will now install the Mac version of the Signiant App on Mac operating systems. 

### TAPI v2.2 - October 22 2015
* Drag and drop support now enabled for use with the drag and drop widget.

# Known Issues in Transfer API v2
* setLogLevel() only enables server side logging
* File injection is currently not detected, associated events will not be generated
* Queued transfers currently do not generate an TRANSFER_QUEUED event

# Deprecated Methods in Transfer API v2
* isIEProtectedModeOn()

# Security
Signiant Web Transfer API customers using cloud storage have the ability to generate their own API keys and increase security through the use of signatures.

Customers generate API keys and secrets using https://manage.signiant.com. 

The secret and key are used to generate a signature that is used to secure requests to Web Transfer API using cloud storage. "singature_generators" contains sample code to show how to generate a signature using a variety of languages.