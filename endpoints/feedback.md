## Feedback

### feedback/give

Give a feedback for a trade

**NB!** Message should be encoded as required per [RFC 3986](https://tools.ietf.org/html/rfc3986) (i.e. spaces should look like %20)

##### Input parameters

| Field name       | Possible value          | Description       | Required |
| ---------------- | ----------------------- | ----------------- | :------: |
| trade_hash       | String                  | Trade hash of the trade |   Yes    |
| message       | String                     | Feedback message |   No    |
| rating       | Integer (-1,0,1)            | Rating |   Yes    |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | boolean       | Whether feedback was added          |

### feedback/reply

Reply to feedback

##### Input parameters

| Field name             | Possible value          | Description       | Required |
| -------------          | ----------------------- | ----------------- | :------: |
| trade_hash       | String                  | Trade hash of the trade |   Yes    |
| message       | String                     | Reply message |   Yes    |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | Whether reply was added      |