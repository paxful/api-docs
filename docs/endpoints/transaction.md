## Transaction requests

### transactions/all

Fetch a list of your transactions, optionally filtered by type

##### Input parameters

| Field name    |   Possible value  | Description                                                   | Required |
| ------------- | ----------------- | ------------------------------------------------------------- | :------: |
| page          | Integer           | Requested page, defaults to 1                                 | No |
| type          | String            | Type of transaction, check below for a list of accepted types | No |
| crypto_currency_code | String | Filter by crypto currency code or 'all' value for fully list, default is btc | No |

Valid Types:
 * trade
 * non-trade
 * received
 * received-internal
 * received-external
 * sent
 * sent-internal
 * sent-external

##### Response parameters

| Field name    | Type    | Description |
| ------------- | ------- | ----------- |
| count         | Integer | Count of transactions returned |
| page          | Integer | Current page |
| transactions  | Array   | Array of transactions |
