## Folder

A list may or may not belong to a folder.

### Get all Folders created by the the current User

    GET a.wunderlist.com/api/v1/folders

#### Response

    Status: 200

    json
    [
      {
        "id": 83526310,
        "title": "Personal Stuff",
        "list_ids": [1, 2, 3, 4],
        "created_at": "2013-08-30T08:29:46.203Z",
        "created_by_request_id": "5541b1d86e925e2dd7e5",
        "updated_at": "2013-08-30T08:29:46.203Z",
        "type": "folder",
        "revision": 10
      },
      ...
    ]

### Get a specific Folder

    GET a.wunderlist.com/api/v1/folders/:id

#### Response

    Status: 200

    json
    {
        "id": 83526310,
        "title": "Personal Stuff",
        "list_ids": [1, 2, 3, 4],
        "created_at": "2013-08-30T08:29:46.203Z",
        "created_by_request_id": "5541b1d86e925e2dd7e5",
        "updated_at": "2013-08-30T08:29:46.203Z",
        "type": "folder",
        "revision": 10
    } 

### Create a Folder

    POST a.wunderlist.com/api/v1/folders

#### Params

name      | type    | notes
:---------|:--------|:------------
title     | string  | **required** (maximum length is 255 characters)
list_ids  | array of integers | **required** (list of ids)

#### Request body example

    {
      "title": "My first Folder",
      "list_ids": [1, 2, 3, 4]
    }

**Attention:** The `list_ids` attribute keeps track of the Lists that are part of that Folder. The `list_ids` attribute doesn't reflect the order. If you add Lists to your folder you still need to sort the Lists via the `list_positions` feature to support clients without the Folder feature.

**Info:** The created Folder is automatically owned by the User who creates it. Only the owner of a Folder can actually see/request it.

#### Response


    Status: 200

    json
    {
        "id": 83526310,
        "title": "My first Folder",
        "list_ids": [1, 2, 3, 4],
        "created_at": "2013-08-30T08:29:46.203Z",
        "created_by_request_id": "5541b1d86e925e2dd7e5",
        "updated_at": "2013-08-30T08:29:46.203Z",
        "type": "folder",
        "revision": 1
    } 

### Update a Folder by overwriting properties

    PATCH a.wunderlist.com/api/v1/folders/:id

#### Params

name      | type    | notes
:---------|:--------|:---------
revision  | integer | **required**
title     | string  | **optional** (maximum length is 255 characters)
list_ids  | array of integers | **optional** (list of ids)

#### Request body example

    {
      "revision": 1000,
      "title": "My renamed Folder"
    }

#### Response

    Status 200

    {
      "id": 83526310,
      "title": "My renamed Folder",
      "list_ids": [1, 2, 3, 4],
      "created_at": "2013-08-30T08:29:46.203Z",
      "created_by_request_id": "5541b1d86e925e2dd7e5",
      "updated_at": "2013-08-30T08:29:46.203Z",
      "type": "folder",
      "revision": 2
    }

### Delete a Folder permanently

    DELETE a.wunderlist.com/api/v1/folders/:id

#### Params

name      | type    | notes
:---------|:--------|:---------
revision  | string  | **required**

#### Response

    Status 204

### Get Folder Revisions

    GET a.wunderlist.com/api/v1/folder_revisions

#### Response

    Status: 200

    [
      {
        "id": 83526310,
        "type": "folder_revision",
        "revision": 10
      },
      ...
    ]