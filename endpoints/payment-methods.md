## Payment Method requests

### payment-method/list

Fetch a list of available payment methods

**NB! This endpoint does not require Authentication**

##### Input parameters

None

##### Response parameters

| Field name    | Type          | Description                                                 |
| ------------- | :------------:| -----------------------------------------------------------:|
| count         | Integer       | Count of methods                                            |
| methods       | Array         | List of payment methods including their name and slug       |


### payment-method/fee

Fetch fees for payment methods

**NB! This endpoint does not require Authentication**

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| currency      | String            | Limit by currency, default is USD | No |
| slug          | String            | Limit by payment method | No |

##### Response parameters

| Field name      | Type          | Description                                                 |
| --------------- | :------------:| -----------------------------------------------------------:|
| count           | Integer       | Number of records                                           |
| btc_rate        | Float         | Bitcoin fiat currency price    |
| fiat_currency   | String        | Currency code       |
| payment_methods | Array         | Payment methods and their fees       |

##### Response example

```json,ignore
{
  "status": "success",
  "timestamp": 1495018511,
  "data": {
    "count": 4,
    "btc_rate": "1034.60",
    "fiat_currency": "USD",
    "payment_methods": {
      "western-union": {
        "avg_from": "5.00",
        "avg_to": "7.00"
      },
      "paypal-my-cash": {
        "avg_from": "107.00",
        "avg_to": "110.00"
      },
      "amazon-gift-card": {
        "avg_from": "16.00",
        "avg_to": "18.00"
      },
      "credit-card": {
        "avg_from": "33.00",
        "avg_to": "45.00"
      }
    }
  }
}
```
