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

Fetch information for an active/completed trade

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| offer_hash    | String            | Hash ID of an offer | Yes |
| satoshi    | Integer            | Trade amount in satoshis | read below |
| fiat    | Float            | Trade amount in fiat currency | read below |

**Either 'satoshi' or 'fiat' must be provided**

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

##### Response parameters

| Field name    | Type | Description |
| ------------- | ---- | ----------- |
| success       | Boolean | Success/Error |