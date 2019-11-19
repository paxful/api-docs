## Offer requests

### offer/create

Create an Offer

##### Input parameters

| Field name             | Possible value          | Description       | Required |
| -------------          | ----------------------- | ----------------- | :------: |
| offer_type_field       | String                  | 'buy' or 'sell' string |   Yes    |
| currency               | String                  | 3 letter ISO code for fiat currency. 'USD' or any other. Case insensitive |   Yes    |
| payment_method         | String                  | Slug of payment method, for example Western Union needs to be passed as 'western-union' |   Yes    |
| margin                 | Float                   | Number between -99.99 to 21000.00 |   Yes    |
| range_min              | Integer                 | Minimum 1         |   Yes    |
| range_max              | Integer                 | Minimum 1         |   Yes    |
| payment_window         | Integer                 | Integer between 30 to 43200 |   Yes    |
| payment_method_label   | String                  | String of max 25 characters. Only ASCII characters |          |
| payment_method_group   | String                  | Enum of options: 'gift-cards', 'cash-deposits', 'online-transfers', 'debitcredit-cards'. |          |
| offer_terms            | String                  | String up to 2500 characters |     Yes     |
| trade_details          | String                  | String up to 2500 characters |     Yes     |
| require_verified_email | Boolean                 |                   |          |
| require_verified_phone | Boolean                 |                   |          |
| require_min_past_trades| Boolean                 |                   |          |
| show_only_trusted_user | Boolean                 |                   |          |
| predefined_amount      | String                  | Comma separated predefined amounts, i.e. 20,30,50 |   |
| country_limitation_type | String                 | Type of limitation. Valid values are 'allowed' or 'disallowed' |  |
| country_limitation_list | String                 | Comma separated list of country codes |  |
| tags                   | String                  | Comma separated list of tags, if a tag was not approved before, it's ignored |  |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | True or false, whether the offer was created           |
| offer_hash    | String        | Hash of the newly added offer                          |

### offer/update

Updates an offer

##### Input parameters

| Field name             | Possible value          | Description       |
| ---------------------- | ----------------------- | ----------------- |
| offer_hash             | String                  | Hash of the offer |
| currency               | String                  | 3 letter ISO code for currency. 'USD' or any other. Case insensitive |
| payment_method         | String                  | Slug of payment method, for example Western Union needs to be passed as 'western-union' |
| margin                 | Float                   | Number between -99.99 to 21000.00 |
| range_min              | Integer                 | Minimum 1         |
| range_max              | Integer                 | Minimum 1         |
| payment_window         | Integer                 | Integer between 30 to 43200 |
| payment_method_label   | String                  | String of max 25 characters. Only ASCII characters |
| payment_method_group   | String                  | Enum of options: 'gift-cards', 'cash-deposits', 'online-transfers', 'debitcredit-cards'. |
| offer_terms            | String                  | String up to 2500 characters |
| trade_details          | String                  | String up to 2500 characters |
| require_verified_email | Boolean                 |                   |
| require_verified_phone | Boolean                 |                   |
| require_min_past_trades| Boolean                 |                   |
| show_only_trusted_user | Boolean                 |                   |
| predefined_amount      | String                  | Comma separated predefined amounts, i.e. 20,30,50 |   |
| tags                   | String                  | Comma separated list of tags, if a tag was not approved before, it's ignored. If this parameter is missing, tags are not updated. If it's empty, any existing tags are removed |  |
| country_limitation_type | String                 | Type of limitation. Valid values are 'allowed' or 'disallowed' |
| country_limitation_list | String                 | Comma separated list of country codes |

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | True or false, whether the offer was updated           |

### offer/update-margin

Updates an offer margin

##### Input parameters

| Field name             | Possible value          | Description       |
| ---------------------- | ----------------------- | ----------------- |
| offer_hash             | String                  | Hash of the offer |
| margin                 | Float                   | Number between -99.99 to 21000.00 |

#### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | True or false, whether the offer margin was updated    |

### offer/delete

Delete an offer

##### Input parameters

| Field name    | Type          | Description       |
| ------------- | ------------- | ----------------- |
| offer_hash    | String        | Hash of the offer |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | Will be always true or error response                  |

### offer/list

Return all your offers

##### Input parameters

| Field name    | Type          | Description                      |
| ------------- | ------------- | ------------------------------------- |
| active        | Boolean       | Whether to only return active offers             |
| offer_type     | String        | Valid types are 'buy' and 'sell' |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of offers               |
| offers        | Array         | Offers                  |

### offer/turn-on

Turn On all your offers

##### Input parameters

None

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of toggled on offers                 |

### offer/turn-off

Turn Off all your offers

##### Input parameters

None

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of toggled off offers                  |

### offer/price

Return a price for an offer

##### Input parameters

| Field name    | Type          | Description                      |
| ------------- | ------------- | ------------------------------------- |
| offer_hash    | String        | Hash of the offer |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| currency      | String       | Price currency |
| price         | Float | Price of the offer |

### offer/prices

Return all prices for offers for a given payment method

##### Input parameters

| Field name     | Type          | Description                      |
| -------------- | ------------- | ------------------------------------- |
| payment_method | String        | Payment method slug |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of price records               |
| prices        | Array         | Prices, an array consisting of currency and price      |

### offer/all

Fetch offers from paxful. Replaces deprecated method of /buy-bitcoin?format=json
Authentication is optional, affects rate limiting

Results are cached for 1 minute.

##### Input parameters

| Field name     | Type          | Description                      | Required | 
| -------------- | ------------- | ------------------------------------- |:----:|
| offer_type     | String        | Offer type (buy, sell) | * |
| payment_method | String        | Payment method slug | |
| currency_code  | String        | Currency code | |
| fiat_min       | String        | Fiat min | |
| group          | String        | Payment group slug | |
| geoname_id     | Int           | Location id is needed to search for offers from Cash in Person payment method. If payment method is another - parameter will be ignored.<br>You can find location ids here: https://www.geonames.org/.<br>For better experience use locations ids of countries and cities. | |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| count         | Integer       | Number of returned offers               |
| totalCount    | Integer         | Total number of existing offers      |
| offers        | Array         | Offers     |

### offer/activate

Activate an offer

##### Input parameters

| Field name     | Type          | Description                      | Required | 
| -------------- | ------------- | ------------------------------------- |:----:|
| offer_hash     | String        | Offer type (buy, sell) | * |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | True on success, false on error           |

### offer/deactivate

Deactivate an offer

##### Input parameters

| Field name     | Type          | Description                      | Required | 
| -------------- | ------------- | ------------------------------------- |:----:|
| offer_hash     | String        | Offer type (buy, sell) | * |


##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| success       | Boolean       | True on success, false on error                  |
