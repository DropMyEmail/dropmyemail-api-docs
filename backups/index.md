---
layout: default
title:  "Accounts"
date:   2013-07-26 11:00:30
categories: accounts
---

## Backup API

Backup API allows you to manipulate email accounts for backing up.

## <a id="list"></a> List

List the email accounts for the user.

```
GET /v1/accounts
```

### Parameters

#### type

- all
- imap
- pop

default: all

#### sort

- email
- message_count
- storage
- created_at
- updated_at

default: email

##### direction

- asc
- desc

default: asc

### Scope
read

### Response

``` javascript
[{
    "id": 888,
    "host": "pop.mail.com",
    "protocol": "pop",
    "start_tls": true,
    "ssl": false,
    "port": 110,
    "msg_count": 1000,
    "storage": 200,
    "created_at": "2013-06-24T23:55:43.000Z",
    "updated_at": "2013-06-26T20:16:40.000Z",
    "email": "demo1@mail.com"
}, {
    "id": 889,
    "host": "pop.mail.com",
    "protocol": "pop",
    "start_tls": true,
    "ssl": false,
    "port": 110,
    "msg_count": 1000,
    "storage": 200,
    "created_at": "2013-06-24T23:55:43.000Z",
    "updated_at": "2013-06-26T20:16:40.000Z",
    "email": "demo2@mail.com"
}]
```

## <a id"show"></a> Get a single account

Get an email account for the user.

```
GET /v1/accounts/:id
```

### Scope
read

### Response

``` javascript
{
    "id": 888,
    "host": "pop.mail.com",
    "protocol": "pop",
    "start_tls": true,
    "ssl": false,
    "port": 110,
    "msg_count": 1000,
    "storage": 200,
    "created_at": "2013-06-24T23:55:43.000Z",
    "updated_at": "2013-06-26T20:16:40.000Z",
    "email": "demo@mail.com"
}
```

## <a id="create"></a> Add an email account

Add an email account for backing up.

```
POST /v1/accounts/
```

### Input parameters

#### email
- required
- string

The email account for backing up.

#### password
- required
- string

The password to the email account

#### host
- optional
- string
- hostname for the server

Eg: 'imap.mailserver.com'

#### protocol
- optional
- string
- use either 'imap' or 'pop'.

This is the supported protocol of the mail server.

Eg: 'imap'

#### start_tls
- optional
- boolean
- default: false

[Start TLS](http://en.wikipedia.org/wiki/STARTTLS) is a configuration setting of the mail server. Check if it is supported by the mail server.

Eg: true

#### ssl
- optional
- boolean
- default: false

[SSL](http://en.wikipedia.org/wiki/Email_encryption) is a configuration setting of the mail server. Check if it is supported by the mail server.

#### port
- optional
- integer

This is the port number that the mail server is listening to. Usually it is a [well known port number](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers).

### Scope
write

### Response

``` javascript
{
    "id": 888,
    "host": "pop.mail.com",
    "protocol": "pop",
    "start_tls": true,
    "ssl": false,
    "port": 110,
    "msg_count": 1000,
    "storage": 200,
    "created_at": "2013-06-24T23:55:43.000Z",
    "updated_at": "2013-06-26T20:16:40.000Z",
    "email": "demo@mail.com"
}
```

#### Special case for Gmail/Google Apps account

_Note: This part is not completed yet. But documented for your reference_

If the email account is a Gmail or Google Apps account, we need the user to grant us permission to access his account. It is done through Oauth.

We will return you an authorization url. First, the user has to be logged in to the same Gmail/Google Apps account. Then the user should be redirected to the authorization url and grant us the permission.

## <a id="update"></a> Update a single account

Update an email account for the user. Updates are allowed for the following fields.

- password
- host
- protocol
- start_tls
- ssl
- port

```
PUT /v1/accounts/:id
```

### Scope
write

### Response
``` javascript
{
    "id": 888,
    "host": "pop.mail.com",
    "protocol": "pop",
    "start_tls": true,
    "ssl": false,
    "port": 110,
    "msg_count": 1000,
    "storage": 200,
    "created_at": "2013-06-24T23:55:43.000Z",
    "updated_at": "2013-06-26T20:16:40.000Z",
    "email": "demo@mail.com"
}
```

## <a id="delete"></a> Delete a single account

Delete an email account for the user.

```
DELETE /v1/accounts/:id
```

### Scope
write

### Response
``` javascript
{
    "id": 888,
    "host": "pop.mail.com",
    "protocol": "pop",
    "start_tls": true,
    "ssl": false,
    "port": 110,
    "msg_count": 1000,
    "storage": 200,
    "created_at": "2013-06-24T23:55:43.000Z",
    "updated_at": "2013-06-26T20:16:40.000Z",
    "email": "demo@mail.com"
}
```
