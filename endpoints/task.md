## Task

Tasks are children of lists.

### Get Tasks for a List

    GET a.wunderlist.com/api/v1/tasks

#### Params

name              | type    | notes
:-----------------|:--------|:------------
list_id           | integer | **required**

#### Response

    Status: 200

    json
    [
      {
        "id": 409233670,
        "assignee_id": 12345,
        "created_at": "2013-08-30T08:36:13.273Z",
        "created_by_id": 6234958,
        "due_date": "2013-08-30",
        "list_id": 123,
        "revision": 1,
        "starred": true,
        "title": "Hello"
      }
    ]

### Get Completed Tasks

    GET a.wunderlist.com/api/v1/tasks

#### Params

name              | type    | notes
:-----------------|:--------|:------------
completed         | boolean | **required**
list_id           | integer  | **required**

#### Response

    Status: 200

    json
    [
      {
        "id": 409233670,
        "assignee_id": 12345,
        "created_at": "2013-08-30T08:36:13.273Z",
        "created_by_id": 6234958,
        "due_date": "2013-08-30",
        "list_id": 123,
        "revision": 1,
        "starred": true,
        "title": "Hello",
        "completed_at": "2013-08-30T08:36:13.273Z",
        "completed_by_id": 123
      }
    ]

## Get a specific task

    GET a.wunderlist.com/api/v1/tasks/:id

### Response

    Status: 200

    json
    {
      "id": 409233670,
      "assignee_id": 12345,
      "created_at": "2013-08-30T08:36:13.273Z",
      "created_by_id": 6234958,
      "due_date": "2013-08-30",
      "list_id": 123,
      "revision": 1,
      "starred": true,
      "title": "Hello"
    }

### Create a task

    POST a.wunderlist.com/api/v1/tasks

#### Data

name              | type    | notes
:-----------------|:--------|:------------
list_id           | integer | **required**
title             | string  | **required**, maximum length is 255 characters
assignee_id       | integer
completed         | boolean
recurrence_type   | string  | valid options: "day", "week", "month", "year", must be accompanied by `recurrence_count`
recurrence_count  | integer | must be >= 1, must be accompanied by `recurrence_type`
due_date          | string  | formatted as an ISO8601 date
starred           | boolean

#### Request body example

    json
    {
      "list_id": -12345,
      "title": "Hallo",
      "assignee_id": 123,
      "completed": true,
      "due_date": "2013-08-30",
      "starred": false
    }

#### Response

    Status 201

    json
    {
      "id": 409233670,
      "assignee_id": 123,
      "created_at": "2013-08-30T08:36:13.273Z",
      "created_by_id": 6234958,
      "due_date": "2013-08-30",
      "list_id": -12345,
      "revision": 1,
      "starred": false,
      "title": "Hello"
    }

### Update a task by overwriting properties

    PATCH a.wunderlist.com/api/v1/tasks/:id

#### Data

name              | type          | notes
:-----------------|:--------------|:------------
revision          | integer       | **required**
list_id           | integer       | can be given to move the Task into a different List
title             | string        | maximum length is 255 characters
assignee_id       | integer
completed         | boolean
recurrence_type   | string        | valid options: "day", "week", "month", "year", must be accompanied by `recurrence_count`
recurrence_count  | integer       | must be >= 1, must be accompanied by `recurrence_type`
due_date          | string        | formatted as an ISO8601 date
starred           | boolean
remove            | array[string] | an array of attributes to delete from the task, e.g. 'due_date'

#### Request body example

    json
    {
      "revision": 999,
      "title": "Hallo",
      "completed": true,
      "due_date": "2013-08-30",
      "starred": false,
      "remove": ["assignee_id"]
    }

#### Response

    Status 200

    json
    {
      "id": 409233670,
      "created_at": "2013-08-30T08:36:13.273Z",
      "created_by_id": 6234958,
      "due_date": "2013-08-30",
      "list_id": -12345,
      "revision": 1001,
      "starred": false,
      "title": "Hello"
    }

### Delete a task

    DELETE a.wunderlist.com/api/v1/tasks/:id

#### Params

name              | type    | notes
:-----------------|:--------|:------------
revision          | integer | **required**

#### Response

    Status 204
