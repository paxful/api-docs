## Offer requests

### offer/create

Create an Offer

#### Input parameters

| Field name             | Possible value          | Description       | Required |
| -------------          | ----------------------- | ----------------- | :------: |
| offer_type_field       | String/Integer          | Hash of the offer |   Yes    |
| currency               | String                  |                   |   Yes    |
| payment_method         | String                  |                   |   Yes    |
| margin                 | Integer                 |                   |   Yes    |
| range_min              | Integer                 | Hash of the offer |   Yes    |
| range_max              | Integer                 | Hash of the offer |   Yes    |
| payment_window         | Integer                 | Hash of the offer |   Yes    |
| payment_method_label   | String                  | Hash of the offer |          |
| payment_method_group   | String                  | Hash of the offer |          |
| offer_terms            | String                  | Hash of the offer |          |
| trade_details          | String                  | Hash of the offer |          |
| require_verified_email | Boolean                 | Hash of the offer |          |
| require_verified_phone | Boolean                 | Hash of the offer |          |
| require_min_past_trades| Boolean                 | Hash of the offer |          |
| show_only_trusted_user | Boolean                 | Hash of the offer |          |

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of toggled Off offers (if any)                  |

### offer/update

Updates an offer

#### Input parameters

| Field name             | Possible value          | Description       |
| ---------------------- | ----------------------- | ----------------- |
| offer_hash             | String                  | Hash of the offer |
| currency               | String                  | Hash of the offer |
| payment_method         | String                  | Hash of the offer |
| margin                 | Integer                 | Hash of the offer |
| range_min              | Integer                 | Hash of the offer |
| range_max              | Integer                 | Hash of the offer |
| payment_window         | Integer                 | Hash of the offer |
| payment_method_label   | String                  | Hash of the offer |
| payment_method_group   | String                  | Hash of the offer |
| offer_terms            | String                  | Hash of the offer |
| trade_details          | String                  | Hash of the offer |
| require_verified_email | Boolean                 | Hash of the offer |
| require_verified_phone | Boolean                 | Hash of the offer |
| require_min_past_trades| Boolean                 | Hash of the offer |
| show_only_trusted_user | Boolean                 | Hash of the offer |

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of toggled Off offers (if any)                  |

### offer/delete

Delete an offer

#### Input parameters

| Field name    | Type          | Description       |
| ------------- | ------------- | ----------------- |
| offer_hash    | String        | Hash of the offer |

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | Will be always true or error response                  |

### offer/list

Return all your offers

#### Input parameters

| Field name    | Type          | Description                      |
| ------------- | ------------- | ------------------------------------- |
| active        | Boolean       | Whether to only return active offers             |
| offerType     | String        | Valid types are 'buy' and 'sell' |

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of offers               |
| offers        | Array         | Offers                  |

### offer/turn-on

Turn On all your offers

#### Input parameters

None

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of toggled On offers (if any)                   |

### offer/turn-off

Turn Off all your offers

#### Input parameters

None

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of toggled Off offers (if any)                  |