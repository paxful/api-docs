## Payment Method requests

### payment-method/list

Fetch a list of available payment methods

**NB! This endpoint does not require Authentication**

##### Input parameters

| Field name    | Type          | Description                                                 | Required |
| ------------- | :------------:| -----------------------------------------------------------:| -------- |
| order         | String        | Sort by buy or sell, default is buy                         | No |

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

```
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
### payment-method/popular

Fetch popular payment methods by country code

**NB! This endpoint does not require Authentication**

##### Input parameters

| Field name    |   Possible value  | Description   | Required |
| ------------- | ----------------- | ------------- | :------: |
| country_code  | String            | Show popular payment methods by country, default US | No |

##### Response parameters

| Field name      | Type          | Description                                                 |
| --------------- | :------------:| -----------------------------------------------------------:|
| sell            | Array         | Payment methods slug list, grouped by overall, country and groups |
| buy             | Array         | Payment methods slug list, grouped by overall, country and groups |

##### Response example

```
{
  "status": "success",
  "timestamp": 1455032576,
  "data": {
    "sell": {
      "overall": [
        "itunes-gift-card"
      ],
      "country": [
        "webmoney"
      ],
      "groups": {
        "bank-transfers": [
          "bank-transfer"
        ]
      }
    },
    "buy": {
      "overall": [
        "cash-deposit-to-bank"
      ],
      "country": [
        "western-union"
      ],
      "groups": {
        "bank-transfers": [
          "bank-transfer"
        ]
      }
    }
  }
}
```
### payment-method-group/list

Fetch payment method groups list

**NB! This endpoint does not require Authentication**

##### Input parameters

None

##### Response parameters

| Field name      | Type          | Description                                                 |
| --------------- | :------------:| -----------------------------------------------------------:|
| name            | String        | Payment method name         |
| slug            | String        | Payment method alias        |
| description     | Array         | Payment methods description for different crypto currencies |

##### Response example

```
{
  "status": "success",
  "timestamp": 1619503055,
  "data": [
    {
      "name": "Gift Cards",
      "slug": "gift-cards",
      "description": {
        "sell": {
          "btc": "Sell your Bitcoin for big discounts on popular gift cards from iTunes, Amazon and more.",
          "usdt": "Sell your Tether for big discounts on popular gift cards from iTunes, Amazon and more.",
          "eth": "Sell your Ethereum for big discounts on popular gift cards from iTunes, Amazon and more."
        },
        "buy": {
          "btc": "Have a gift card you don't need? Trade it here for Bitcoin instantly.",
          "usdt": "Have a gift card you don't need? Trade it here for Tether instantly.",
          "eth": "Have a gift card you don't need? Trade it here for Ethereum instantly."
        }
      }
    }
  ]
}
```