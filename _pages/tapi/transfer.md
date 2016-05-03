---
layout: page
title: Transfer
permalink: tapi/v2/transfer
---

## Signiant.Mst.Transfer
This class should not be instantiated. It is extended by the Download or Upload class.

# Methods

## cancel 
Cancels an in-progress upload or download. This method returns as soon as the Signiant App has been successfully asked to cancel the transfer. Further notifications related to the progress of the transfer can be retrieved by registering event listeners with the subscribeForBasicEvents and subscribeForTransferProgress functions.  If a transfer is not in progress, an exception is thrown.

## clearServerList
Removes all the servers that exist in the transfer configuration property for the source/destination server.

## deleteProperty
Deletes the transfer configuration property specified by name.  An exception is thrown if name is undefined, or if the data-type of name is not String.

## getDestinationDir
Returns the location of the destination directory where downloaded content will be stored, from the download configuration properties.

## getLastError
Returns the detailed error code, as reported by the Media Shuttle Transfer Plug-in, for the latest error condition encountered during an upload or download. This error code can be used to further hone in on the exact error that occurred in the plug-in.

## getLogLevel
Retrieve the current upload and download log level.
* INFO - basic logging level (default)
* DEBUG - debug logging level

## getProperty
Returns the value of the transfer configuration property specified by name. An exception is thrown if name is undefined, or if the data-type of name is not String.

## getTransferId
Returns the unique identifier for the transfer. Every upload or download has a unique identifier that you can use to distinguish one transfer from another.

## getTrustedCA
Returns the value of the trusted CA certificate configuration property.

## getServer
Returns the list of all servers that exist in the transfer configuration property for the source/destination server.

## getFileEncryption
Returns a JSON object with the current key and initialization vector set for end-to-end file encryption. If file encryption is not set, undefined is returned. See the End-to-End File Encryption section in the Developer Guide for more details.

## getSubFolder
Returns the sub folder set for the upload or download. If a sub folder was not set undefined will be returned.

## getTargetFileName
Returns the target file name mapping for the upload or download. If a sub folder was not set undefined will be returned.

## resetTransferProperties
Clears all the configuration properties for the upload or download.

## setCredentials
Sets the credentials to be used for the transfer in the configuration properties.  An exception is thrown if username or password is undefined.

## setDestinationDir
Saves the location of the destination directory where downloaded content is stored, in the download configuration properties. An exception is thrown if destinationDir is undefined or an empty String.

## setJobNamePrefix
Sets the prefix of the name associated with an upload or download to the value specified in the value parameter. The remainder of the name will be a date/time stamp in numeric form. The name is useful for identifying Media Shuttle Transfer API uploads and downloads in a management Interface. The default value is MediaShuttleAPI_. The value is limited to 32 alphanumeric characters and underscores.  An exception is thrown if the value contains invalid characters or is undefined.

## setLogLevel
Enable and disable upload and download logging.
* INFO - basic logging level (default)
* DEBUG - debug logging level

## setProperty
Changes the value of a specific property in the transfer configuration of an upload or download.  An exception is thrown if the name or value are undefined, or if the data-type of name is not String.

## setServer
Add the specified server, with the specified relays, to the source/destination server configuration property. Every time a method is called, the supplied server is added to the existing list of source/destination servers for the transfer. To clear the existing list of servers, use the clearServerList method. An exception is thrown if server is undefined or is an empty String.

## setSubFolder 
Sets a sub folder set for the upload or download. On upload the sub folder will be prepended to the file and folders specified. The files and folders will be created on the target file system under the sub folder specified. In the download case the sub folder is prepended to the file names specified for download. In this case the files must exist in the specified by the sub folder.

## setTargetFileName
Set target file name allows a file being uploaded to be saved with a different name on the target storage system. The current implementation is limited to a single file. If multiple files or folders are specified for upload and a target file name is set the upload will not start.

## setTransferProperties
Overwrites all the transfer configuration properties with the supplied properties parameter.  An exception is thrown if properties is undefined or not a JSON object.

## setTrustedCA
Stores the supplied CA certificate in the transfer configuration properties. The supplied certificate must be a Base64 encoded DER certificate, enclosed between "-----BEGIN CERTIFICATE-----" and "-----END CERTIFICATE-----".  An exception is thrown, if trustedCACertificate is undefined, or empty, or if is not in the DER format, enclosed between "-----BEGIN CERTIFICATE-----" and "-----END CERTIFICATE-----".

## setFileEncryption
Enable end-to-end file encryption by specifying an encryption key and initialization vector. The values need to be supplied in a JSON object with the key and initialization vector. The format is : { 'key' : 'FFFF...', 'iv' : 'FFFF....' }. See the End-to-End File Encryption section in the Developer Guide for more details.

## subscribeForBasicEvents
Registers the supplied callbackFunc as the handler for basic events related to an upload or download. 

The following event types are classified as basic events:

* TRANSFER_STARTED
* PRE_TRANSFER_EVENT
* TRANSFER_CONNECTION_STATUS
* TRANSFER_QUEUED
* TRANSFER_PRE_FILE_EVENT
* TRANSFER_ERROR_EVENT
* TRANSFER_CANCEL_EVENT
* INJECTED_FILES_FOUND_EVENT
* INJECTED_DESTINATION_DIR_EVENT
* TRANSFER_COMPLETED

The callbackFunc is invoked with the following parameters:
Upload or Download transfer object (Object)
Event Type (String)
Message (String)
(Optional) Event-specific data. Based on the type of event, the callbackFunc will be invoked with a fourth parameter.
For further details see the table of Basic Event Types

## subscribeForTransferErrors
Registers the supplied callbackFunc as the handler for transfer error events related to an upload or download. 

The callbackFunc is invoked with the following parameters:
Upload or Download transfer object (Object)
Event Type (String)
Error Message (String)
(Optional) Name of configuration property that caused the error (String)
The Event Type supplied to the callbackFunc can have the following values, depending on the specific error condition:

* INCOMPLETE_USER_CREDENTIALS
* INVALID_CREDENTIALS
* SPECIFIED_FILE_DOES_NOT_EXIST
* DOWNLOAD_FILES_DO_NOT_EXIST
* NO_FOLDER_CHOSEN_FOR_DOWNLOAD
* INVALID_DESTINATION_DIRECTORY
* CONNECTION_FAILURE
* TRANSFER_ERROR_EVENT

The Error Type Table provides descriptions of the error types.

## subscribeForTransferProgress
Registers the supplied callbackFunc as the handler for transfer progress events related to an upload or	download. 

The callbackFunc is invoked with the following parameters:
Upload or Download transfer object (Object)
Bytes Sent/Received (Number)
Total Bytes to be transferred (Number)
Estimated Time Remaining, in seconds (Number)