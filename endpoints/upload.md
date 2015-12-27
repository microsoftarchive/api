## Upload

The first resource that needs to be created to upload a file is the [Upload](endpoints/upload.md) resource. After the upload
is finished you need to create a new [File](endpoints/file.md) resource that will published via real time to
all the other members of the [List](endpoints/list.md) you are creating the [File](endpoints/file.md) in.

Here are the single steps you need to process to finish a file upload.

### Step #1: Create a new Upload

    POST a.wunderlist.com/api/v1/uploads

#### Data

name | type | notes
-----|------|------
content_type|string|**required**
file_name|string|**required**
file_size|integer|**required**
part_number|integer|**optional**
md5sum|string|**optional**

#### Response

    201 Created

    json
    {
      "id": 2000,
      "user_id": 1337,
      "state": "new",
      "type": "upload",
      "expires_at": "2014-04-30T14:44:48Z",
      "part": {
        "url": "https://s3.amazonawas.com/...?partNumber=1&uploadId=something",
        "date": "Wed, 30 Apr 2014 14:44:48 UTC +00:00",
        "authorization": "AWS SOME-KEY-HERE:SOME-SIGNATURE-HERE"
      }
    }

**Info:** Creating a new `Upload` resource will automatically initiate a multipart
upload on Amazon and will give you the needed information for the first part of the chunked
upload.

**Attention:** You need to **force** an empty string "" for the header `Content-Type` in your `PUT` request, otherwise Amazon will reject the request because of an invalid signature.

### Step #2: Fetching new parts for the chunked upload

If you need more than one part to upload the new file you need to call the following
endpoint to get another one.

    GET a.wunderlist.com/api/v1/uploads/:id/parts?part_number=2

#### Params

name | type | notes
-----|------|------
id|integer|**required**
part_number|integer|**required**
md5sum|string|**optional**

#### Response

    200 OK

    json
    {
      "id": 2000,
      "user_id": 1337,
      "state": "new",
      "type": "upload",
      "expires_at": "2014-04-30T14:44:48Z",
      "part": {
        "url": "https://s3.amazonawas.com/...?partNumber=2&uploadId=something",
        "date": "Wed, 30 Apr 2014 14:44:48 UTC +00:00",
        "authorization": "AWS SOME-KEY-HERE:SOME-SIGNATURE-HERE"
      }
    }

**Info:** The `part_number` attribute always starts with `1`, never with `0`. The `expires_at` date represents the lifetime of the given `part`.

After receiving the needed information and credentials to upload your first part to the given Amazon URL you need to set the following headers to be successful.

* `Content-Type` with an empty string.
* `Authorization` with the "authorization" string of the `part`.
* `x-amz-date` with the "date" string of the `part`.

### Step #3: Mark the upload as finished

    PATCH a.wunderlist.com/api/v1/uploads/:id

#### Data

name | type | values | notes
-----|------|--------|------
id|integer||**required**
state|string|`finished`|**required**

#### Request body example

    200 OK

    json
    {
      "state": "finished"
    }

#### Response

**On Success:**

    200 OK

    json
    {
      "id": 2000,
      "user_id": 1337,
      "state": "finished",
      "type": "upload"
    }

**Info:** You **must** set the state to `finished` once the upload parts are finished.

**On Failure:**

This case can happen if you try to mark the upload as finished without uploading any parts.

    400 Bad Request

    json
    {
      "errors": ["state", "There are no parts upload to finish it"]
    }

**Info:** If an upload fails, simply create a new upload. Failed uploads will be automatically
garbage collected by the API.
