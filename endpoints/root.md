## Root

Root is the top-level entity in the [sync hierarchy](concepts/revisions.md).

### Fetch the Root for the current User

    GET a.wunderlist.com/api/v1/root

#### Response

    Status: 200

    json
    {
      "id": 12345,
      "type": "root",
      "revision": 10,
      "user_id": 6234958
    }
