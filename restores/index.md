---
layout: default
title:  "Accounts"
date:   2013-10-16 13:35:30
categories: accounts
---

## Restore API

Restore API allows you to manipulate email accounts for restores. A restore means moving the emails from the backups to the same account.

## <a id="list"></a> List

List the restores for the account.

```
GET /v1/accounts/:account_id/restores
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
        "id": 153,
        "account_id": 100272,
        "downloaded": 1,
        "messages": 12,
        "status": "7",
        "start_time": "2013-07-10T22:20:10.000Z",
        "end_time": "2013-07-10T22:21:21.000Z",
        "created_at": "2013-07-10T22:19:40.000Z",
        "backup_id": null,
        "message_ids": null
    }
]
```

## <a id"show"></a> Get a single restore

Get a restore from the account.

```
GET /v1/accounts/:account_id/restores/:id
```

### Scope

read

### Response

``` javascript
{
    "id": 153,
    "account_id": 100272,
    "downloaded": 1,
    "messages": 12,
    "status": "7",
    "start_time": "2013-07-10T22:20:10.000Z",
    "end_time": "2013-07-10T22:21:21.000Z",
    "backup_id": null,
    "message_ids": null,
    "created_at": "2013-07-10T22:19:40.000Z"
}
```

## <a id="create"></a> Add a restore

Start an restore for the account

```
POST /v1/accounts/:account_id/restores
```

### Input parameters

None needed

### Scope
write

### Response

``` javascript
{
    "user_id": 347563,
    "account_id": "100272",
    "downloaded": false,
    "restore_size": 0,
    "messages": 0,
    "attempts": 0,
    "created_at": "2013-11-08T07:05:17.300Z",
    "id": 156
}
```
