## Offer requests

### offer/create

Create an Offer

#### Input parameters

| Field name             | Possible value          | Description       | Required |
| -------------          | ----------------------- | ----------------- | :------: |
| offer_type_field       | String/Integer          | 'buy' or 'sell' string, on backend it's converted to 1 or 2 |   Yes    |
| currency               | String                  | 3 letter ISO code for currency. 'USD' or any other, case insensitive |   Yes    |
| payment_method         | String                  | Slug of payment method, for example Western Union needs to be passed as 'western-union' |   Yes    |
| margin                 | Integer                 | Number between -99 to 21000 |   Yes    |
| range_min              | Integer                 | Minimum 1         |   Yes    |
| range_max              | Integer                 | Minimum 1         |   Yes    |
| payment_window         | Integer                 | Integer between 30 to 43200 |   Yes    |
| payment_method_label   | String                  | string of max 25 characters |          |
| payment_method_group   | String                  | enum of options - 'gift-cards', 'cash-deposits', 'online-transfers', 'debitcredit-cards'. |          |
| offer_terms            | String                  | string up to 2.5k |          |
| trade_details          | String                  | string up to 2.5k |          |
| require_verified_email | Boolean                 |                   |          |
| require_verified_phone | Boolean                 |                   |          |
| require_min_past_trades| Boolean                 |                   |          |
| show_only_trusted_user | Boolean                 |                   |          |

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | True or False, whether the offer was created           |
| offer_hash    | String        | Hash of the newly added offer                          |

### offer/update

Updates an offer

#### Input parameters

| Field name             | Possible value          | Description       |
| ---------------------- | ----------------------- | ----------------- |
| offer_hash             | String                  | Hash of the offer |
| currency               | String                  | 3 letter ISO code for currency. 'USD' or any other, case insensitive |
| payment_method         | String                  | Slug of payment method, for example Western Union needs to be passed as 'western-union' |
| margin                 | Integer                 | Number between -99 to 21000 |
| range_min              | Integer                 | Minimum 1         |
| range_max              | Integer                 | Minimum 1         |
| payment_window         | Integer                 | Integer between 30 to 43200 |
| payment_method_label   | String                  | string of max 25 characters |
| payment_method_group   | String                  | enum of options - 'gift-cards', 'cash-deposits', 'online-transfers', 'debitcredit-cards'. |
| offer_terms            | String                  | string up to 2.5k |
| trade_details          | String                  | string up to 2.5k |
| require_verified_email | Boolean                 |                   |
| require_verified_phone | Boolean                 |                   |
| require_min_past_trades| Boolean                 |                   |
| show_only_trusted_user | Boolean                 |                   |

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | True or False, whether the offer was updated           |

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