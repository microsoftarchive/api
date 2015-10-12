## Subtask

Subtasks are children of tasks

### Get Subtasks for a Task or List

    GET a.wunderlist.com/api/v1/subtasks

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
        "id": 409233670,
        "task_id": 123,
        "created_at": "2013-08-30T08:36:13.273Z",
        "created_by_id": 123456,
        "revision": 1,
        "title": "Hello"
      }
    ]

### Get Completed Subtasks

    GET a.wunderlist.com/api/v1/subtasks

#### Params

name              | type    | notes
:-----------------|:--------|:------------
completed         | boolean | **required**
list_id           | integer | **required**

or

name              | type    | notes
:-----------------|:--------|:------------
completed         | boolean | **required**
task_id           | integer | **required**

#### Response

    Status: 200

    json
    [
      {
        "id": 409233670,
        "task_id": 123,
        "created_at": "2013-08-30T08:36:13.273Z",
        "created_by_id": 123456,
        "revision": 1,
        "completed": true,
        "completed_at": "2013-08-30T08:36:13.273Z",
        "title": "Hello"
      }
    ]

### Get a specific subtask

    GET a.wunderlist.com/api/v1/subtasks/:id

#### Response

    Status: 200

    json
    {
      "id": 409233670,
      "task_id": 123,
      "created_at": "2013-08-30T08:36:13.273Z",
      "created_by_id": 123456,
      "revision": 1,
      "title": "Hello"
    }

### Create a subtask

    POST a.wunderlist.com/api/v1/subtasks

#### Data

name              | type    | notes
:-----------------|:--------|:------------
task_id           | integer | **required**
title             | string  | **required**, maximum length is 255
completed         | boolean |

#### Request body example

    json
    {
      "task_id": 12345,
      "title": "Hallo",
      "completed": false
    }

#### Response

    Status 201

    json
    {
      "id": 409233670,
      "created_at": "2013-08-30T08:36:13.273Z",
      "created_by_id": 6234958,
      "task_id": 12345,
      "revision": 1,
      "title": "Hello"
    }

### Update a subtask by overwriting properties

    PATCH a.wunderlist.com/api/v1/subtasks/:id

#### Data

name              | type    | notes
:-----------------|:--------|:------------
revision          | integer | **required**
title             | string  | maximum length is 255
completed         | boolean |

#### Request body example

    json
    {
      "revision": 999,
      "title": "Hallo",
      "completed": true
    }

#### Response

    Status 200

    json
    {
      "id": 409233670,
      "created_at": "2013-08-30T08:36:13.273Z",
      "created_by_id": 6234958,
      "task_id": 12345,
      "revision": 1001,
      "completed": true,
      "completed_at": "2013-08-30T08:36:13.273Z",
      "title": "Hallo"
    }

### Delete a subtask

    DELETE a.wunderlist.com/api/v1/subtasks/:id

#### Params

name              | type    | notes
:-----------------|:--------|:------------
revision          | integer | **required**

#### Response

    Status 204