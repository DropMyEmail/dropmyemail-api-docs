---
layout: default
title:  "Accounts"
date:   2013-10-16 13:35:30
categories: accounts
---

## Messages API

Message API allows you to view the messages of the account.

## <a id="list_mailboxes"></a> List Mailboxes

List the mailboxes for the account. To see the messages, use the __list__ query for the mailbox.

```
GET /v1/accounts/:account_id/mailboxes
```

### Parameters

#### page

As the number of mailboxes can be big, we use pagination for the API. The page parameter denotes the page number. If this is omitted, it will default to the first page. The numbering will start from 1.

default: 1

#### per_page

You may specify the number of mailboxes to return in a page. The number is capped at 40 mailboxes.

range: 1 - 40
default: 20

#### sort

- name
- message_count

default: name

##### direction

- asc
- desc

default: asc

### Scope

email

### Response

``` javascript
{
  count: 1,
  start: 0,
  mailboxes: [
      {
          "id": 675,
          "user_id": 347563,
          "account_id": 100272,
          "name": "INBOX",
          "message_count": 4
      }
  ]
}
```

## <a id="list_messages"></a> List Messages

List the messages for the mailbox. To retrieve the full message, use the __show__ query.

```
GET /v1/accounts/:account_id/mailboxes/:mailbox_id/messages
```

### Parameters

#### page

As the number of messages can be big, we use pagination. The page parameter denotes the page number. If this is omitted, it will default to the first page. The numbering will start from 1.

default: 1

#### per_page

You may specify the number of messages to return in a page. The number is capped at 40 messages.

range: 1 - 40
default: 20

#### type

- all
- has_attachments

default: all

#### sort

- date

default: date

##### direction

- asc
- desc

default: asc

### Scope

email

### Response

``` javascript
[
    {
        "id": 110328,
        "mailbox_id": 675,
        "from": "\"The Foo Team\" <support@foomail.com>",
        "to": null,
        "subject": "FooMail renewal reminder for dropmyemail@foomail.com,
        "has_attachments": false,
        "date": "2013-09-04T19:22:25.000Z",
        "size": 2421
    },
    {
        "id": 110212,
        "mailbox_id": 675,
        "from": "\"The FooMail Team\" <support@foomail.fm>",
        "to": null,
        "subject": "Info - Renewal for user dropmyemail@foomail.fm",
        "has_attachments": false,
        "date": "2013-08-19T19:42:25.000Z",
        "size": 2713
    },
    {
        "id": 109413,
        "mailbox_id": 675,
        "from": "\Zan\" <zan@dme.com>",
        "to": null,
        "subject": "test emails",
        "has_attachments": false,
        "date": "2013-07-21T18:01:06.000Z",
        "size": 2136
    },
    {
        "id": 109414,
        "mailbox_id": 675,
        "from": "\"FooMail.FM Administrator\" <webmaster@foomail.fm>",
        "to": null,
        "subject": "IMPORTANT: Click here to begin using your account",
        "has_attachments": true,
        "date": "2013-07-21T17:59:48.000Z",
        "size": 13736
    }
]
```

## <a id"show"></a> Get a single message

Get a message from the account. It will return a file in [.eml](http://en.wikipedia.org/wiki/Email) format. The response will be encoded in [Base 64](http://en.wikipedia.org/wiki/Base64‎).

```
GET /v1/accounts/:account_id/mailboxes/mailbox_id/messages/:id
```

### Scope

email

### Response

Base 64 encoded .eml file.

## <a id="search"></a> Search for messages

Search for messages with search terms.

```
GET /v1/accounts/:account_id/messages/search
```

### Parameters

#### query

Enter the terms for searching the emails. It will return the meta data of emails that satisfy the search terms.

default: empty string

#### page

As the number of messages can be big, we use pagination by default for the messages API. The page parameter denotes the page number. If this is omiitted, it will default to the first page. The numbering will start from 1.

default: 1

#### per_page

You may specify the number of messages to return in a page. The number is capped at 40 messages.

range: 1 - 40
default: 20

### Scope

email

### Response

``` javascript
{
    "count": 1,
    "start": 0,
    "messages": [
        {
            "id": 110212,
            "mailbox_id": 675,
            "from": "\"The Team\" <support@foo.com>",
            "to": null,
            "subject": "Info - Renewal for user dropmyemail@foo.com,
            "has_attachments": false,
            "date": "2013-08-19T19:42:25.000Z",
            "size": 2713
        }
    ]
}
```
