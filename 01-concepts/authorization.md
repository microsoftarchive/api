## Authorization

The Wunderlist API uses [OAuth2](http://oauth.net/2/) to allow external applications to request authorization to a user’s Wunderlist account without directly handling their password.

Developers must [register their application](https://developer.wunderlist.com/apps/new) before getting started. Registration assigns a unique client ID and client secret for your application’s use. After you have registered your application, you can let Wunderlist users authorize access to their account information from your application by getting an access token.

After a user has authorized your application and you have an access token, you can use it in Wunderlist API requests by setting the `X-Client-ID` and `X-Access-Token` HTTP request headers.

    X-Access-Token: OAUTH-TOKEN X-Client-ID: CLIENT-ID

As an example, in curl you can set the Authorization header like this:

    curl -H "X-Access-Token: OAUTH-TOKEN" -H "X-Client-ID: CLIENT-ID" https://a.wunderlist.com/api/v1/user

<div class="p2 rounded border border-red bg-transparent-red">
	<strong class="bold">Attention!</strong>
	Please note that setting the above mentioned headers is required to access protected resources on the Wunderlist API. OAuth2 is only used for obtaining user tokens.
</div>

### Web Server Application Integration

To integrate your third-party web server application with Wunderlist, use the following flow:


#### 1. Redirect users to request Wunderlist access

    https://www.wunderlist.com/oauth/authorize?client_id=ID&redirect_uri=URL&state=RANDOM

#### Parameters

Name | Type | Description
-----|------|--------------
`client_id`|`string` | **Required**. The Client ID you received from Wunderlist when you [registered your application](https://developer.wunderlist.com/apps/new).
`redirect_uri`|`string` | **Required**. The URL in your app where users will be sent after authorization. See details below about [redirect urls](#redirect-urls).
`state`|`string` | **Required**. An unguessable random string. It is used to protect against cross-site request forgery attacks.

#### 2. Wunderlist redirects back to your site

If the user accepts your request, Wunderlist will redirect to your `redirect_uri`
with a temporary code in a `code` parameter as well as the state you provided in
the previous step in a `state` parameter. If the states don't match, the request
has been created by a third party and the process should be aborted.

Exchange `code` for an access token:

    POST https://www.wunderlist.com/oauth/access_token

### JSON Data

Name | Type | Description
-----|------|---------------
`client_id`|`string` | **Required**. The client ID you received from Wunderlist when you [registered](https://developer.wunderlist.com/apps/new).
`client_secret`|`string` | **Required**. The client secret you received from Wunderlist when you [registered](https://developer.wunderlist.com/apps/new).
`code`|`string` | **Required**. The code you received as a response to [Step 1](#1-redirect-users-to-request-wunderlist-access).

### Response

A successful response will take the following form:

    {
      "access_token": "976d16a81ccf621a654fcc23193b09498b220e89eb72ced3"
    }

### Libraries

If you are developing a Rails app and are using omniauth, you can use the [omniauth-wunderlist strategy](https://rubygems.org/gems/omniauth-wunderlist) to managing redirects and code exchange for you.
