## Wallet

### wallet/balance

Fetch user balance

##### Input parameters

None

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| balance       | Integer       | Currently available user balance in satoshi for btc wallet, micro cents for usdt wallet and wei for eth wallet.           |
| incoming_amount    | Integer        |                           |
| crypto_currency_code | String | By default if not defined returns btc wallet balance. Cryptocurrency code: ‘btc', ‘usdt’ or 'eth’. |
| balance_escrow | Integer | Balance in escrow, in satoshi for btc wallet, micro cents for usdt wallet and wei for eth wallet. |

### wallet/new-address

Generate new bitcoin address

##### Input parameters

None

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| address       | String       | New bitcoin address       |

### wallet/list-addresses

Fetch list of your addresses

##### Input parameters

None

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| addresses     | Array         | List of your bitcoin addresses, 50 limit       |
| crypto_currency_code | String | By default if not defined returns btc  addresses. Cryptocurrency code: ‘btc', ‘usdt’ or 'eth’. |

### wallet/conversion-quotes

Get the current conversion quotes/prices of cryptocurrency pair(s).
Note, array **response** is returned.

##### Input parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| convert_from     | String         | Cryptocurrency to convert from e.g "BTC", "USDT", "ETH". |
| convert_to | String | Cryptocurrency to convert to e.g "BTC", "USDT", "ETH". |

##### Response parameters

Response is Array of one or many objects. Each object has the following fields.

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| pair     | String         |Conversion pair e.g BTCUSDT.       |
| quote_id | String | Converstion rate's quote id, to be used for the conversion as input parameter e.g `"50165aec-44dd-4e41-9c180e04432e2b01"`. |
| conversion_rate | Object | An Object consisting of Conversion Rate e.g `{"amount": "58421.55", "currency_code": "BTC"}`. |
| expired_time | String | Time when quote expires e.g "2021-05-30 15:00:05" Conversion using given quote_id can be made before this time. Time is in UTC. |
| is_active | Boolean | Active status of this pair. Shows if conversion of the pair is possible. |

### wallet/convert

Convert balance from one cryptocurrency to another. `quote_id` is required and only BTC, USDT, and ETH is available.

##### Input parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| convert_from     | String         | Cryptocurrency to convert from e.g "BTC", "USDT", "ETH". |
| convert_to | String | Cryptocurrency to convert to e.g "BTC", "USDT", "ETH". |
| amount | String | Amount to convert from, in cryptocurrency. For BTC in satoshi, for ETH in wei, for USDT in microcents. 1 USDT = 1000000 micocents. |
| quote_id | String | Request quote_id retrieved from `wallet/conversion-quotes` endpoint. If expired, new `quote_id` should be requested. |

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| order_id     | String         | Conversion order id.      |
| converted_from_crypto_currency_code | String | Cryptocurrency code of converted from amount e.g "BTC". |
| converted_from_amount | String | Amount converted (in full unit e.g for BTC then "0.04", for USDT "10" etc). |
| converted_to_crypto_currency_code | String | Cryptocurrency code of received amount e.g "USDT". |
| converted_to_amount | String | Amount received after conversion (in full unit e.g for BTC then "0.04", for USDT "10" etc). |