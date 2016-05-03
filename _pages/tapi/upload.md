---
layout: page
title: Upload
permalink: /tapi/v2/upload
---

### Signiant.Mst.Upload
This allows you to easily upload files to cloud storage or a local storage server using Signiant's acceleration. One Signiant.Mst.Upload object must be created per upload.

```javascript
//create a new upload Object
transferObject = new Signiant.Mst.Upload();
//set the default server
transferObject.setServer('us-east-1-am.cloud.signiant.com'); //see https://flight.support.signiant.com/customer/en/portal/articles/2173685 for cloud storage servers
transferObject.subscribeForTransferErrors(transferErrors);
transferObject.subscribeForBasicEvents(transferEvents);
transferObject.subscribeForTransferProgress(transferProgressCallback);
//setup the storage config options to upload to the right S3 bucket
transferObject.setStorageConfig('{"access-key":"'+YOUR_S3_ACCESS_KEY+'", "secret-key":"'+YOUR_S3_SECRET+'", "bucket":"'+YOUR_S3_BUCKET+'"}');
} 
//send the server the API key
transferObject.setApiKey(YOUR_API_KEY); //get an API key from 
transferObject.setProbeLB(true); //always set to true for Flight
```

# Methods

## clearFiles 
This will clear the files/folders specified in the filesArray parameter, from the list of files to be uploaded. The files/folders must be specified using their full paths in the filesArray parameter. An exception is thrown if the filesArray parameter is undefined or datatype of filesArray is not an Array.

```javascript
transferObject.clearFiles(filesArray);
```

## clearAllFiles
Clears all the files from the list of files to be uploaded.

```javascript
transferObject.clearAllFiles();
```

## chooseUploadFiles
This function launches the platform-specific file-chooser so that the user can select the files/folders to be uploaded.  Once the user has selected the desired files/folders the callbackFunction is invoked. If the user did not select any files/folders, the callbackFunc is not invoked.

```javascript
transferObject.chooseUploadFiles(callbackFunction);
```

returns

```
callbackFunction(eventType,selectedFiles)
```

selectedFiles is a JSON array of objects

```javascript
{ 
  "name":"upload.txt",
  "path":"/tmp/upload.txt",
  "isDirectory":"false",
  "size":"10190"
}
```

## setFilesToUpload
Starts the upload of the specified files/folders to the destination server.  If the specified API key is not valid, or if the Signiant App is not installed, an exception is thrown. This function simply notifies the Signiant App to begin the transfer, and then returns. Further notifications related to the state/progress of the transfer can be retrieved by registering event listeners with the subscribeForBasicEvents and subscribeForTransferProgress functions.