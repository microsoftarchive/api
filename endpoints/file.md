## File

The first resource that needs to be created to upload a file is the [Upload](/documentation/endpoints/upload) resource. After the upload
is finished you need to create a new [File](/documentation/endpoints/file) resource that will published via real time to
all the other members of the [List](/documentation/endpoints/list) you are creating the [File](/documentation/endpoints/file) in.

### Get Files for a Task or List

    GET a.wunderlist.com/api/v1/files

#### Params

name | type | notes
-----|------|------
task_id|integer|**required**

or

name | type | notes
-----|------|------
list_id|integer|**required**

#### Response

    200 OK

    json
    [
      {
        "id": 123456,
        "url": "http://uploads-s3-wunderlist-production.com/43ht43-file.md",
        "task_id": 123,
        "list_id": 123,
        "user_id": 123,
        "file_name": "file.md",
        "content_type", "text/plain",
        "file_size": 1234124,
        "local_created_at": "2013-08-02T11:58:55.123Z",
        "created_at": "2013-08-02T11:58:55Z",
        "updated_at": "2013-08-02T11:58:55Z",
        "type": "file",
        "revision": 1
      }
    ]

### Get a specific File

    GET a.wunderlist.com/api/v1/files/:id

#### Response

    200 OK

    json
    {
      "id": 123456,
      "url": "http://uploads-s3-wunderlist-production.com/43ht43-file.md",
      "task_id": 123,
      "list_id": 123,
      "user_id": 123,
      "file_name": "file.md",
      "content_type", "text/plain",
      "file_size": 1234124,
      "local_created_at": "2013-08-02T11:58:55.123Z",
      "created_at": "2013-08-02T11:58:55Z",
      "updated_at": "2013-08-02T11:58:55Z",
      "type": "file",
      "revision": 1
    }

### Create a File

For creating files we have introduced the `:local_created_at` from comments again. This attribute will help us later to sort the files and comments in the right order. The field needs to be send in the following format: `2013-08-02T11:58:55.123Z`

    POST a.wunderlist.com/api/v1/files

#### Data

name | type | notes
-----|------|------
upload_id|integer|**required**
task_id|integer|**required**
local\_created\_at|datetime|**optional**

#### Response

    201 Created

    json
    {
      "id": 123456,
      "url": "http://uploads-s3-wunderlist-production.com/43ht43-file.md",
      "task_id": 123,
      "list_id": 123,
      "user_id": 123,
      "file_name": "file.md",
      "content_type", "text/plain",
      "file_size": 1234124,
      "local_created_at": "2013-08-02T11:58:55.123Z",
      "created_at": "2013-08-02T11:58:55Z",
      "updated_at": "2013-08-02T11:58:55Z",
      "type": "file",
      "revision": 1
    }

### Destroy a File

    DELETE a.wunderlist.com/api/v1/files/:id

#### Params

name | type | notes
-----|------|------
revision|integer|**required**

#### Response

**On Success:**

    204 No Content

**On Failure:**

    400 Bad Request

    json
    {
      "errors": ["bad request"]
    }
