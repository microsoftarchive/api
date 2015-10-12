## User

All info related to the currently signed in user.

### Fetch the currently logged in user

    GET a.wunderlist.com/api/v1/user

#### Response

    Status: 200

    json
    {
      "id": 6234958,
      "name": "BENCHMARK",
      "email": "benchmark@example.com",
      "created_at": "2013-08-30T08:25:58.000Z",
      "revision": 1
    }

### Fetch the users this user can access

    GET a.wunderlist.com/api/v1/users

#### Params

name      | type    | notes
:---------|:--------|:------------
list_id   | integer | optional, restricts the list of returned users to only those who have access to a particular list

#### Response

    Status: 200

    json
    [
      {
        "id": 6234958,
        "name": "BENCHMARK",
        "email": "benchmark@example.com",
        "created_at": "2013-08-30T08:25:58.000Z",
      }
    ]