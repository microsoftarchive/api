## Task Comment

A task_comment is a comment that belongs to a task.

### Get the Comments for a Task or a List

    GET a.wunderlist.com/api/v1/task_comments

#### Params

name              | type    | notes
:-----------------|:--------|:------------
task_id           | integer | **required**

or

name              | type    | notes
:-----------------|:--------|:------------
list_id           | integer | **required**


#### Response

    Status: 200

    json
    [
      {
        "id": 1234,
        "task_id": 1234,
        "revision": 12,
        "text": "Hey there",
        "type": "task_comment",
        "created_at": "2013-08-30T08:36:13.273Z"
      }
    ]

### Get a specific Comment

    GET a.wunderlist.com/api/v1/task_comments/:id


#### Response

    Status: 200

    json
    {
      "id": 1234,
      "task_id": 1234,
      "revision": 12,
      "text": "Hey there",
      "type": "task_comment",
      "created_at": "2013-08-30T08:36:13.273Z"
    }

### Create a Comment

    POST a.wunderlist.com/api/v1/task_comments

#### Data

name              | type    | notes
:-----------------|:--------|:------------
task_id           | integer | **required**
text              | string  | **required**

#### Request body example

    json
    {
      "task_id": 1234,
      "text": "Hey there"
    }

#### Response

    Status: 201

    json
    {
      "id": 1234,
      "task_id": 1234,
      "revision": 12,
      "read": false,
      "text": "Hey there",
      "type": "task_comment",
      "created_at": "2013-08-30T08:36:13.273Z"
    }