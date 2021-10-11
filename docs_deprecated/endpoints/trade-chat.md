## Trade Chat requests

### trade-chat/latest

Fetch latest messages for all active trades, or for one trade if trade_hash has passed. Latest messages are messages posted in last 10 minutes

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade. If passed, method return latest messages only for this trade. If omitted, the method return latest messages/attachments for all active trades| No |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| count   | Integer | Total number of active trades| 
| trades | Array | Array of trades, hashed by trade hash, with keys "messages", "attachments" |

Example
````json
{
    "status": "success",
    "timestamp": 1585672464,
    "data": {
        "count": 2,
        "trades": {
            "zXDL8Rv7Jge": {
                "messages": [
                    {
                        "id": "5e83710b8512b00ef6759316",
                        "timestamp": 1585672459.258,
                        "type": "msg",
                        "text": "test message",
                        "author": "vendor"
                    }
                ],
                "attachments": []
            },
            "mndVjYvPLD7": {
                "messages": [
                    {
                        "id": "5e836f758512b00ef6759315",
                        "timestamp": 1585672053.788,
                        "type": "msg",
                        "text": "test message",
                        "author": "vendor"
                    },
                    {
                        "id": "5e836f8b5a7d1679473b4802",
                        "timestamp": 1585672075.142,
                        "type": "msg",
                        "text": "test message",
                        "author": "buyer"
                    },
                    {
                        "id": "5e836f8e413b234fff7c8423",
                        "timestamp": 1585672078.114,
                        "type": "trade_attach_uploaded",
                        "text": "vendor has just uploaded an attachment.",
                        "author": "vendor"
                    }
                ],
                "attachments": [
                    {
                        "image_hash": "MqyZokwaZNX",
                        "author": "vendor"
                    }
                ]
            }
        }
    }
}
````

### trade-chat/get

Fetch messages for a trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| messages      | Array | Array of messages with keys "text", "timestamp", <br> "type" and "user_id" if its a reply from user |
| attachments   | Array | Array of attachments in trade, contains either image_hash or url properties. For image_hash property check docs for endpoint trade-chat/image | 

Example
````json
{
    "messages": [
        {
            "id": "5e836bfd413b234fff7c8422",
            "text": "Hi",
            "timestamp": 12345678,
            "type": "msg",
            "user_id": 1001
        },
        {
            "id": "5e8367d7ec5e63484e6d41e2",
            "text": "Cancelled",
            "timestamp": 12345678,
            "type": "trade_cancelled"
        }
    ]
}
````

### trade-chat/post

Post message into trade chat

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |
| message    | String               | Message contents | Yes |
                   
##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success         | Boolean | Whether message was posted |
| id | String | Id of the message if posted |

### trade-chat/image

Fetch an image attachment from trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| image_hash    | String            | Hash ID of image which you get from trade-chat/get endpoint, attachments property | Yes |
| size    | Integer               | Size to fetch, either 2 (full sized) or 3 (thumbnail) | No |
                   
##### Response parameters

Response is the image

### trade-chat/image/add

Attach image to trade chat.

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |
| file    | String               | Link to a file in the Internet. It should be reachable from an external service. Supported formats are `jpeg`, `png`, `jpg`. | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success | Boolean | Whether image was posted in trade chat |
| id | String | Id of the image's message if posted |