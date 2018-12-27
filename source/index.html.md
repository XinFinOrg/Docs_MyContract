---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python
  - javascript
  - go
  - php
  - ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---



# Introduction

Welcome to the MyContract API!
We are the leading platform for Smart Contract Creation, Deployment, Interaction and Token Offering. 
 
You can use our API to build your own smart contracts easily.
Though, an ERC gives you some technical guidelines to work with and implement smart contracts on the Ethereum network. It gives you two ways for deploying your contract, they are ERC20 and ERC223.
We have language bindings in Solidity and NodeJS! 


You can create your smart contracts using [MyContract](https://mycontract.co/). Feel free to edit it and use it as a base for your own Smart Contract Creation, Deployment, Interaction and Token Offering.

# Authentication

> Make sure to replace `04af606c-38a3-11e8-b467-0ed5f89f718b` with your API key.

MyContract uses API key to allow access to the API. You can request a new API key at our [developer portal](http://docs.xinfin.org/).

Two ways to authenticate: 

1) JWT Token - issued after signin

2) API Key based

`Authorization: 04af606c-38a3-11e8-b467-0ed5f89f718b`

<aside class="notice">
You must replace <code>04af606c-38a3-11e8-b467-0ed5f89f718b</code> with your personal API key.
</aside>

# Admin Related APIs

## adminSignup

`POST https://api.mycontract.co/api/adminSignup`

Creates a new admin account. 

```ruby
require "uri"
require "net/http"

url = URI("https://api.mycontract.co/api/adminSignup")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\nXyz123\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"firstName\"\r\n\r\nXyz\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"lastName\"\r\n\r\nazoor\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body


```

```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/adminSignup',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\nXyz123\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"firstName\"\r\n\r\nXyz\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"lastName\"\r\n\r\nazoor\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();

```

```shell

curl --location --request POST "api.mycontract.co/api/adminSignup" \
  --form "email=xyz@gmail.com" \
  --form "password=Xyz123" \
  --form "firstName=Xyz" \
  --form "lastName=azoor"
  ```

```python
import requests
url = 'api.mycontract.co/api/adminSignup'
payload = {'email': 'xyz@gmail.com',
'password': 'Xyz123',
'firstName': 'Xyz',
'lastName': 'azoor'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/adminSignup",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'xyz@gmail.com','password' => 'Xyz123','firstName' => 'Xyz','lastName' => 'azoor'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/adminSignup"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "xyz@gmail.com")
  _ = writer.WriteField("password", "Xyz123")
  _ = writer.WriteField("firstName", "Xyz")
  _ = writer.WriteField("lastName", "azoor")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> The above command returns JSON structured like this:

```json
{
  "email": "xyz@gmail.com",
  "password": "Xyz123",
  "firstName": "Xyz",
  "lastName": "azoor"
}
```

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
password | password | yes
firstName | String | yes
lastName | String | yes

includes:
- Welcome admin
- welcome user

## Admin Login

`POST https://api.mycontract.co/api/adminLogin`

On Sign In Admin is issued JWT tokens.

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/adminLogin")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\nXyz123\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body


```

```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/adminLogin',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\nXyz123\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();

```

```shell
curl --location --request POST "api.mycontract.co/api/adminLogin" \
  --form "email=xyz@gmail.com" \
  --form "password=Xyz123"
  ```

```python
import requests
url = 'api.mycontract.co/api/adminLogin'
payload = {'email': 'xyz@gmail.com',
'password': 'Xyz123'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/adminLogin",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'xyz@gmail.com','password' => 'Xyz123'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/adminLogin"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "xyz@gmail.com")
  _ = writer.WriteField("password", "Xyz123")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> The above command returns JSON structured like this:

```json
{
  "email": "xyz@gmail.com",
  "password": "Xyz123"
}
```

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
password | password | yes


## payment for Admin

`POST https://api.mycontract.co/api/paymentforAdmin`

Payment for admin generates OTP for secured transaction.


```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/paymentforAdmin")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"otpValue\"\r\n\r\n8379\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```

```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/paymentforAdmin',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"otpValue\"\r\n\r\n8379\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();

```

```shell
curl --location --request POST "api.mycontract.co/api/paymentforAdmin" \
  --form "otpValue=8379"
  ```

```python
import requests
url = 'api.mycontract.co/api/paymentforAdmin'
payload = {'otpValue': '8379'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/getClientData/uid/bd973760-fc4f-11e8-a1be-3b62c8107ed1",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract/api/paymentforAdmin"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("otpValue", "8379")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> The above command returns JSON structured like this:

```json
{
  "otpValue": "8379",
  
}
```

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
otpValue | Number | yes





## admin KYC upload

`POST https://api.mycontract.co/api/adminKYCupload`

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/adminKYCupload")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"firstName\"\r\n\r\nXyz\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"lastName\"\r\n\r\nazoor\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"ISDCode\"\r\n\r\n+91\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"contactNumber\"\r\n\r\n9952634510\r\n\"KYCDoc1\"' = '')\"KYCDoc2\"' = '')\"KYCDoc3\"' = '')------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName1\"\r\n\r\npassport\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName2\"\r\n\r\nofficial doc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName3\"\r\n\r\nofficial doc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```

```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/adminKYCupload',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"firstName\"\r\n\r\nXyz\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"lastName\"\r\n\r\nazoor\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"ISDCode\"\r\n\r\n+91\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"contactNumber\"\r\n\r\n9952634510\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"KYCDoc1\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"KYCDoc2\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"KYCDoc3\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName1\"\r\n\r\npassport\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName2\"\r\n\r\nofficial doc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName3\"\r\n\r\nofficial doc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();

```

```shell
curl --location --request POST "api.mycontract.co/api/adminKYCupload" \
  --form "email=xyz@gmail.com" \
  --form "firstName=xyz" \
  --form "lastName=azoor" \
  --form "ISDCode=+91" \
  --form "contactNumber=9256562203" \
  --form "KYCDoc1=@" \
  --form "KYCDoc2=@" \
  --form "KYCDoc3=@" \
  --form "kycDocName1=passport" \
  --form "kycDocName2=official doc" \
  --form "kycDocName3=official doc"
  ```

```python
import requests
url = 'api.mycontract.co/api/adminKYCupload'
payload = {'email': 'xyz@gmail.com',
'firstName': 'xyz',
'lastName': 'azoor',
'ISDCode': '+91',
'contactNumber': '9823561212',
'kycDocName1': 'passport',
'kycDocName2': 'official doc',
'kycDocName3': 'official doc'}
files = {('KYCDoc1': open('','rb'),('KYCDoc2': open('','rb'),('KYCDoc3': open('','rb')}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/adminKYCupload",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'xyz@gmail.com','firstName' => 'xyz','lastName' => 'azoor','ISDCode' => '+91','contactNumber' => '9823561212','KYCDoc1'=> new CURLFILE(''),'KYCDoc2'=> new CURLFILE(''),'KYCDoc3'=> new CURLFILE(''),'kycDocName1' => 'passport','kycDocName2' => 'official doc','kycDocName3' => 'official doc'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/adminKYCupload"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "xyz@gmail.com")
  _ = writer.WriteField("firstName", "xyz")
  _ = writer.WriteField("lastName", "azoor")
  _ = writer.WriteField("ISDCode", "+91")
  _ = writer.WriteField("contactNumber", "9823561212")
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  _ = writer.WriteField("kycDocName1", "passport")
  _ = writer.WriteField("kycDocName2", "official doc")
  _ = writer.WriteField("kycDocName3", "official doc")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> The above command returns JSON structured like this:

```json
{
  "email": "xyz@gmail.com",
  "firstName": "Xyz",
  "lastName": "azoor",
  "ISDCode": "+91",
  "contactNumber": "9952526390",
  "KYCDoc1": "",
  "KYCDoc2": "",
  "KYCDoc3": "",
  "KYCDocName1": "",
  "KYCDocName2": "",
  "KYCDocName3": ""

}
```

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
firstName | String | yes
lastName | String | yes
ISDCode | Number | yes
contactNumber | Number | yes
KYCDoc1 | | yes
KYCDoc2 | | yes
KYCDoc3 | | yes
KYCDocName1 | | yes
KYCDocName2 | | yes
KYCDocName3 | | yes


## admin Balance

`GET https://api.mycontract.co/api/adminBalance`

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/adminBalance")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/api/adminBalance',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();

```

```shell
curl --location --request GET "api.mycontract.co/api/adminBalance"


  ```

```python
import requests
url = 'api.mycontract.co/api/adminBalance'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/adminBalance",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/adminBalance"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```



## client Data  

`GET https://api.mycontract.co/api/clientList`

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/clientList")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/api/clientList',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});


```

```shell
curl --location --request GET "api.mycontract.co/api/clientList"


  ```

```python
import requests
url = 'api.mycontract.co/api/clientList'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)



```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/clientList",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/clientList"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```



## update Client KYC Data

`POST https://api.mycontract.co/api/updateClientKYCData/uid/80bafd60-044a-11e9-b109-9bf6dd27fbd4`





```shell
curl --location --request POST "api.mycontract.co/api/updateClientKYCData/uid/80bafd60-044a-11e9-b109-9bf6dd27fbd4" \
  --form "kycStatus=false" \
  --form "accountStatus=active"
  ```
  ```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/updateClientKYCData/uid/80bafd60-044a-11e9-b109-9bf6dd27fbd4")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycStatus\"\r\n\r\nfalse\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"accountStatus\"\r\n\r\nactive\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/updateClientKYCData/uid/80bafd60-044a-11e9-b109-9bf6dd27fbd4',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycStatus\"\r\n\r\nfalse\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"accountStatus\"\r\n\r\nactive\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();

```
```python
import requests
url = 'api.mycontract.co/api/updateClientKYCData/uid/80bafd60-044a-11e9-b109-9bf6dd27fbd4'
payload = {'kycStatus': 'false',
'accountStatus': 'active'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/updateClientKYCData/uid/80bafd60-044a-11e9-b109-9bf6dd27fbd4",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('kycStatus' => 'false','accountStatus' => 'active'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/updateClientKYCData/uid/80bafd60-044a-11e9-b109-9bf6dd27fbd4"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("kycStatus", "false")
  _ = writer.WriteField("accountStatus", "active")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```


> The above command returns JSON structured like this:

```json
{
  "kycStatus": "false",
  "accountStatus": "active"
}
```

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
kycStatus | String | yes
accountState | String | yes

## admin Logout

`GET https://api.mycontract.co/api/adminLogout`



```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/adminLogout")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```


```shell
curl --location --request GET "api.mycontract.co/adminLogout"



  ```

```python
import requests
url = 'api.mycontract.co/adminLogout'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/adminLogout',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```




```php

<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/adminLogout",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/adminLogout"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```

## Get Balances

`GET https://api.mycontract.co/api/getBalances`

```shell

curl --location --request GET "api.mycontract.co/getBalances"

```

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/getBalances")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```
```python

import requests
url = 'api.mycontract.co/getBalances'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript

var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/getBalances',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/getBalances",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go

package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/getBalances"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

# Client Profile Related APIs

## Login

`POST http://api.mycontract.co/api/login`

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/api/login")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@xinfin.org\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\nWht@1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
   ```
   ```php
   <?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract/api/login",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'xyz@xinfin.org','password' => 'Wht@1234'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract/api/login"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "xyz@xinfin.org")
  _ = writer.WriteField("password", "Wht@1234")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```




```python
import requests
url = 'api.mycontract.co/api/login'
payload = {'email': 'demo@xinfin.org',
'password': 'Wht@1234'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```


```shell
curl --location --request POST "api.mycontract.co/api/login" \
  --form "email=demo@gmail.com" \
  --form "password=Wht@1234"
```


```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract',
  'path': '/api/login',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\nWht@1234\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```



> The above command returns JSON structured like this:

```json
{
  "email": "demo@gmail.com",
  "password": "Wht@1234"
}
```
### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
password | password | yes



<aside class="success">
Remember — You must login first to access users APIs.
</aside>


## Sign Up

`POST http://api.mycontract.co/api/adminId/965a81c0-0505-11e9-9fb9-d56ad143a4b6/signup`


```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/api/adminId/51923ed0-fed8-11e8-a664-9b0fd9d26b09/signup")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\n123456\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract/api/adminId/51923ed0-fed8-11e8-a664-9b0fd9d26b09/signup",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'xyz@gmail.com','password' => '123456'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go
package# Admin APIs

import # Admin APIs
  "fmt"# Admin APIs
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract/api/adminId/51923ed0-fed8-11e8-a664-9b0fd9d26b09/signup"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "xyz@gmail.com")
  _ = writer.WriteField("password", "123456")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

```python
import requests
url = 'api.mycontract/api/adminId/51923ed0-fed8-11e8-a664-9b0fd9d26b09/signup'
payload = { 'fname': 'abc',
'lname': 'xyz',
  'email': 'xyz@gmail.com',
'password': '123456'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
# Admin APIs
# Admin APIs0-fed8-11e8-a664-9b0fd9d26b09/signup',
# Admin APIs
# Admin APIs
# Admin APIs
# Admin APIs
var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\n123456\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```shell
curl --location --request POST "api.mycontract/api/adminId/51923ed0-fed8-11e8-a664-9b0fd9d26b09/signup" \
  --form "fname=abc" \
  --form "lname=xyz" \
  --form "email=xyz@gmail.com" \
  --form "password=123456"
  ```
> The above command returns JSON structured like this:

```json
{
  "fname": "abcd",
  "lname": "xyz",
  "email": "xyz@gmail.com",
  "password": "Wht@1234"
}
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
firstname | String | yes
lastname | String | yes
email | String | yes
password | password | yes



<aside class="success">
Remember — You must create an account first.
</aside>


## Get Project Info

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/icoDashboardSetup/project/demo")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```


```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract/icoDashboardSetup/project/demo",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>

```



```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract/icoDashboardSetup/project/demo"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

```python
import requests
url = 'api.mycontract/api/projectInfo'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```shell
  curl --location --request GET "api.mycontract/api/profileDetails"
```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract',
  'path': '/api/profileDetails',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```


### HTTP Request

`GET http://api.mycontract.com/icoDashboardSetup/project/demo`




## Get Project Details

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/api/api/profileDetails")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body


```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract/api/api/profileDetails",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract/api/api/profileDetails"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

```python
import requests
url = 'api.mycontract/icoDashboardSetup/project/demo'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```shell
  curl --location --request GET "api.mycontract.co/icoDashboardSetup/project/demo"
```

```javascript
var settings = {
  "url": "api.mycontract/icoDashboardSetup/project/demo",
  "method": "GET",
  "timeout": 0,
};
$.ajax(settings).done(function (response) {
  console.log(response);
});
```





### HTTP Request

`GET http://api.mycontract/api/profileDetails<ID>`



##Client Logout

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/api/logout")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract/api/logout",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>

```



```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract/api/logout"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```


```python
import requests
url = 'api.mycontract/api/logout'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```

```shell
  curl --location --request GET "api.mycontract/api/logout"
```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract',
  'path': '/api/logout',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```


### HTTP Request

`GET http://api.mycontract.co/api/logout/<ID>`


##Client forgot password

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/api/forgotPassword")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```
```php

<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract/api/forgotPassword",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go

package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract/api/forgotPassword"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```




```python
import requests
url = 'api.mycontract/api/forgotPassword'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```shell
  curl --location --request GET "api.mycontract/api/forgotPassword"


```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': require "uri"
require "net/http"

url = URI("api.mycontract/api/forgotPassword")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_bodyact'
  'path': '/aprequire "uri"
require "net/http"

url = URI("api.mycontract/api/forgotPassword")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_bodyPassword',
  'headers': {require "uri"
require "net/http"

url = URI("api.mycontract/api/forgotPassword")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

> The above command returns JSON structured like this:

```json
{
  
  "email": "abc@gmail.com"
}
```


### HTTP Request

`GET http://api.mycontract.co/api/forgotpassword/<ID>`

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes




##Client update password



```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/api/updatePassword")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\n123456\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"resetId\"\r\n\r\n$2a$08$jmtFYVH7ZVSBapiFZuEzoOOInSxjQkbPvmXaH2X7Gr1YBDk3du8n.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body

```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract/api/updatePassword",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'xyz@gmail.com','password' => '123456','resetId' => '$2a$08$jmtFYVH7ZVSBapiFZuEzoOOInSxjQkbPvmXaH2X7Gr1YBDk3du8n.'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract/api/updatePassword"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "xyz@gmail.com")
  _ = writer.WriteField("password", "123456")
  _ = writer.WriteField("resetId", "$2a$08$jmtFYVH7ZVSBapiFZuEzoOOInSxjQkbPvmXaH2X7Gr1YBDk3du8n.")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```


```python
import requests
url = 'api.mycontract/api/updatePassword'
payload = {'email': 'xyz@gmail.com',
'password': '123456',
'resetId': '$2a$08$jmtFYVH7ZVSBapiFZuEzoOOInSxjQkbPvmXaH2X7Gr1YBDk3du8n.'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```shell
  curl --location --request POST "api.mycontract/api/updatePassword" \
  --form "email=xyz@gmail.com" \
  --form "password=123456" \
  --form "resetId=$2a$08$jmtFYVH7ZVSBapiFZuEzoOOInSxjQkbPvmXaH2X7Gr1YBDk3du8n."
```

```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract',
  'path': '/api/updatePassword',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\n123456\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"resetId\"\r\n\r\n$2a$08$jmtFYVH7ZVSBapiFZuEzoOOInSxjQkbPvmXaH2X7Gr1YBDk3du8n.\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```

### HTTP Request

`POST http://api.mycontract/api/updatePassword/<ID>`

> The above command returns JSON structured like this:

```json
{
  
  "email": "abc@gmail.com",
  "password": "12345",
  "resetId": "$2a$08$jmtFYVH7ZVSBapiFZuEzoOOInSxjQkbPvmXaH2X7Gr1YBDk3du8n"
 
}
```


### HTTP Request

`GET http://api.mycontract.co/api/forgotpassword/<ID>`

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
password | Number | yes
resetId | String | yes


##Client check existence

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/api/checkExistence")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract/api/checkExistence",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```



```go
package main

importClient Related APIs
  "fmtClient Related APIs
  "os"Client Related APIs
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := 'api.mycontract/api/checkExistence'
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

```python
import requests
url := 'api.mycontract/api/checkExistence'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```shell
 curl --location --request GET "api.mycontract/api/checkExistence"


```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract',
  'path': '/api/checkExistence',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

### HTTP Request

`GET http://api.mycontract.co/api/checkExistence/<ID>`

> The above command returns JSON structured like this:

```json
{
  
  "email": "abc@gmail.com"

}
```
### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes

##Client KYC document Upload
 `POST http://api.mycontract.co/api/KYCdocUpload`

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract/api/KYCdocUpload")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"firstName\"\r\n\r\nxyz\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"lastName\"\r\n\r\nazoor\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"ISDCode\"\r\n\r\n+91\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"contactNumber\"\r\n\r\n9876543210\r\n\"KYCDoc1\"' = '')\"KYCDoc2\"' = '')\"KYCDoc3\"' = '')------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName1\"\r\n\r\npassport\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName2\"\r\n\r\nofficial doc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName3\"\r\n\r\nofficial doc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```
```shell
curl --location --request POST "api.mycontract.co/api/KYCdocUpload" \
  --form "email=xyz@gmail.com" \
  --form "firstName=Xyz" \
  --form "lastName=azoor" \
  --form "ISDCode=+91" \
  --form "contactNumber=9876543210" \
  --form "KYCDoc1=@" \
  --form "KYCDoc2=@" \
  --form "KYCDoc3=@" \
  --form "kycDocName1=passport" \
  --form "kycDocName2=official doc" \
  --form "kycDocName3=official doc"
```
```python
import requests
url = 'api.mycontract.co/api/KYCdocUpload'
payload = {'email': 'xyzz@gmail.com',
'firstName': 'Xyz',
'lastName': 'azoor',
'ISDCode': '+91',
'contactNumber': '9876543210',
'kycDocName1': 'passport',
'kycDocName2': 'official doc',
'kycDocName3': 'official doc'}
files = {('KYCDoc1': open('','rb'),('KYCDoc2': open('','rb'),('KYCDoc3': open('','rb')}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/KYCdocUpload',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nxyzz@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"firstName\"\r\n\r\nXyz\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"lastName\"\r\n\r\npilankar\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"ISDCode\"\r\n\r\n+91\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"contactNumber\"\r\n\r\n9876543210\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"KYCDoc1\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"KYCDoc2\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"KYCDoc3\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName1\"\r\n\r\npassport\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName2\"\r\n\r\nofficial doc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName3\"\r\n\r\nofficial doc\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/KYCdocUpload",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'xyzz@gmail.com','firstName' => 'Xyz','lastName' => 'pilankar','ISDCode' => '+91','contactNumber' => '9876543210','KYCDoc1'=> new CURLFILE(''),'KYCDoc2'=> new CURLFILE(''),'KYCDoc3'=> new CURLFILE(''),'kycDocName1' => 'passport','kycDocName2' => 'official doc','kycDocName3' => 'official doc'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/KYCdocUpload"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "xyzz@gmail.com")
  _ = writer.WriteField("firstName", "Xyz")
  _ = writer.WriteField("lastName", "pilankar")
  _ = writer.WriteField("ISDCode", "+91")
  _ = writer.WriteField("contactNumber", "9876543210")
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  _ = writer.WriteField("kycDocName1", "passport")
  _ = writer.WriteField("kycDocName2", "official doc")
  _ = writer.WriteField("kycDocName3", "official doc")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/buyFirstPackage"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("otpValue", "8027")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```
> The above command returns JSON structured like this:

```json
{
  
  "email": "abc@gmail.com",
   "firstName": "abc",
    "lastName": "def",
     "ISDCode": "+91",
      "contactNumber": "9865986530",
       "KYCDoc1": "",
       "KYCDoc2": "",
       "KYCDoc3": "",
       "KYCDocName1": "",
       "KYCDocName2": "",

       "KYCDocName3": ""



}
```

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
firstName | String | yes
lastName | String | yes
ISDCode | Number | yes
contactNumber | Number | yes
KYCDoc1 | | yes
KYCDoc2 | | yes
KYCDoc3 | | yes
KYCDocName1 | | yes
KYCDocName2 | | yes
KYCDocName3 | | yes

## Get Balances

`GET http://api.mycontract.co/api/getBalances`

```shell
curl --location --request GET "api.mycontract.co/getBalances"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/getBalances")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```
```python
import requests
url = 'api.mycontract.co/getBalances'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```
```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/getBalances',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/getBalances",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/getBalances"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```


## First Package Payment

`GET http://api.mycontract.co/api/buyFirstPackage`

```shell
curl --location --request POST "api.mycontract.co/buyFirstPackage" \
  --form "otpValue=8027"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/buyFirstPackage")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"otpValue\"\r\n\r\n8027\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```
```python
import requests
url = 'api.mycontract.co/buyFirstPackage'
payload = {'otpValue': '8027'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/buyFirstPackage',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"otpValue\"\r\n\r\n8027\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```php

<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/buyFirstPackage",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('otpValue' => '8027'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/buyFirstPackage"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("otpValue", "8027")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```
> The above command returns JSON structured like this:

```json
{
  
  "otpValue": "8027"
}
```

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
otpValue | Number | yes



# Client Contract Creation and Delpoyment

## Create ERC20 Contract 

`POST http://api.mycontract.co/api/createERC20Contract`

```shell
curl --location --request POST "api.mycontract.co/api/createERC20Contract" \
  --form "tokenName=Demo" \
  --form "tokenSymbol=Dmo" \
  --form "tokenDecimals=18" \
  --form "tokenSupply=1000000" \
  --form "ethRate=1" \
  --form "bonusRate=0" \
  --form "isPausable=true" \
  --form "isBurnable=true" \
  --form "isMintable=true" \
  --form "isUpgradeable=true"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/createERC20Contract")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSymbol\"\r\n\r\nDmo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenDecimals\"\r\n\r\n18\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSupply\"\r\n\r\n1000000\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"ethRate\"\r\n\r\n1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"bonusRate\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isPausable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isBurnable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isMintable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isUpgradeable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body

```
```python
import requests
url = 'api.mycontract.co/api/createERC20Contract'
payload = {'tokenName': 'Demo',
'tokenSymbol': 'Dmo',
'tokenDecimals': '18',
'tokenSupply': '1000000',
'ethRate': '1',
'bonusRate': '0',
'isPausable': 'true',
'isBurnable': 'true',
'isMintable': 'true',
'isUpgradeable': 'true'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/createERC20Contract',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSymbol\"\r\n\r\nDmo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenDecimals\"\r\n\r\n18\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSupply\"\r\n\r\n1000000\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"ethRate\"\r\n\r\n1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"bonusRate\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isPausable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isBurnable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isMintable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isUpgradeable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/createERC20Contract",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('tokenName' => 'Demo','tokenSymbol' => 'Dmo','tokenDecimals' => '18','tokenSupply' => '1000000','ethRate' => '1','bonusRate' => '0','isPausable' => 'true','isBurnable' => 'true','isMintable' => 'true','isUpgradeable' => 'true'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>

```
```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/createERC20Contract"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("tokenName", "Demo")
  _ = writer.WriteField("tokenSymbol", "Dmo")
  _ = writer.WriteField("tokenDecimals", "18")
  _ = writer.WriteField("tokenSupply", "1000000")
  _ = writer.WriteField("ethRate", "1")
  _ = writer.WriteField("bonusRate", "0")
  _ = writer.WriteField("isPausable", "true")
  _ = writer.WriteField("isBurnable", "true")
  _ = writer.WriteField("isMintable", "true")
  _ = writer.WriteField("isUpgradeable", "true")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```
> The above command returns JSON structured like this:

```json
{
  
  "tokenName": "Demo",
  "tokenSymbol": "DMO",
  "tokenDecimals": "18",
  "tokenSupply": "100000",
  "ethRate": "1",
  "bonusRate": "0",
  "isPausable":"true",
"isBurnable":"true",
"isMintable":"true",
"isUpgradable":"true"
}
```
### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
tokenName | String | yes
tokenSymbol | String | yes
tokenDecimals | Number | yes
tokenSupply | Number | yes
ethRate | Number | yes
bonusRate | Number | yes
isPausable | String | yes
isBurnable | String | yes
isMintable | String | yes
isUpgradable | String | yes


## Create ERC223 Contract 

`POST http://api.mycontract.co/api/createERC223Contract`

```shell
curl --location --request POST "api.mycontract.co/api/createERC223Contract" \
  --form "tokenName=Demo" \
  --form "tokenSymbol=Dmo" \
  --form "tokenDecimals=18" \
  --form "tokenSupply=1000000" \
  --form "ethRate=1" \
  --form "bonusRate=0" \
  --form "isPausable=true" \
  --form "isBurnable=true" \
  --form "isMintable=true" \
  --form "isUpgradeable=true"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/createERC223Contract")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSymbol\"\r\n\r\nDmo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenDecimals\"\r\n\r\n18\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSupply\"\r\n\r\n1000000\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"ethRate\"\r\n\r\n1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"bonusRate\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isPausable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isBurnable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isMintable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isUpgradeable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```

```python
import requests
url = 'api.mycontract.co/api/createERC223Contract'
payload = {'tokenName': 'Demo',
'tokenSymbol': 'Dmo',
'tokenDecimals': '18',
'tokenSupply': '1000000',
'ethRate': '1',
'bonusRate': '0',
'isPausable': 'true',
'isBurnable': 'true',
'isMintable': 'true',
'isUpgradeable': 'true'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/createERC223Contract',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSymbol\"\r\n\r\nDmo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenDecimals\"\r\n\r\n18\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSupply\"\r\n\r\n1000000\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"ethRate\"\r\n\r\n1\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"bonusRate\"\r\n\r\n0\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isPausable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isBurnable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isMintable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isUpgradeable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/createERC223Contract",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('tokenName' => 'Demo','tokenSymbol' => 'Dmo','tokenDecimals' => '18','tokenSupply' => '1000000','ethRate' => '1','bonusRate' => '0','isPausable' => 'true','isBurnable' => 'true','isMintable' => 'true','isUpgradeable' => 'true'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/createERC223Contract"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("tokenName", "Demo")
  _ = writer.WriteField("tokenSymbol", "Dmo")
  _ = writer.WriteField("tokenDecimals", "18")
  _ = writer.WriteField("tokenSupply", "1000000")
  _ = writer.WriteField("ethRate", "1")
  _ = writer.WriteField("bonusRate", "0")
  _ = writer.WriteField("isPausable", "true")
  _ = writer.WriteField("isBurnable", "true")
  _ = writer.WriteField("isMintable", "true")
  _ = writer.WriteField("isUpgradeable", "true")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```
> The above command returns JSON structured like this:

```json
{
  
  "tokenName": "Demo",
  "tokenSymbol": "DMO",
  "tokenDecimals": "18",
  "tokenSupply": "100000",
  "ethRate": "1",
  "bonusRate": "0",
  "isPausable":"true",
"isBurnable":"true",
"isMintable":"true",
"isUpgradable":"true"
}
```



### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
tokenName | String | yes
tokenSymbol | String | yes
tokenDecimals | Number | yes
tokenSupply | Number | yes
ethRate | Number | yes
bonusRate | Number | yes
isPausable | String | yes
isBurnable | String | yes
isMintable | String | yes
isUpgradable | String | yes

## Create ERC721Contract 

`POST http://api.mycontract.co/api/createERC721Contract`


```shell
curl --location --request POST "api.mycontract.co/api/createERC721Contract" \
  --form "tokenName=Demo" \
  --form "tokenSymbol=Dmo" \
  --form "isPausable=true" \
  --form "isBurnable=true" \
  --form "isOwnable=true"

```

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/createERC721Contract")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSymbol\"\r\n\r\nDmo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isPausable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isBurnable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isOwnable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body

```
```python
import requests
url = 'api.mycontract.co/api/createERC721Contract'
payload = {'tokenName': 'Demo',
'tokenSymbol': 'Dmo',
'isPausable': 'true',
'isBurnable': 'true',
'isOwnable': 'true'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/createERC721Contract',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenSymbol\"\r\n\r\nDmo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isPausable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isBurnable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isOwnable\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/createERC721Contract",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('tokenName' => 'Demo','tokenSymbol' => 'Dmo','isPausable' => 'true','isBurnable' => 'true','isOwnable' => 'true'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/createERC721Contract"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("tokenName", "Demo")
  _ = writer.WriteField("tokenSymbol", "Dmo")
  _ = writer.WriteField("isPausable", "true")
  _ = writer.WriteField("isBurnable", "true")
  _ = writer.WriteField("isOwnable", "true")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```
> The above command returns JSON structured like this:

```json
{
  
  "tokenName": "Demo",
  "tokenSymbol": "DMO",
"isPausable":"true",
"isBurnable":"true",
"isOwnable":"true"
}
```



### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
tokenName | String | yes
tokenSymbol | String | yes
isPausable | String | yes
isBurnable | String | yes
isOwnable | String | yes

## Automatic Deployer 

`POST http://api.mycontract.co/api/automaticDeployer`


```shell
curl --location --request POST "api.mycontract.co/api/automaticDeployer" \
  --form "coinName=Demo" \
  --form "network=testnet"
  ```

  ```ruby
  require "uri"
require "net/http"

url = URI("api.mycontract.co/api/automaticDeployer")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"coinName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"network\"\r\n\r\ntestnet\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```
```python
import requests
url = 'api.mycontract.co/api/automaticDeployer'
payload = {'coinName': 'Demo',
'network': 'testnet'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript

var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/automaticDeployer',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"coinName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"network\"\r\n\r\ntestnet\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/automaticDeployer",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('coinName' => 'Demo','network' => 'testnet'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/automaticDeployer"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("coinName", "Demo")
  _ = writer.WriteField("network", "testnet")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()

  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```
> The above command returns JSON structured like this:

```json
{
 "coinName": "Demo",
 "network": "testnet" 
}
```



### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
coinName | String | yes
network | String | yes


## Project Contract Data

`POST http://api.mycontract.co/api/projectContractData`

```shell
curl --location --request POST "api.mycontract.co/api/projectContractData" \
  --form "tokenName=Demo"
  ```

  ```ruby
  require "uri"
require "net/http"

url = URI("api.mycontract.co/api/projectContractData")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body

```
```python
import requests
url = 'api.mycontract.co/api/projectContractData'
payload = {'tokenName': 'Demo'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/projectContractData',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/projectContractData",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('tokenName' => 'Demo'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/projectContractData"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("tokenName", "Demo")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```
> The above command returns JSON structured like this:

```json
{
  "tokenName": "Demo"
}
```

### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
tokenName | String | yes


# Tokenization Platforms

## Get Site Configuration

`GET http://api.mycontract.co/api/siteConfiguration/project/Demo/getSiteConfiguration`

```shell
curl --location --request GET "api.mycontract.co/api/siteConfiguration/project/Demo/getSiteConfiguration"

```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/siteConfiguration/project/Demo/getSiteConfiguration")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```
```python
requests
url = 'api.mycontract.co/api/siteConfiguration/project/Demo/getSiteConfiguration'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```
```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/api/siteConfiguration/project/Demo/getSiteConfiguration',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/siteConfiguration/project/Demo/getSiteConfiguration",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/siteConfiguration/project/Demo/getSiteConfiguration"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

> The above command returns JSON structured like this:

```json
{
  "tokenName": "Demo"
}
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
tokenName | String | yes


## Update Site Configuration

`POST http://api.mycontract.co/api/siteConfiguration/project/Demo/updateSiteConfiguration`

```shell
curl --location --request POST "api.mycontract.co/api/siteConfiguration/project/Demo/updateSiteConfiguration" \
  --form "siteLogo=@" \
  --form "siteName=Demo" \
  --form "softCap=100" \
  --form "hardCap=9000" \
  --form "startDate=2018-12-16 19:55:36.614+05:30" \
  --form "endDate=2018-12-26 19:55:36.614+05:30" \
  --form "homeURL=www.api.mycontract.co" \
  --form "minimumContribution=2"
  ```
  ```ruby
  
  require "uri"
require "net/http"

url = URI("api.mycontract.co/api/siteConfiguration/project/Demo/updateSiteConfiguration")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "\"siteLogo\"' = '')------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"siteName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"softCap\"\r\n\r\n100\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"hardCap\"\r\n\r\n9000\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"startDate\"\r\n\r\n2018-12-16 19:55:36.614+05:30\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"endDate\"\r\n\r\n2018-12-26 19:55:36.614+05:30\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"homeURL\"\r\n\r\nwww.api.mycontract.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"minimumContribution\"\r\n\r\n2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```
```python
 import requests
url = 'api.mycontract.co/api/siteConfiguration/project/Demo/updateSiteConfiguration'
payload = {'siteName': 'Demo',
'softCap': '100',
'hardCap': '9000',
'startDate': '2018-12-16 19:55:36.614+05:30',
'endDate': '2018-12-26 19:55:36.614+05:30',
'homeURL': 'www.api.mycontract.co',
'minimumContribution': '2'}
files = {('siteLogo': open('','rb')}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/api/siteConfiguration/project/Demo/updateSiteConfiguration',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"siteLogo\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"siteName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"softCap\"\r\n\r\n100\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"hardCap\"\r\n\r\n9000\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"startDate\"\r\n\r\n2018-12-16 19:55:36.614+05:30\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"endDate\"\r\n\r\n2018-12-26 19:55:36.614+05:30\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"homeURL\"\r\n\r\nwww.api.mycontract.co\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"minimumContribution\"\r\n\r\n2\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/siteConfiguration/project/Demo/updateSiteConfiguration",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('siteLogo'=> new CURLFILE(''),'siteName' => 'Demo','softCap' => '100','hardCap' => '9000','startDate' => '2018-12-16 19:55:36.614+05:30','endDate' => '2018-12-26 19:55:36.614+05:30','homeURL' => 'www.api.mycontract.co','minimumContribution' => '2'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/siteConfiguration/project/Demo/updateSiteConfiguration"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  _ = writer.WriteField("siteName", "Demo")
  _ = writer.WriteField("softCap", "100")
  _ = writer.WriteField("hardCap", "9000")
  _ = writer.WriteField("startDate", "2018-12-16 19:55:36.614+05:30")
  _ = writer.WriteField("endDate", "2018-12-26 19:55:36.614+05:30")
  _ = writer.WriteField("homeURL", "www.api.mycontract.co")
  _ = writer.WriteField("minimumContribution", "2")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```
> The above command returns JSON structured like this:

```json
{
  "siteLogo": "",
  "siteName": "Demo",
  "softCap": "100",
  "hardCap": "900",
  "startDate": "2018-12-16 19:55:36.614+05:30",
  "endDate": "2018-12-26 19:55:36.614+05:30",
  "homeURL": "",
  "minimumContribution": ""
}
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
siteLogo | Image | yes
siteName | String | yes
softCap | Number | yes
hardCap | Number | yes
startDate | Number | yes
endDate | Number | yes
homeURL | String | yes
minimumContribution | Number | yes



## Get All Transactions

`GET http://api.mycontract.co/transaction/project/demo`

```shell
curl --location --request GET "api.mycontract.co/transaction/project/demo"

```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/transaction/project/demo")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```
```python
import requests
url = 'api.mycontract.co/transaction/project/demo'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/transaction/project/demo',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```php

<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/transaction/project/demo",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/transaction/project/demo"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```


## Get All ICO User Data

`GET http://api.mycontract.co/api/icoDashboardSetup/project/Demo/kyctab/getICOUsersData`

```shell

curl --location --request GET "api.mycontract.co/icoDashboardSetup/project/Demo/kyctab/getICOUsersData"
```

```ruby

require "uri"
require "net/http"

url = URI("api.mycontract.co/icoDashboardSetup/project/Demo/kyctab/getICOUsersData")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```

```python

import requests
url = 'api.mycontract.co/icoDashboardSetup/project/Demo/kyctab/getICOUsersData'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript

var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/icoDashboardSetup/project/Demo/kyctab/getICOUsersData',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/icoDashboardSetup/project/Demo/kyctab/getICOUsersData",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go

package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/icoDashboardSetup/project/Demo/kyctab/getICOUsersData"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```


## Get Single User Data

`GET http://api.mycontract.co/api/icoDashboardSetup/project/Demo/userId/123/getUserData`

```shell
curl --location --request GET "api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/getUserData"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/getUserData")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```
```python
import requests
url = 'api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/getUserData'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)
```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/icoDashboardSetup/project/Demo/userId/123/getUserData',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```php

<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/getUserData",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/getUserData"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```



## Update Single User Data

`POST http://api.mycontract.co/api/icoDashboardSetup/project/Demo/userId/123/updateUserData`

```shell
curl --location --request POST "api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/updateUserData" \
  --form "kycStatus=true" \
  --form "accountStatus=true"
  ```
  ```ruby

  require "uri"
require "net/http"

url = URI("api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/updateUserData")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycStatus\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"accountStatus\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```

```python
import requests
url = 'api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/updateUserData'
payload = {'kycStatus': 'true',
'accountStatus': 'true'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/icoDashboardSetup/project/Demo/userId/123/updateUserData',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycStatus\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"accountStatus\"\r\n\r\ntrue\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/updateUserData",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('kycStatus' => 'true','accountStatus' => 'true'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/icoDashboardSetup/project/Demo/userId/123/updateUserData"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("kycStatus", "true")
  _ = writer.WriteField("accountStatus", "true")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```






> The above command returns JSON structured like this:

```json
{
  "kycStatus": "true",
  "accountStatus": "true"
}
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
kycStatus | String | yes
accountStatus | String | yes

## project information

`GET http://api.mycontract.co/api/icoDashboardSetup/project/Demo`

```shell
curl --location --request GET "api.mycontract.co/api/icoDashboardSetup/project/Demo"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/api/icoDashboardSetup/project/Demo")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```

```python
import requests
url = 'api.mycontract.co/api/icoDashboardSetup/project/Demo'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/api/icoDashboardSetup/project/Demo',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();

```

```php

<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/api/icoDashboardSetup/project/Demo",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>

```
```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/api/icoDashboardSetup/project/Demo"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```

## Token Transfer

`POST http://api.mycontract.co/api/icoDashboard/transaction/project/demo/tokenTrasfer`

```shell
curl --location --request POST "api.mycontract.co/icoDashboard/transaction/project/demo/tokenTrasfer" \
  --form "tokenAmount=1000" \
  --form "tokenAddress=0xF6409e8113a70830996eD62F552316958A658ef4"
```

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/icoDashboard/transaction/project/demo/tokenTrasfer")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenAmount\"\r\n\r\n1000\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenAddress\"\r\n\r\n0xF6409e8113a70830996eD62F552316958A658ef4\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body
```

```python

import requests
url = 'api.mycontract.co/icoDashboard/transaction/project/demo/tokenTrasfer'
payload = {'tokenAmount': '1000',
'tokenAddress': '0xF6409e8113a70830996eD62F552316958A658ef4'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```
```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/icoDashboard/transaction/project/demo/tokenTrasfer',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenAmount\"\r\n\r\n1000\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"tokenAddress\"\r\n\r\n0xF6409e8113a70830996eD62F552316958A658ef4\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/icoDashboard/transaction/project/demo/tokenTrasfer",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('tokenAmount' => '1000','tokenAddress' => '0xF6409e8113a70830996eD62F552316958A658ef4'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```
```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/icoDashboard/transaction/project/demo/tokenTrasfer"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("tokenAmount", "1000")
  _ = writer.WriteField("tokenAddress", "0xF6409e8113a70830996eD62F552316958A658ef4")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```



> The above command returns JSON structured like this:

```json
{
  "tokenAmount": "1000",
  "tokenAddress": "0xF6409e8113a70830996eD62F552316958A658ef4"
}
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
tokenAmount | Number | yes
tokenAddress | String | yes

## pending Transaction Transfer

`GET http://api.mycontract.co/api/icoDashboard/transaction/project/demo/initiateTransferReq`

```shell
curl --location --request POST "api.mycontract.co/icoDashboard/transaction/project/Demo/initiateTransferReq" \
  --header "Content-Type: application/json" \
  --data "{\"transactionId\":[\"e66d1f20-08d8-11e9-9b07-8da6f2c251c1\",\"03e55f40-08d9-11e9-9b07-8da6f2c251c1\"]}"

```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/icoDashboard/transaction/project/Demo/initiateTransferReq")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["Content-Type"] = "application/json"
request.body = "{\"transactionId\":[\"e66d1f20-08d8-11e9-9b07-8da6f2c251c1\",\"03e55f40-08d9-11e9-9b07-8da6f2c251c1\"]}"

response = http.request(request)
puts response.read_body
```

```python
import requests
url = 'api.mycontract.co/icoDashboard/transaction/project/Demo/initiateTransferReq'
payload = "{\"transactionId\":[\"e66d1f20-08d8-11e9-9b07-8da6f2c251c1\",\"03e55f40-08d9-11e9-9b07-8da6f2c251c1\"]}"
headers = {
  'Content-Type': 'application/json'
}
response = requests.request('POST', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```javascript

var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/icoDashboard/transaction/project/Demo/initiateTransferReq',
  'headers': {
    'Content-Type': 'application/json'
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData =  "{\"transactionId\":[\"e66d1f20-08d8-11e9-9b07-8da6f2c251c1\",\"03e55f40-08d9-11e9-9b07-8da6f2c251c1\"]}";

req.write(postData);

req.end();
```

```php

<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/icoDashboard/transaction/project/Demo/initiateTransferReq",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS =>"{\"transactionId\":[\"e66d1f20-08d8-11e9-9b07-8da6f2c251c1\",\"03e55f40-08d9-11e9-9b07-8da6f2c251c1\"]}",
  CURLOPT_HTTPHEADER => array(
    "Content-Type: application/json"
  ),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "strings"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/icoDashboard/transaction/project/Demo/initiateTransferReq"
  method := "POST"

  payload := strings.NewReader("{\"transactionId\":[\"e66d1f20-08d8-11e9-9b07-8da6f2c251c1\",\"03e55f40-08d9-11e9-9b07-8da6f2c251c1\"]}")

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Add("Content-Type", "application/json")

  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```



> The above command returns JSON structured like this:

```json
{
  "Content-Type": "application/json"
}
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
contentType | String | yes


# User Account Related APIs 

##User Signup

`POST http://api.mycontract.co/Demo/userSignup`

```shell
curl --location --request POST "api.mycontract.co/Demo/userSignup" \
  --form "email=abc@gmail.com" \
  --form "password=123456" \
  --form "firstName=abc" \
  --form "lastName=pilankar" \
  --form "countryId=india" \
  --form "projectName=Demo"
```

```ruby

require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/userSignup")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nakshay@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\n123456\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"firstName\"\r\n\r\nakshay\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"lastName\"\r\n\r\npilankar\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"countryId\"\r\n\r\nindia\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"projectName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body

```

```python
import requests
url = 'api.mycontract.co/Demo/userSignup'
payload = {'email': 'abc@gmail.com',
'password': '123456',
'firstName': 'abc',
'lastName': 'pilankar',
'countryId': 'india',
'projectName': 'Demo'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/userSignup',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nakshay@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\n123456\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"firstName\"\r\n\r\nakshay\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"lastName\"\r\n\r\npilankar\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"countryId\"\r\n\r\nindia\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"projectName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/userSignup",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'abc@gmail.com','password' => '123456','firstName' => 'abc','lastName' => 'pilankar','countryId' => 'india','projectName' => 'Demo'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>

```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/userSignup"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "abc@gmail.com")
  _ = writer.WriteField("password", "123456")
  _ = writer.WriteField("firstName", "abc")
  _ = writer.WriteField("lastName", "pilankar")
  _ = writer.WriteField("countryId", "india")
  _ = writer.WriteField("projectName", "Demo")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```
> The above command returns JSON structured like this:

```json
{
  "email": "abc@gmail.com",
  "password": "123456",
  "firstName": "abc",
  "lastName": "def",
  "countryId": "india",
  "projectName": "Demo",
}
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
password | Number | yes
firstName | String | yes
lastName | String | yes
countryId | String | yes
projectName | String | yes


## User Login

`POST http://api.mycontract.co/Demo/userLogin`

```shell
curl --location --request POST "api.mycontract.co/Demo/userLogin" \
  --form "email=abc@gmail.com" \
  --form "password=123456" \
  --form "projectName=Demo"
```

```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/userLogin")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nakshay@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\n123456\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"projectName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body


```

```python
import requests
url = 'api.mycontract.co/Demo/userLogin'
payload = {'email': 'abc@gmail.com',
'password': '123456',
'projectName': 'Demo'}
files = {}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/userLogin',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nakshay@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"password\"\r\n\r\n123456\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"projectName\"\r\n\r\nDemo\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/userLogin",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'abc@gmail.com','password' => '123456','projectName' => 'Demo'),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/userLogin"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "abc@gmail.com")
  _ = writer.WriteField("password", "123456")
  _ = writer.WriteField("projectName", "Demo")
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```








> The above command returns JSON structured like this:

```json
{
  "email": "abc@gmail.com",
  "password": "123456",
  "projectName": "Demo"
}
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
password | Number | yes
projectName | String | yes



## KYC Upload

`POST http://api.mycontract.co/Demo/user/kycUpload`

```shell
curl --location --request POST "api.mycontract.co/Demo/user/kycUpload" \
  --form "email=abc@gmail.com" \
  --form "isdCode=+91" \
  --form "contactNumber=98" \
  --form "country=india" \
  --form "kycDocName1=passport" \
  --form "kycDoc1=@" \
  --form "kycDocName2=official Id" \
  --form "kycDoc2=@" \
  --form "kycDocName3=official Id" \
  --form "kycDoc3=@"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/user/kycUpload")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Post.new(url)
request["content-type"] = 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW'
request.body = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nakshay@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isdCode\"\r\n\r\n+91\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"contactNumber\"\r\n\r\n98\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"country\"\r\n\r\nindia\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName1\"\r\n\r\npassport\r\n\"kycDoc1\"' = '')------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName2\"\r\n\r\nofficial Id\r\n\"kycDoc2\"' = '')------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName3\"\r\n\r\nofficial Id\r\n\"kycDoc3\"' = '')------WebKitFormBoundary7MA4YWxkTrZu0gW--"

response = http.request(request)
puts response.read_body

```
```python
import requests
url = 'api.mycontract.co/Demo/user/kycUpload'
payload = {'email': 'abc@gmail.com',
'isdCode': '+91',
'contactNumber': '98',
'country': 'india',
'kycDocName1': 'passport',
'kycDocName2': 'official Id',
'kycDocName3': 'official Id'}
files = {('kycDoc1': open('','rb'),('kycDoc2': open('','rb'),('kycDoc3': open('','rb')}
headers = {}
response = requests.request('POST', url, headers = headers, data = payload, files = files, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```javascript
var https = require('https');

var options = {
  'method': 'POST',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/user/kycUpload',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = "------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"email\"\r\n\r\nakshay@gmail.com\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"isdCode\"\r\n\r\n+91\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"contactNumber\"\r\n\r\n98\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"country\"\r\n\r\nindia\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName1\"\r\n\r\npassport\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDoc1\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName2\"\r\n\r\nofficial Id\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDoc2\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDocName3\"\r\n\r\nofficial Id\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW\r\nContent-Disposition: form-data; name=\"kycDoc3\"; filename=\"{Insert_File_Name}\"\r\nContent-Type: \"{Insert_File_Content_Type}\"\r\n\r\n{Insert_File_Content}\r\n------WebKitFormBoundary7MA4YWxkTrZu0gW--";

req.setHeader('content-type', 'multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW');

req.write(postData);

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/user/kycUpload",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "POST",
  CURLOPT_POSTFIELDS => array('email' => 'abc@gmail.com','isdCode' => '+91','contactNumber' => '98','country' => 'india','kycDocName1' => 'passport','kycDoc1'=> new CURLFILE(''),'kycDocName2' => 'official Id','kycDoc2'=> new CURLFILE(''),'kycDocName3' => 'official Id','kycDoc3'=> new CURLFILE('')),
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "bytes"
  "mime/multipart"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/user/kycUpload"
  method := "POST"

  payload := &bytes.Buffer{}
  writer := multipart.NewWriter(payload)
  _ = writer.WriteField("email", "abc@gmail.com")
  _ = writer.WriteField("isdCode", "+91")
  _ = writer.WriteField("contactNumber", "98")
  _ = writer.WriteField("country", "india")
  _ = writer.WriteField("kycDocName1", "passport")
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  _ = writer.WriteField("kycDocName2", "official Id")
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  _ = writer.WriteField("kycDocName3", "official Id")
  // add your file name in the next statement in place of path
  file, err := os.Open(path)
  defer file.Close()
  part, err := writer.CreateFormFile("file", filepath.Base(path))
  _, err := io.Copy(part, file)
  err := writer.Close()
  if err != nil {  fmt.Println(err)}


  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, payload)

  if err != nil {
    fmt.Println(err)
  }
  req.Header.Set("Content-Type", writer.FormDataContentType())
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```








> The above command returns JSON structured like this:

```json
{
  "email": "abc@gmail.com",
  "isdCode": "+91",
  "contactNumber": "02224565",
  "country": "India",
  "kycDocName1": "passport",
  "kycDoc1": "",
   "kycDocName2": "official Id",
  "kycDoc2": "",
   "kycDocName3": "official Id",
  "kycDoc3": ""
  }
```




### Query Parameters

Argument | Type | Required
--------- | ------- | -----------
email | String | yes
isdCode | Number | yes
contactNumber | Number | yes
kycDocName1 | String | yes
kycDoc1 | String | yes
kycDocName2 | String | yes
kycDoc2 | String | yes
kycDocName3 | String | yes
kycDoc3 | String | yes



## Get Dashboard Data

`GET http://api.mycontract.co/Demo/user/dashboard`

```shell
curl --location --request GET "api.mycontract.co/Demo/user/dashboard"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/user/dashboard")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```
```python
import requests
url = 'api.mycontract.co/Demo/user/dashboard'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/user/dashboard',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/user/dashboard",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/user/dashboard"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```


## Get Prices

`POST http://api.mycontract.co/Demo/user/getPrices`

```shell
shell
curl --location --request GET "api.mycontract.co/Demo/user/getPrices"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/user/getPrices")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body


```
```python
import requests
url = 'api.mycontract.co/Demo/user/getPrices'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/user/getPrices',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();


```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/user/getPrices",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/user/getPrices"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```



## Check Balances

`POST http://api.mycontract.co/Demo/user/api/checkBalances`

```shell
curl --location --request GET "api.mycontract.co/Demo/user/api/checkBalances"

```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/user/api/checkBalances")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```
```python

import requests
url = 'api.mycontract.co/Demo/user/api/checkBalances'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)


```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/user/api/checkBalances',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/user/api/checkBalances",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/user/api/checkBalances"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}

```







## Check Token Balances

`POST http://api.mycontract.co/Demo/user/api/checkTokenBalances`

```shell
curl --location --request GET "api.mycontract.co/Demo/user/api/checkTokenBalances"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/user/api/checkTokenBalances")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```
```python
import requests
url = 'api.mycontract.co/Demo/user/api/checkTokenBalances'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/user/api/checkTokenBalances',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/user/api/checkTokenBalances",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/user/api/checkTokenBalances"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```





## Get Transaction Log

`POST http://api.mycontract.co/Demo/user/api/getTransactions`

```shell
curl --location --request GET "api.mycontract.co/Demo/user/api/getTransactions"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/user/api/getTransactions")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body
```
```python
import requests
url = 'api.mycontract.co/Demo/user/api/getTransactions'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/user/api/getTransactions',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/user/api/getTransactions",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/user/api/getTransactions"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```






## Get Bitcoin Transaction Log

`POST http://api.mycontract.co/Demo/user/api/getBitcoinTransactions`
```shell
curl --location --request GET "api.mycontract.co/Demo/user/api/getBitcoinTransactions"
```
```ruby
require "uri"
require "net/http"

url = URI("api.mycontract.co/Demo/user/api/getBitcoinTransactions")

http = Net::HTTP.new(url.host, url.port)

request = Net::HTTP::Get.new(url)

response = http.request(request)
puts response.read_body

```
```python
import requests
url = 'api.mycontract.co/Demo/user/api/getBitcoinTransactions'
payload = {}
headers = {}
response = requests.request('GET', url, headers = headers, data = payload, allow_redirects=False, timeout=undefined, allow_redirects=false)
print(response.text)

```

```javascript
var https = require('https');

var options = {
  'method': 'GET',
  'hostname': 'api.mycontract.co',
  'path': '/Demo/user/api/getBitcoinTransactions',
  'headers': {
  }
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "api.mycontract.co/Demo/user/api/getBitcoinTransactions",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => false,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);
$err = curl_error($curl);

curl_close($curl);

if ($err) {
  echo "cURL Error #:" . $err;
} else {
  echo $response;
} ?>
```

```go
package main

import (
  "fmt"
  "os"
  "path/filepath"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "api.mycontract.co/Demo/user/api/getBitcoinTransactions"
  method := "GET"

  client := &http.Client {
    CheckRedirect: func(req *http.Request, via []*http.Request) error {
      return http.ErrUseLastResponse
    },
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```



