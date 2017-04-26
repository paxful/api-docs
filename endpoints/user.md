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
| feedback_neutral  | Int | Neutral feedback |
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
| last_seen         | String | User last seen |
 