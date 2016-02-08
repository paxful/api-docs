## Payment Method requests

### payment-method/list

Fetch a list of available payment methods

**NB! This endpoint does not require Authentication**

#### Input parameters

None

#### Response parameters

| Field name    | Type          | Description                                                 |
| ------------- | :------------:| -----------------------------------------------------------:|
| count         | Integer       | Count of methods                                            |
| methods       | Array         | List of payment methods including their name and slug       |
