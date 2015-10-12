## List

All tasks created in Wunderlist belong to a list.

### Get all Lists a user has permission to

    GET a.wunderlist.com/api/v1/lists

#### Response

    Status: 200

    json
    [
      {
        "id": 83526310,
        "created_at": "2013-08-30T08:29:46.203Z",
        "title": "Read Later",
        "list_type": "list",
        "type": "list",
        "revision": 10
      }
    ]

### Get a specific List

    GET a.wunderlist.com/api/v1/lists/:id

#### Response

    Status: 200

    json
    {
      "id": 83526310,
      "created_at": "2013-08-30T08:29:46.203Z",
      "title": "Read Later",
      "list_type": "list",
      "type": "list",
      "revision": 10
    }
<!-- 
### Get a List's Task Counts

    GET a.wunderlist.com/api/v1/lists/tasks_count

#### Params

name      | type    | notes
:---------|:--------|:------------
list_id   | integer | **required**

#### Response

    Status: 200

    json
    {
      "id": 83526310,
      "completed_count": 100,
      "uncompleted_count": 200,
      "type": "tasks_count"
    } -->

### Create a list

    POST a.wunderlist.com/api/v1/lists

#### Data

name      | type    | notes
:---------|:--------|:------------
title     | string  | **required.** maximum length is 255 characters

#### Request body example

    json
    {
      "title": "Hallo"
    }


#### Response

    Status: 201

    json
    {
      "id": 83526310,
      "created_at": "2013-08-30T08:29:46.203Z",
      "title": "Read Later",
      "revision": 1000,
      "type": "list"
    }

### Update a list by overwriting properties

    PATCH a.wunderlist.com/api/v1/lists/:id

#### Data

name      | type    | notes
:---------|:--------|:------------
revision  | integer | **required**
title     | string  | maximum length is 255 characters

#### Request body example

    json
    {
      "revision": 1000,
      "title": "Hallo"
    }

#### Response

    Status 200

    json
    {
      "id": 409233670,
      "revision": 1001,
      "title": "Hello",
      "type": "list"
    }

### Make a list public

    PATCH a.wunderlist.com/api/v1/lists/:id

#### Data

name      | type    | notes
:---------|:--------|:------------
revision  | integer | **required**
public    | boolean |

#### Request body example

    json
    {
      "revision": 1000,
      "public": true
    }


#### Response

    Status 200

    json
    {
      "id": 409233670,
      "revision": 1001,
      "public": true
    }

### Delete a list permanently

    DELETE a.wunderlist.com/api/v1/lists/:id

#### Params

name      | type    | notes
:---------|:--------|:------------
revision  | integer | **required**

#### Response

    Status 204

### See Also

  - [task](/documentation/endpoints/task) - get the tasks belonging to a given list
  - [membership](/documentation/endpoints/membership) - determine list ownership, members, and whether the list is pending or accepted
  - [positions](/documentation/endpoints/positions) - get the current order for a users' lists