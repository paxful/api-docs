## User requests

### user/info

Fetch information for a user

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| username      | String            | Username of the user | Yes |

##### Response parameters

| Field name        | Type   | Description |
| ----------------- | -------| ----------- |
| username          | String | Username |
| feedback_positive | Int    | Positive feedback |
| feedback_negative | Int | Negative feedback |
| total_partners    | Int | Total number of trade partners |
| total_trades      | Int | Total number of trades |
| trusted_by        | Int | Trusted by user count |
| blocked_by        | Int | Blocked by user count |
| joined            | String | User joined time ago |
| total_btc         | String | Approx. amount of total traded btc |
| email_verified    | Boolean | Is email verified |
| phone_verified    | Boolean | Is Phone verified |
| is_vendor         | Boolean | Confirmed vendor |
| is_verified       | Boolean | Is verified |
| is_trusted        | Boolean | Is trusted |
| last_seen         | String | User last seen |
| avatar_url        | String | Avatar url | 
| status            | String | User status | 
| blocked_count     | Int    | Count of people blocked by the user | 
| completed_trades_with_me | Int | Count of completed trades with authorized user | 
| trades_total      | Int    | Count of total completed trades | 
| first_trade_date  | String | Date of the first completed trade | 
| created_at        | String | Date of account has been created | 
 
### user/trust

Add username to a trusted user list

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| username      | String            | Username of the user | Yes |

##### Response parameters

Empty

### user/untrust

Remove username from trusted list

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| username      | String            | Username of the user | Yes |

##### Response parameters

Empty

### user/block

Add username to blocked list

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| username      | String            | Username of the user | Yes |

##### Response parameters

Empty

### user/unblock

Remove user from blocked list

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| username      | String            | Username of the user | Yes |

##### Response parameters

Empty

### user/touch

Deprecated. You don’t need to use this endpoint directly, last seen time is going to be updated automatically if you use other API endpoints.

Refresh your last seen time. This endpoint has its own rate limit and is limited to 360 requests per hour (every 10 second max).

##### Input parameters

None

##### Response parameters

Empty

### user/me

Fetch information for a current user

##### Input parameters

None

##### Response parameters

| Field name        | Type   | Description |
| ----------------- | -------| ----------- |
| username          | String | Username |
| feedback_positive | Int    | Positive feedback |
| feedback_negative | Int | Negative feedback |
| total_partners    | Int | Total number of trade partners |
| total_trades      | Int | Total number of trades |
| trusted_by        | Int | Trusted by user count |
| blocked_by        | Int | Blocked by user count |
| joined            | String | User joined time ago |
| total_btc         | String | Approx. amount of total traded btc |
| email_verified    | Boolean | Is email verified |
| phone_verified    | Boolean | Is Phone verified |
| is_vendor         | Boolean | Confirmed vendor |
| is_verified       | Boolean | Is verified |
| is_trusted        | Boolean | Is trusted |
| last_seen         | String | User last seen |
| avatar_url        | String | Avatar url |
| status            | String | User status | 
