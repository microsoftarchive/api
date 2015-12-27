## Webhook

A webhook sends notifications when a list is updated.


### Get all webhooks for a list

    GET a.wunderlist.com/api/v1/webhooks

#### Params

name      | type    | notes
:---------|:--------|:------------
list_id   | integer | **required**

#### Response

    Status: 200

    json
    [
      {
        "id": 62,
        "list_id": 105743947,
        "membership_id": 49876097,
        "membership_type": "Membership",
        "url": "https:/yourhost.com/foo",
        "processor_type": "generic",
        "configuration": "",
        "created_at": "2015-03-03T15:32:09.272Z",
        "updated_at": "2015-03-03T15:32:09.272Z"
      }
    ]

### Create a Webhook

    POST a.wunderlist.com/api/v1/webhooks

#### Data

name            | type    | notes
:---------------|:--------|:------------
list_id         | integer | **required**
url             | string  | **required** maximum length is 255 characters
processor_type  | string  | **required**
configuration   | string  | **required** can be ""

#### Request body example

    json
    {
      "list_id": 105743947,
      "url":"https://foo.bar.chadfowler.com/struts/asdf.do",
      "processor_type":"generic",
      "configuration":""
    }

#### Response

    Status: 201

    json
    {
      "id": 105743947,
      "created_by_id": 6234958,
      "processor_type": "generic",
      "url": "https://foo.bar.chadfowler.com/struts/asdf.do",
      "created_at": "2014-08-30T08:36:13.273Z",
      "configuration": ""
    }

### Delete a webhook permanently

    DELETE a.wunderlist.com/api/v1/webhooks/:id

#### Params

name      | type    | notes
:---------|:--------|:------------
revision  | integer | **required**

#### Response

    Status 204


### See Also

  - [membership](endpoints/membership.md) - determine list ownership, members, and whether the list is pending or accepted
