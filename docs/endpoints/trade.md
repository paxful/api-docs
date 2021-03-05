## Trade requests

### trade/get

Fetch information for an active/completed trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| trade         | Object | Trade item |
 
 Possible trade statuses in `trade_status` field are
 
   * Not funded
   * Funds processing
   * Funds processed
   * Active funded
   * Paid
   * Cancelled system
   * Cancelled buyer
   * Cancelled seller
   * Released
   * Dispute open
   * Dispute wins seller
   * Dispute wins buyer

### trade/start

Start a trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| offer_hash    | String            | Hash ID of an offer | Yes |
| satoshi    | Integer            | Trade amount in satoshis | Read below |
| crypto_amount | Integer | Trade amount in cyptocurrency. For btc trade in satoshi, for eth trade in gwei, for usdt trade in micro cents. 1 usdt = 1000000 micro cents. | Read below | 
| fiat    | Float            | Trade amount in fiat currency | Read below |

**Trade amount can be either passed in fiat or in crypto_amount. Crypto_amount is a new input parameter to replace satoshi, while satoshi is still supported.**

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success       | Boolean | True or false, whether the trade was started |
| trade_hash    | String | Hash Id of the trade |

### trade/list

List all your active trades 

##### Input parameters

None

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| count         | Integer       | Number of trades  |
| trades        | Array         | Trades            |

### trade/locations

Fetch information for seller and buyer locations in a trade.

Restricted: User requesting the information must be a trade partner.

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| seller       | Object | Seller location |
| buyer       | Object | Buyer location |

Example

```json
{
    "status": "success",
    "timestamp": 1596706249,
    "data": {
        "seller": {
            "detected_location": {
                "iso": "USA",
                "name": "USA",
                "localized_name": "USA"
            },
            "ip_location": {
                "iso": "USA",
                "name": "USA",
                "localized_name": "USA"
            }
        },
        "buyer": {
            "detected_location": {
                "iso": "DE",
                "name": "Germany",
                "localized_name": "Germany"
            },
            "ip_location": {
                "iso": "DE",
                "name": "Germany",
                "localized_name": "Germany"
            }
        }
    }
}
```

### trade/paid

Mark trade as PAID

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success       | Boolean | Success/Error |

### trade/cancel

Cancel a trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success       | Boolean | Success/Error |

### trade/reopen

Reopen trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| trade         | Object | Trade item |

### trade/release

Release bitcoins for a trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success       | Boolean | Success/Error |

### trade/dispute

Open a dispute

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |
| reason        | String            | Description of the dispute reason, max length 250 characters|Yes|
| reason_type   | String            | Type of reason, see below for valid values | No |

Reason Types:
* buyer_unresponsive_vendor
* buyer_payment_issue
* buyer_other
* vendor_coinlocker 
* vendor_payment_issue
* vendor_other

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success       | Boolean | Success/Error |

### trade/completed

Fetch a list of your completed trades, optionally limited by partner username

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| page          | Integer           | Page number, default 1 | No |
| partner       | String            | Limit by user | No |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| count         | Integer | Number of returned trades |
| page          | Integer | Page requested |
| trades        | Array | Array of trades |

### trade/fund

Fund a deferred escrow trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| trade_hash    | String            | Hash ID of a trade | Yes |

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success       | Boolean | Success/Error |
