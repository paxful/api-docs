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