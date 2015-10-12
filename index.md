## Introduction

The Wunderlist API provides REST-based storage and synchronization of a user’s lists across multiple platforms and devices.

The primary things you’ll need to use it are an understanding of our data model, how we [version individual entities](documentation/concepts/revisions) in a user’s data, the [formats we use for transmission](documentation/concepts/formats), and a set of [OAuth credentials](documentation/concepts/authorization).

### Support

Each page of this documentation has a Disqus comment box for questions and feedback. You can also reach us at [support@wunderlist.com](mailto:support@wunderlist.com) if you need help.


### Compatibility

This API *will* evolve rapidly and future versions will add new endpoints and parameters. To provide a sane experience, the API is versioned. Within a version, the behavior and return values of the API will not change from currently documented behavior and return values. As well, the API and its data payloads are designed so that new parameters and return values can be added at any time.

To provide the best experience, a well-behaved Wunderlist API client must not send undocumented parameters as part of their request. These parameters could collide with a future version of the API. As well, a Wunderlist API client must accept and ignore any additional keys that it doesn’t handle in a response.


### Security

It should go without saying, but all requests must be made using a secure connection. We support a minimum of TLS 1.0. We also recommend that you use certificate pinning in clients that you ship and which may operate on untrusted public networks.  
