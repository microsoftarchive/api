## Wunderlist.js SDK

The Wunderlist.js SDK is an IO module for easily accessing Wunderlist API
endpoints via node, io.js, or the browser.

### Installation

`npm install wunderlist`

### Basic Usage

#### Node/io.js

    var WunderlistSDK = require('wunderlist');
    var wunderlistAPI = new WunderlistSDK({
      'accessToken': 'a user access_token',
      'clientID': 'your client_id'
    });

    wunderlistAPI.http.lists.all()
      .done(function (lists) {
        /* do stuff */
      })
      .fail(function () {
        console.error('there was a problem');
      });

### Source

  [https://github.com/wunderlist/wunderlist.js](https://github.com/wunderlist/wunderlist.js)