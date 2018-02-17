## Affiliate requests

Requests related to your affiliate account

### affiliate/transactions

Fetch a list of your affiliate transactions

##### Input parameters

| Field name    |   Possible value  | Description                                                   | Required |
| ------------- | ----------------- | ------------------------------------------------------------- | :------: |
| page          | Integer           | Requested page, defaults to 1                                 | No |


##### Response parameters

| Field name    | Type    | Description |
| ------------- | ------- | ----------- |
| count         | Integer | Count of transactions returned |
| page          | Integer | Current page |
| transactions  | Array   | Array of transactions |
