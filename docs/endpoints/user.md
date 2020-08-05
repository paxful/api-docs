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
| feedback_negative | Int | Positive feedback |
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
| is_trusted       | Boolean | Is trusted |
| last_seen         | String | User last seen |
 
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

Refresh your last seen timestamp

**This endpoint has its own rate limit and is limited to 360 requests per hour (every 10 second max)**

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
| feedback_negative | Int | Positive feedback |
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
| is_trusted       | Boolean | Is trusted |
| last_seen         | String | User last seen |
 