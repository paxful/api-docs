## Trade Chat requests

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
            "text": "Hi",
            "timestamp": 12345678,
            "type": "msg",
            "user_id": 1001
        },
        {
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

### trade-chat/image

Fetch an image attachment from trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| image_hash    | String            | Hash ID of image which you get from trade-chat/get endpoint, attachments property | Yes |
| size    | Integer               | Size to fetch, either 2 (full sized) or 3 (thumbnail) | No |
                   
##### Response parameters

Response is the image