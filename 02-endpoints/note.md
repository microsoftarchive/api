## Note

A note is a large text blobs belonging to tasks.


### Get the Notes for a Task or List

    GET a.wunderlist.com/api/v1/notes

#### Params

name      | type    | notes
:---------|:--------|:------------
task_id   | integer | **required**

or

name      | type    | notes
:---------|:--------|:------------
list_id   | integer | **required**


#### Response

    Status: 200

    json
    [
      {
        "id": 1,
        "task_id": 1234,
        "content": "Hey there",
        "created_at": "2013-08-30T08:36:13.273Z",
        "updated_at": "2013-08-30T08:36:13.273Z",
        "revision": 999
      }
    ]

### Get a specific note

    GET a.wunderlist.com/api/v1/notes/:id

#### Response

    Status: 200

    json
    {
      "id": 1,
      "task_id": 1234,
      "content": "Hey there",
      "created_at": "2013-08-30T08:36:13.273Z",
      "updated_at": "2013-08-30T08:36:13.273Z",
      "revision": 999
    }

### Create a note

    POST a.wunderlist.com/api/v1/notes

#### Data

name      | type    | notes
:---------|:--------|:------------
task_id   | integer | **required**
content   | string  | **required**

#### Request body example

    json
    {
      "task_id": 1234,
      "content": "Hey there"
    }

#### Response

    Status 201

    json
    {
      "id": 1,
      "task_id": 1234,
      "content": "Hey there",
      "created_at": "2013-08-30T08:36:13.273Z",
      "updated_at": "2013-08-30T08:36:13.273Z",
      "revision": 999
    }

### Update a note by overwriting properties

    PATCH a.wunderlist.com/api/v1/notes/:id

#### Data

name      | type    | notes
:---------|:--------|:------------
revision  | integer | **required**
content   | string | **required**

#### Request body example

    json
    {
      "revision": 999,
      "content": "Hallo",
    }

#### Response

    Status 200

    json
    {
      "id": 1,
      "task_id": 1234,
      "content": "Hey there",
      "created_at": "2013-08-30T08:36:13.273Z",
      "updated_at": "2013-08-30T08:36:13.273Z",
      "revision": 1000
    }

### Delete a note

    DELETE a.wunderlist.com/api/v1/notes/:id

#### Params

name      | type    | notes
:---------|:--------|:------------
revision  | integer | **required**

#### Response

    Status 204
