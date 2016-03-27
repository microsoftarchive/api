## Reminder

The reminder for a task.

### Get Reminders for a Task or List

    GET a.wunderlist.com/api/v1/reminders

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
        "id": 123456,
        "date": "2013-08-30T08:29:46.203Z",
        "task_id": 123445,
        "revision": 1,
        "type": "reminder",
        "created_at": "2013-08-30T08:29:46.203Z",
        "updated_at": "2013-08-30T08:29:46.203Z"
      }
    ]

### Create a Reminder

    POST a.wunderlist.com/api/v1/reminders

#### Data

name                   | type    | notes
:----------------------|:--------|:------------
task_id                | integer | **required**
date                   | string  | **required**
created\_by\_device\_udid | string  | **optional**


#### Request body example

    json
    {
      "task_id": 59191,
      "date": "2013-08-30T08:29:46.203Z",
      "created_by_device_udid": "same-udid-on-device-register"
    }

**Notes:** The `created_by_device_udid` parameter is optional, but can be set to not schedule any reminder push notification for that device and that newly created reminder. This is mostly used by iOS, because they schedule a local reminder as well to have offline support.

#### Response

    Status: 201

    json
    [
      {
        "id": 20000,
        "date": "2014-05-30T08:29:46.203Z",
        "task_id": 59191,
        "revision": 1,
        "created_at": "2014-04-30T08:29:46.203Z",
        "updated_at": "2014-04-30T08:29:46.203Z"
      }
    ]

### Update a Reminder

    PATCH a.wunderlist.com/api/v1/reminders/:id

#### Data

name              | type    | notes
:-----------------|:--------|:------------
id                | integer | **required**
date              | string  | **required**
revision          | integer | **required**

#### Request body example

    json
    {
        "revision": 2,
        "date": "2015-06-30T08:29:46.203Z"
    }

#### Response

    Status: 200

    json
    {
        "id": 2000,
        "date": "2015-06-30T08:29:46.203Z",
        "task_id": 59191,
        "revision": 3,
        "created_at": "2014-04-30T08:29:46.203Z",
        "updated_at": "2014-04-30T08:29:46.203Z"
    }

### Delete a Reminder

    DELETE a.wunderlist.com/api/v1/reminders/:id

#### Params

name              | type    | notes
:-----------------|:--------|:------------
revision          | integer | **required**

#### Response

    Status: 204
