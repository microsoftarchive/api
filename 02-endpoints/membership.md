## Membership

A Membership is the join model between Users and Lists.


### Get Memberships for a List or the current User

    GET a.wunderlist.com/api/v1/memberships

#### Response

    Status: 200

    json
    [
      {
        "id": 26817784,
        "user_id": 6234958,
        "list_id": 83526257,
        "state": "pending",
        "type": "membership",
        "owner": true,
        "muted": false
      },
      {
        "id": -26817784,
        "user_id": -12345,
        "list_id": 83526257,
        "state": "accepted",
        "type": "membership",
        "owner": false,
        "muted": false
      }
    ]

### Add a Member to a List

    POST a.wunderlist.com/api/v1/memberships

#### Data

One of the following combinations:

name      | type    | notes
:---------|:--------|:------------
list_id   | integer | **required**
user_id   | integer | **required**
muted     | boolean |

or

name      | type    | notes
:---------|:--------|:------------
list_id   | integer | **required**
email     | string  | **required**
muted     | boolean |

#### Response

    Status: 201

    json
    {
      "id": -26817784,
      "user_id": 6234958,
      "list_id": 12345,
      "state": "pending",
      "type": "membership",
      "owner": false,
      "muted": false
    }

### Mark a Member as accepted

    PATCH a.wunderlist.com/api/v1/memberships/:id

#### Data

name      | type    | value    | notes
:---------|:--------|:---------|:------------
revision  | integer |          | **required**
state     | string  | accepted | **required**
muted     | boolean |          |

#### Response

    Status: 200

    json
    {
      "id": 26817784,
      "user_id": 6234958,
      "list_id": 1234,
      "state": "accepted",
      "type": "membership",
      "owner": false,
      "muted": false
    }

### Remove a Member from a List

    DELETE a.wunderlist.com/api/v1/memberships/:id

#### Data

name      | type    | notes
:---------|:--------|:------------
revision  | integer | **required**


#### Response

    Status: 204

### Reject an invite to a List

    DELETE a.wunderlist.com/api/v1/memberships/:id

#### Params

name      | type    | notes
:---------|:--------|:------------
revision  | integer | **required**

#### Response

    Status: 204

### See Also

  - [user](/documentation/endpoints/user) - get information about users