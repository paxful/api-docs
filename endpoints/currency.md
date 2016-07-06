## Currency requests

### currency/rates

List all currencies and their rates (does not require authorization)

##### Input parameters

NONE

##### Response parameters

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| data          |  Array        | Array of rates data including rates in USD and BTC     |

### currency/btc

Shows bitcoin price in US Dollars (does not require authorization). Paxful updates bitcoin price every 3 minutes.

##### Input parameters

| Field name     | Type          | Description                      | Required | 
| -------------- | ------------- | ------------------------------------- |:----:|
| response     | String        | add `text` to get only bitcoin price as text and in non JSON format | No |

##### Response parameters

If not asked for `?response=text` return will be in JSON.

| Field name    | Type          | Description                                            |
| ------------- | :------------:| ------------------------------------------------------:|
| price          |  String        | Bitcoin price     |
| currency       |  String        | currency in which the price is returned. Currently only USD |