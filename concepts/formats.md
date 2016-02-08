## Formats

Every request and response in our API is transmitted in [JSON](http://www.json.org)—JavaScript Object Notation. It’s simple to use and implementations of JSON are widely available.  Where you see `Data` in these documents for POST, PATCH, and PUT requests, you must send data as JSON in the body of your request.

For example creating a task:

    POST a.wunderlist.com/api/v1/tasks

    {
      "list_id": 12345,
      "title": "Hallo",
      "assignee_id": 123,
      "completed": true,
      "due_date": "2013-08-30",
      "starred": false
    }

### Content-Type

All requests that POST, PATCH, or PUT JSON must set a `Content-Type` header with a value of `application/json`. Not setting this header or setting it to a different value will result in an error.

### Encoding

All requests must be encoded using UTF-8. All responses are UTF-8.

### Date and Time Format

All dates and times in the Wunderlist API are formatted as ISO-8601 strings. All times are provided as UTC. For example: `2013-10-09T23:34:11Z`

### Error Responses

Error responses are transmitted as an `error` dictionary and contain at least `type`, `translation_key`, and `message` attributes.

#### 401 Unauthorized

    {
      "error": {
        "type": "unauthorized",
        "translation_key": "api_error_unauthorized",
        "message": "You are not authorized."
      }
    }

#### 404 Not Found

    {
      "error": {
        "type": "not_found",
        "translation_key": "api_error_not_found",
        "message": "The resource you requested could not be found."
      }
    }

#### 400 Bad Request

Additional attributes may be sent with some errors. In particular, for bad requests with a `message` of `Missing parameter.`, the missing parameters along with messages indicating the problem are provided.

    {
      "error": {
        "type": "missing_parameter",
        "translation_key": "api_error_missing_params",
        "message": "Missing parameter.",
        "list_id": ["required", "can't be blank"]
      }
    }
