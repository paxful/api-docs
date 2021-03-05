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