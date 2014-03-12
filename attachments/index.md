---
layout: default
title:  "Attachments"
date:   2013-07-26 11:00:30
categories: attachmetns
---

## Attachments API

Attachments API allows you to search and download attachments.

## <a id="list_attachments"></a> List Attachments

List the attachments for the accounts.

```
GET /v1/accounts/:account_id/attachments
```

### Parameters

#### page

As the number of attachments can be big, we use pagination for the API. The page parameter denotes the page number. If this is omitted, it will default to the first page. The numbering will start from 1.

default: 1

#### per_page

You may specify the number of attachments to return in a page. The number is capped at 40 attachments.

range: 1 - 40
default: 20

#### sort

- date
- filename
- sender

default: date

##### direction

- asc
- desc

default: asc

### Scope

attachment

### Response

``` javascript
{
    "count": 3,
    "start": 0,
    "attachments": [
        {
            "id": 15915,
            "account_id": 100267,
            "message_id": 86652,
            "sender": "\"sue\" <sue@hotmail.sg>",
            "filename": "OfficeTrack Admin and Web User Guide.pdf",
            "mime_type": "application/pdf",
            "meta_data": "PDF document, version 1.5",
            "date": "2013-06-25T19:17:24.000Z",
            "size": 2274960
        },
        {
            "id": 15916,
            "account_id": 100267,
            "message_id": 86661,
            "sender": "\"mat\" <s@hotmail.sg>",
            "filename": "Android.png",
            "mime_type": "image/png",
            "meta_data": "Format: PNG, Geometry: 228x363, Depth: 8 bits-per-pixel, Colors: 11155",
            "date": "2013-06-25T18:04:07.000Z",
            "size": 52726
        },
        {
            "id": 18746,
            "account_id": 100267,
            "message_id": 109414,
            "sender": "\"FastMail.FM Administrator\" <webmaster@fastmail.fm>",
            "filename": "This_is_how_attachments_appear.txt",
            "mime_type": "text/plain",
            "meta_data": "ASCII text, with CRLF line terminators",
            "date": "2013-07-21T17:59:48.000Z",
            "size": 247
        }
    ]
}
```

## <a id"show"></a> Get a single attachment

Get an attachment from the account. It will return the attachment encoded in [Base 64](http://en.wikipedia.org/wiki/Base64‎).

```
GET /v1/accounts/:account_id/attachments/:id
```

### Scope

attachment

### Response

Base 64 encoded file.

## <a id="search_attachments"></a> Search for attachments

Search for attachments with search terms.

```
GET /v1/accounts/:account_id/attachments_search
```

### Parameters

#### query

Enter the terms for searching the attachments. It will return the meta data of attachments that satisfy the search terms.

default: empty string

#### page

As the number of attachments can be big, we use pagination by default for the messages API. The page parameter denotes the page number. If this is omiitted, it will default to the first page. The numbering will start from 1.

default: 1

#### per_page

You may specify the number of attachments to return in a page. The number is capped at 40 attachments.

range: 1 - 40
default: 20

### Scope

attachment

### Response


``` javascript
{
    "count": 1,
    "start": 0,
    "attachments": [
        {
            "id": 110212,
            "account_id": 675,
	    "message_id": 812,
	    "sender": "\"at\" <f@hotmail.sg>",
            "filename": "OfficeTrack Admin and Web User Guide.pdf",
            "mime_type": "application/pdf",
            "meta_data": "PDF document, version 1.5",
            "date": "2013-06-25T19:17:24.000Z",
            "size": 2274960
        }
    ]
}
```
