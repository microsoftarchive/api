## Wunderlist API Documentation

The Wunderlist API provides REST-based storage and synchronization of a user’s lists across multiple platforms and devices.

The primary things you’ll need to use it are an understanding of our data model, how we [version individual entities](concepts/revisions.md) in a user’s data, the [formats we use for transmission](concepts/formats.md), and a set of [OAuth credentials](concepts/authorization.md).

<!-- START_TOC -->

### Concepts

* [Authorization](concepts/authorization.md)
* [Formats](concepts/formats.md)
* [Revisions](concepts/revisions.md)

### Endpoints

* [Avatar](endpoints/avatar.md)
* [File](endpoints/file.md)
* [File Preview](endpoints/file_preview.md)
* [Folder](endpoints/folder.md)
* [List](endpoints/list.md)
* [Membership](endpoints/membership.md)
* [Note](endpoints/note.md)
* [Positions](endpoints/positions.md)
* [Reminder](endpoints/reminder.md)
* [Root](endpoints/root.md)
* [Subtask](endpoints/subtask.md)
* [Task](endpoints/task.md)
* [Task Comment](endpoints/task_comment.md)
* [Upload](endpoints/upload.md)
* [User](endpoints/user.md)
* [Webhooks](endpoints/webhook.md)

### Tools

* [Wundlist.js SDK](tools/wunderlist.js.md)

<!-- END_TOC -->

### Support

You can report issues or ask questions via our [GitHub repository](https://github.com/wunderlist/api/issues). You can also reach us at [support@wunderlist.com](mailto:support@wunderlist.com).

### Compatibility

This API *will* evolve rapidly and future versions will add new endpoints and parameters. To provide a sane experience, the API is versioned. Within a version, the behavior and return values of the API will not change from currently documented behavior and return values. As well, the API and its data payloads are designed so that new parameters and return values can be added at any time.

To provide the best experience, a well-behaved Wunderlist API client must not send undocumented parameters as part of their request. These parameters could collide with a future version of the API. As well, a Wunderlist API client must accept and ignore any additional keys that it doesn’t handle in a response.


### Security

It should go without saying, but all requests must be made using a secure connection. We support a minimum of TLS 1.0. We also recommend that you use certificate pinning in clients that you ship and which may operate on untrusted public networks.  
