## Positions

A list of ordered, unique integers related to a users's lists or a
list's tasks or a task's subtasks.


### Determining Order

Positions are almost completely docoupled from the resource they refer to.
Order is determined by the order of the resources' ids in the "values" array on
the positions object. This leads to two possibilities:

* An id in the values array refers to a resource that does not exist
* Ids of resources which **do** exist do not appear in the values array

To determine the order of resources the following convention shall be followed:

* Existing resources follow the order of their ids in the "values" array
* Ids in the "values" array which do not refer to an existing resource are simply ignored
* Existing resources with ids that do not appear in the values array appear
  at the end ordered by id ASC and then local id ASC.


### Get Positions for a user's lists

    GET a.wunderlist.com/api/v1/list_positions

#### Response

    Status: 200

    json
    [
      {
        "id": 131232,
        "values": [123, 234, 345, 456],
        "revision": 1,
        "type": "list_position"
      }
    ]

### Get a specific list position

    GET a.wunderlist.com/api/v1/list_positions/:id

#### Response

    Status: 200

    json
    {
      "id": 131232,
      "values": [123, 234, 345, 456],
      "revision": 1,
      "type": "list_position"
    }

### Update Positions for a user's lists

    PUT or PATCH a.wunderlist.com/api/v1/list_positions/:id

#### Data

name      | type           | notes
:---------|:---------------|:------------
values    | array[integer] | **required** - an ordered array of list ids
revision  | integer        | **required**

#### Request body example

    json
    {
      "values": [4567, 4568, 9876, 234],
      "revision": 123
    }

#### Response

    Status: 200

    json
    {
      "id": 34234234,
      "values": [123, 234, 345, 456, 321],
      "revision": 124,
      "list_id": 34234234,
      "type": "list_position"
    }

### Get Positions for a list's tasks

    GET a.wunderlist.com/api/v1/task_positions

#### Params

name      | type    | notes
:---------|:--------|:------------
list_id   | integer | **required**

#### Response

    Status: 200

    json
    [
      {
        "id": 34234234,
        "values": [123, 234, 345, 456],
        "revision": 1,
        "list_id": 34234234,
        "type": "task_position"
      }
    ]

### Get a specific task position

    GET a.wunderlist.com/api/v1/task_positions/:id

#### Response

    Status: 200

    json
    {
      "id": 34234234,
      "values": [123, 234, 345, 456],
      "revision": 1,
      "list_id": 34234234,
      "type": "task_position"
    }

### Update Positions for a list's tasks

    PUT or PATCH a.wunderlist.com/api/v1/task_positions/:id

#### Data

name      | type           | notes
:---------|:---------------|:------------
values    | array[integer] | **required**
revision  | integer        | **required**

#### Request body example

    json
    {
      "values": [4567, 4568, 9876, 234],
      "revision": 1
    }

#### Response

    Status: 200

    json
    {
      "id": 34234234,
      "values": [123, 234, 345, 456, 321],
      "revision": 1,
      "list_id": 34234234,
      "type": "task_position"
    }

### Get Positions for a task's subtasks

    GET a.wunderlist.com/api/v1/subtask_positions

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
        "id": 34234234,
        "values": [123, 234, 345, 456],
        "revision": 1,
        "task_id": 34234234,
        "type": "subtask_position"
      }
    ]

## Get a specific subtask position

    GET a.wunderlist.com/api/v1/subtask_positions/:ids

### Response

    Status: 200

    json
    {
      "id": 34234234,
      "values": [123, 234, 345, 456],
      "revision": 2,
      "task_id": 34234234,
      "type": "subtask_position"
    }

## Update Positions for a task's subtasks

    PUT or PATCH a.wunderlist.com/api/v1/subtask_positions/:id

### Data

name      | type           | notes
:---------|:---------------|:------------
values    | array[integer] | **required**
revision  | integer        | **required**

#### Request body example

    json
    {
      "values": [4567, 4568, 9876, 234],
      "revision": 1
    }

### Response

    Status: 200

    json
    {
      "id": 34234234,
      "values": [123, 234, 345, 456, 321],
      "revision": 2,
      "list_id": 34234234,
      "type": "task_position"
    }
