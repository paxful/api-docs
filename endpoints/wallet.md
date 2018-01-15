## Wallet

### wallet/balance

Fetch user balance

##### Input parameters

None

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| balance       | Integer       | Currently available user balance in satoshis           |
| incoming_amount    | Integer        |                           |
| balance_escrow | Integer | Balance in escrow, in satoshis |

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