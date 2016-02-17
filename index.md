##Authentication

For authentication, you need to generate your API key under your Paxful account settings in developer tab

Example of request content
```
apikey=c3KJ7M5qw2SKSrw3QnQA8D2DHZCpwTlx&nonce=1455035029943&offer_hash=Agq1Bpw7oX9&apiseal=9b67236984c40a7c66892782cc3b0426833e699a1b44e1a5b44d63d82ba75767
```

In which following parameters are required:

   * apikey - Your key generated under your Paxful account settings, unique per user
   * nonce - current unix timestamp (required to protect against replay attacks)
   * apiseal - signature (digest) of the request params passed through HMAC-SHA256 construct
   
   
To generate the apiseal, you need to pass the request payload (i.e. apikey, nonce + request parameters) through hash method using the secret key provided from the UI

#####Examples
OpenSSL:

```
echo -n “apikey=c3KJ7M5qw2SKSrw3QnQA8D2DHZCpwTlx&nonce=1455035029943&offer_hash=Agq1Bpw7oX9” | openssl dgst -sha256 -hmac f8KjbW13VxrY1ziOF5j48Kd9OYxSmleT
```

```
(stdin)= 9b67236984c40a7c66892782cc3b0426833e699a1b44e1a5b44d63d82ba75767
```

PHP:

```
$payload = [
    'apikey' => 'dgsdrij234fsdfgkhr',
    'nonce' => time(),
    'offer_hash' => 'Agq1Bpw7oX9',
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
        body = 'apikey=' + 'dgsdrij234fsdfgkhr' + '&nonce=' + Date.now() + '&offer_hash=Agq1Bpw7oX9&margin=50';
    
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
Accept: application/json; version=1
Content-Type: text/plain
```

Currently there's only version=1 supported. When a new version becomes available, if no "version" is set, it will use the latest one. For compatibility you should use the version header appended to the Accept Header

Response formats are always in json containing data *status* *timestamp* and *data* or *error* (in case of errors)

Example of a successful response

``` javascript
{
    "status": "success",
    "timestamp": 1455032576,
    "data": {
        "success": true,
        "offer_hash": "Agq1Bpw7oX9"
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

Response also contains two custom header

```
X-RateLimit-Limit
X-RateLimit-Remaining
```

The _X-RateLimit-Limit_ shows your overall limit, while the _X-RateLimit-Remaining_ shows how many requests you're allowed to make until you hit your hour limit.