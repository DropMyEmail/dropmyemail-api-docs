---
layout: default
title:  "Accounts"
date:   2013-10-16 13:35:30
categories: accounts
---

## Migrate API

Migrate API allows you to manipulate email accounts for migrations. A migration means moving the emails from one account to another.

## <a id="list"></a> List

List the migrates for the account.

```
GET /v1/accounts/:account_id/migrates
```

### Parameters

#### sort

- start_time
- end_time

default: start_time

##### direction

- asc
- desc

default: asc

### Scope

read

### Response

``` javascript
[
    {
        "id": 53,
        "account_id": 100272,
        "host": "imap.googlemail.com",
        "protocol": "imap",
        "start_tls": false,
        "port": 993,
        "ssl": true,
        "downloaded": 0,
        "messages": 0,
        "status": null,
        "start_time": "2013-10-16T00:36:01.000Z",
        "end_time": "2013-10-16T01:36:01.000Z",
        "created_at": "2013-10-16T00:32:40.000Z",
        "google_oauth_token": "some-token",
        "backup_id": null,
        "google_oauth_token_secret": "massive-secret",
        "message_ids": "[72915,110091,110314,109815,110353,85899,54637,108237,69084,70322]",
        "email": "demo@dropmyemail.com"
    }
]
```

## <a id"show"></a> Get a single migrate

Get a migrate from the account.

```
GET /v1/accounts/:account_id/migrates/:id
```

### Scope

read

### Response

``` javascript
{
    "id": 53,
    "account_id": 100272,
    "host": "imap.googlemail.com",
    "protocol": "imap",
    "start_tls": false,
    "ssl": true,
    "port": 993,
    "downloaded": 0,
    "messages": 0,
    "status": null,
    "start_time": "2013-10-16T00:36:01.000Z",
    "end_time": "2013-10-16T01:36:01.000Z",
    "google_oauth_token": "some-token",
    "google_oauth_token_secret": "massive-secret",
    "backup_id": null,
    "message_ids": "[72915,110091,110314,109815,110353,85899,54637,108237,69084,70322]",
    "created_at": "2013-10-16T00:32:40.000Z",
    "email": "demo@dropmyemail.com"
}
```

## <a id="create"></a> Add a migrate

Start an migration for the account

```
POST /v1/accounts/:account_id/migrates
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
    "id": 63,
    "account_id": "100272",
    "host": "imap.mail.yahoo.com",
    "protocol": "imap",
    "start_tls": false,
    "ssl": true,
    "port": "993",
    "created_at": "2013-10-18T03:47:59.765Z",
    "email": "dropmyemail@yahoo.com"
}
```

#### Special case for Gmail/Google Apps account

_Note: This part is not completed yet. But documented for your reference_

If the email account is a Gmail or Google Apps account, we need the user to grant us permission to access his account. It is done through Oauth.

We will return you an authorization url. First, the user has to be logged in to the same Gmail/Google Apps account. Then the user should be redirected to the authorization url and grant us the permission.
