---
layout: default
title:  "Contacts"
date:   2013-07-26 11:00:30
categories: contacts
---

## Contacts API

Contacts API allows you to download contacts

## <a id="list_contacts"></a> List Contacts

List the contacts for the accounts.

```
GET /v1/accounts/:account_id/contacts
```

### Parameters

#### page

As the number of contacts can be big, we use pagination for the API. The page parameter denotes the page number. If this is omitted, it will default to the first page. The numbering will start from 1.

default: 1

#### per_page

You may specify the number of contacts to return in a page. The number is capped at 40 contacts.

range: 1 - 40
default: 20

#### sort

- name
- email

default: name

##### direction

- asc
- desc

default: asc

### Scope

contact

### Response

``` javascript
{
    "count": 27,
    "start": 0,
    "contacts": [
        {
            "id": 1,
            "account_id": 100267,
            "name": "foo",
            "filename": "4QoLFBjjk6MjgBwCce8PRONMCRr%2BYynflr3hMAAAABxhiAACce8PRONMCRr%2BYynflr3hMAAAACFCnAAA%3D",
            "email": "foo@email.com",
            "phone": "123784",
            "backup_date": "2013-07-03T22:44:22.527Z"
        },
        {
            "id": 2,
            "account_id": 100267,
            "name": "moo",
            "filename": "moo",
            "email": "moo@email.com",
            "phone": "12982349",
            "backup_date": "2013-12-05T07:01:20.008Z"
        },
        {
            "id": 3,
            "account_id": 100267,
            "name": "boo",
            "filename": "boo",
            "email": "boo@email.com",
            "phone": "12387234",
            "backup_date": "2013-12-05T07:02:46.673Z"
        },
        {
            "id": 4,
            "account_id": 100267,
            "name": "too",
            "filename": "too",
            "email": "too@email.com",
            "phone": "1092837",
            "backup_date": "2013-12-05T07:03:17.656Z"
        },
        {
            "id": 5,
            "account_id": 100267,
            "name": "roo",
            "filename": "roo",
            "email": "roo@email.com",
            "phone": "0918247",
            "backup_date": "2013-12-05T07:04:37.051Z"
        },
        {
            "id": 6,
            "account_id": 100267,
            "name": "poo",
            "filename": "poo",
            "email": "poo@email.com",
            "phone": "987192874",
            "backup_date": "2013-12-05T07:05:56.034Z"
        },
        {
            "id": 7,
            "account_id": 100267,
            "name": "woo",
            "filename": "woo",
            "email": "woo@email.com",
            "phone": "09234807",
            "backup_date": "2013-12-05T07:06:26.592Z"
        },
        {
            "id": 8,
            "account_id": 100267,
            "name": "qoo",
            "filename": "qoo",
            "email": "qoo@email.com",
            "phone": "98723412",
            "backup_date": "2013-12-05T07:06:55.391Z"
        },
        {
            "id": 9,
            "account_id": 100267,
            "name": "eoo",
            "filename": "eoo",
            "email": "eoo@email.com",
            "phone": "2938472134",
            "backup_date": "2013-12-05T07:07:13.007Z"
        },
        {
            "id": 10,
            "account_id": 100267,
            "name": "voo",
            "filename": "voo",
            "email": "voo@email.com",
            "phone": "981273",
            "backup_date": "2013-12-05T07:08:19.151Z"
        },
        {
            "id": 11,
            "account_id": 100267,
            "name": "coo",
            "filename": "coo",
            "email": "coo@email.com",
            "phone": "123987",
            "backup_date": "2013-12-05T07:08:42.068Z"
        },
        {
            "id": 12,
            "account_id": 100267,
            "name": "goo",
            "filename": "goo",
            "email": "goo@email.com",
            "phone": "9182374",
            "backup_date": "2013-12-05T07:09:00.772Z"
        },
        {
            "id": 13,
            "account_id": 100267,
            "name": "doo",
            "filename": "doo",
            "email": "doo@email.com",
            "phone": "9123",
            "backup_date": "2013-12-05T07:11:27.912Z"
        },
        {
            "id": 14,
            "account_id": 100267,
            "name": "xoo",
            "filename": "xoo",
            "email": "xoo@email.com",
            "phone": "90823",
            "backup_date": "2013-12-05T07:11:45.296Z"
        },
        {
            "id": 15,
            "account_id": 100267,
            "name": "zoo",
            "filename": "zoo",
            "email": "zoo@email.com",
            "phone": "7234",
            "backup_date": "2013-12-05T07:12:03.039Z"
        },
        {
            "id": 16,
            "account_id": 100267,
            "name": "whoo",
            "filename": "whoo",
            "email": "whoo@email.com",
            "phone": "28347",
            "backup_date": "2013-12-05T07:12:27.631Z"
        },
        {
            "id": 17,
            "account_id": 100267,
            "name": "joo",
            "filename": "joo",
            "email": "joo@email.com",
            "phone": "7124",
            "backup_date": "2013-12-05T07:13:11.383Z"
        },
        {
            "id": 18,
            "account_id": 100267,
            "name": "yoo",
            "filename": "yoo",
            "email": "yoo@email.com",
            "phone": "234987",
            "backup_date": "2013-12-05T07:13:28.062Z"
        },
        {
            "id": 19,
            "account_id": 100267,
            "name": "kuu",
            "filename": "kuu",
            "email": "kuu@email.com",
            "phone": "324213",
            "backup_date": "2013-12-05T07:13:47.333Z"
        },
        {
            "id": 20,
            "account_id": 100267,
            "name": "ioo",
            "filename": "ioo",
            "email": "ioo@email.com",
            "phone": "8576234",
            "backup_date": "2013-12-05T07:14:09.821Z"
        }
    ]
}
```


## <a id"show"></a> Get a single contact

Get a contact from the account. It will return a file in [.vcard](http://en.wikipedia.org/wiki/VCard) format. The response will be encoded in [Base 64](http://en.wikipedia.org/wiki/Base64‎).

```
GET /v1/accounts/:account_id/contacts/:id
```

### Scope

contact

### Response

Base 64 encoded .vcard file.
