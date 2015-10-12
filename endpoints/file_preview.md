## File Previews

A file preview is an image thumbnail for a file.

### Get a Preview of a specific File

The preview endpoint will generate a preview image on-demand for the given file. This endpoint **only** works with images for now. There are a bunch of image types supported to generate a preview from:

* `image/gif`
* `image/jpeg`
* `image/jpg`
* `image/pjpeg`
* `image/png`
* `image/svg+xml`
* `image/tiff`

#### Endpoint

    GET a.wunderlist.com/api/v1/previews

#### Params

name | type | values | notes|
-----|------|--------|-------
file_id|integer||**required**
platform|string|`mac`, `web`, `windows`, `iphone`, `ipad`, `android`|**optional**
size|string|`nonretina`, `retina`|**optional**

#### Response

**On Success:**

    200 OK

    json
    {
      "url": "http://uploads-s3-wunderlist-production.com/preview-43ht43-file.md",
      "size": "420x420",
      "expires_at": "2013-08-02T11:58:55Z",
      "type": "preview"
    }


**On Failure:**

    400 Bad Request

    json
    {
      "errors": ["bad request"]
    }

**Info:** The response in a failure case can differ from the given one.