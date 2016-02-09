#Getting started

##Authentication

For authentication, you need to obtain credentials from the Settings > Developer part in paxful.com

Example of request content
```
api_key=dgsdrij234fsdfgkhr&nounce=1455035029943&offer_hash=jewldanf_234f&apiseal=25a62a4c646c5c401ea7c04ebefd6324f15d7ec7b9c6b0710f50117469d2f830
```

In which there are required:

   * api_key - key generated from the UI, unique per user
   * nounce - unix timestamp
   * apiseal - signature (digest) of the request params passed through a HMAC-SHA1 construct
   
   
To generate the apiseal, you need to pass the request payload (i.e. api_key, nounce + request parameters) through hash method using the secret key provided from the UI

#####Examples
PHP:

```
$payload = [
    'api_key' => 'dgsdrij234fsdfgkhr',
    'nounce' => time(),
    'offer_hash' => '12Da_F1ef2D98',
    'margin' => 50,
];

$apiSeal = hash_hmac('sha256', http_build_query($payload), 'aefij3ldaase_ase23fdAdwjnA2123fFa'); 
```

Javascript:

``` html
<script src="http://crypto-js.googlecode.com/svn/tags/3.1.2/build/rollups/hmac-sha256.js"></script>
<script>
    var xhr = new XMLHttpRequest(),
        secret = 'aefij3ldaase_ase23fdAdwjnA2123fFa',
        body = 'api_key=' + 'dgsdrij234fsdfgkhr' + '&nounce=' + Date.now() + '&offer_hash=234fds827h&margin=50';
    
    var seal = CryptoJS.HmacSHA256(body, secret);

    xhr.open('POST', 'https://www.paxful.com/api/offer/list');
    xhr.setRequestHeader('Content-Type', 'text/plain');
    xhr.setRequestHeader('Accept', 'application/json');  
    xhr.send(body + '&apiseal=' + seal);    
</script>
```

##Request and response formats

Valid Request headers **MUST** contain

```
Accept: application/json
Content-Type: text/plain
```

Response formats are always in json containing data *status* *timestamp* and *data* or *error* (in case of errors)

Example of a successful response

``` javascript
{
    "status": "success",
    "timestamp": 1455032576,
    "data": {
        "success": true,
        "offer_hash": "23hA0_Agf3"
    }
}
```

Example of error response

``` javascript
{
    "status": "error",
    "timestamp": 1455032576,
    "error": {
        "code": 404,
        "message": "Not Found"
    }
}
```

All Responses are expected to have status code 200