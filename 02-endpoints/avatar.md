## Avatar

User avatars of different sizes can be fetched or loaded inline in HTML.

### Show the avatar of a user

    GET a.wunderlist.com/api/v1/avatar

name              | type    | notes
:-----------------|:--------|:------------
user_id|integer|**required**
size|integer|**optional**, values: 25, 28, 30, 32, 50, 54, 56, 60, 64, 108, 128, 135, 256, 270, 512 and original
fallback|boolean|**optional**

#### Response

    302 Found

This request will redirect you to an url for the avatar of the given user based on the `user_id`, if there is no avatar it will redirect a default avatar image.

**Info:** You don't need to send an `X-Access-Token` for this request.

If you add the optional parameter `size` to the request it will redirect to an avatar with the given `size`.

By adding the optional parameter `fallback` with the value `false` to the request, you will not be redirected to our fallback avatars. If there is no custom avatar uploaded for the given `user_id` it will respond with a `204 No Content` and an empty body.