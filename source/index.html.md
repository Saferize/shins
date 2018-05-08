---
title: Saferize API v1
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<h1 id="Saferize-API">Saferize API v1</h1>

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

The Saferize API is organized around [REST](http://en.wikipedia.org/wiki/Representational_State_Transfer). Our API has predictable, resource-oriented URLs, and uses HTTP response codes to indicate API errors. We support [cross-origin resource sharing](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing), allowing you to interact securely with our API from a client-side web application (though you should never expose your secret API key in any public website's client-side code). [JSON](http://www.json.org/) is returned by all API responses, including errors.

To make the API as explorable as possible, accounts have test mode and live mode API keys. There is no "switch" for changing between modes, just use the appropriate key to perform a live or test transaction.

Be sure to subscribe to Saferize's API announcements mailing list to receive information on new additions and changes.

The requests in the right sidebar are designed to work as is.

`NOTE` - We HIGHLY suggest using Saferize's [Developer Console Tool](https://console.saferize.com) as opposed to making raw calls.

Base URLs:

* <a href="http://api.saferize.com">http://api.saferize.com</a>

<a href="https://saferize.com/terms-of-service/">Terms of service</a>
Email: <a href="mailto:devs@saferize.com">Saferize Customer Support</a> 

# Authentication

- HTTP Authentication, scheme: bearer 
- Learn more about <a href="https://jwt.io/introduction/">JSON Web Tokens</a>.

<h1 id="Saferize-API-Developer">Developer</h1>

The [Developer](#tocSdeveloper) object represents the publisher. You can create, retrieve and update a developer. You may also view all the apps associated with the developer.

## createDeveloper

<a id="opIdcreateDeveloper"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://api.saferize.com/developer \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
POST http://api.saferize.com/developer HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/developer',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/developer',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.post 'http://api.saferize.com/developer',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.post('http://api.saferize.com/developer', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/developer");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://api.saferize.com/developer", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /developer`

*Create a Developer*

The `Developer` object is created when a new developer registers.

> Body parameter

```json
{
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}
```

<h3 id="createDeveloper-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|The new developer to be created|
|» firstName|body|string|true|Developer's first name.|
|» lastName|body|string|true|Developer's last name.|
|» email|body|string|true|Developer's primary email address.|
|» mobilePhone|body|string|true|Developer's primary mobile phone number. The format should be XXXYYYZZZZ (no dashes or parentheses).|
|» company|body|string|false|Developer's company name.|
|» country|body|string|false|The country in which the developer resides, or in which the company is legally established. This should be an ISO 3166-1 alpha-2 country code. For example, if you are in the United States and the business for which you're creating an account is legally represented in Canada, you would use `CA` as the country for the account being created.|

> Example responses

```json
{
  "id": 1234,
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}
```

<h3 id="createDeveloper-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The created developer|[Developer](#schemadeveloper)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|The request conflicts with another request|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getDeveloper

<a id="opIdgetDeveloper"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/developer/me \
  -H 'Accept: */*' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/developer/me HTTP/1.1
Host: api.saferize.com

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/developer/me',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'*/*',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/developer/me',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/developer/me',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/developer/me', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/developer/me");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"*/*"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/developer/me", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /developer/me`

*Retrieve the Developer*

Retrieves the developer object associated with the current session.

> Example responses

<h3 id="getDeveloper-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The developer object|[Developer](#schemadeveloper)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## updateDeveloper

<a id="opIdupdateDeveloper"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://api.saferize.com/developer/me \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
PUT http://api.saferize.com/developer/me HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/developer/me',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "firstName": "Jane",
  "lastName": "Doe",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/developer/me',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.put 'http://api.saferize.com/developer/me',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.put('http://api.saferize.com/developer/me', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/developer/me");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://api.saferize.com/developer/me", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /developer/me`

*Update the developer*

Updates the developer object associated with the current session. For security reasons, email cannot be updated through this endpoint.

> Body parameter

```json
{
  "firstName": "Jane",
  "lastName": "Doe",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}
```

<h3 id="updateDeveloper-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|The developer properties to be updated to.|
|» firstName|body|string|true|Developer's first name.|
|» lastName|body|string|true|Developer's last name.|
|» mobilePhone|body|string|true|Developer's primary mobile phone number. The format should be XXXYYYZZZZ (no dashes or parentheses).|
|» company|body|string|false|Developer's company name.|
|» country|body|string|false|The country in which the developer resides, or in which the company is legally established. This should be an ISO 3166-1 alpha-2 country code. For example, if you are in the United States and the business for which you're creating an account is legally represented in Canada, you would use `CA` as the country for the account being created.|

> Example responses

```json
{
  "id": 1234,
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}
```

<h3 id="updateDeveloper-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The updated developer.|[Developer](#schemadeveloper)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getApps

<a id="opIdgetApps"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/developer/me/apps \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/developer/me/apps HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/developer/me/apps',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/developer/me/apps',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/developer/me/apps',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/developer/me/apps', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/developer/me/apps");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/developer/me/apps", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /developer/me/apps`

*Retrieve Developer's apps*

Retrieves the apps associated with the developer.

> Example responses

```json
[
  {
    "id": 1,
    "name": "Saferize Example",
    "platforms": [
      "ANDROID",
      "IOS"
    ],
    "category": "GAME",
    "timeRestriction": "ENABLED",
    "status": "PUBLISHED",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    "shortDescription": "Lorem ipsum dolor sit amet.",
    "urlName": "string",
    "age": 5,
    "email": "developer@example.com"
  }
]
```

<h3 id="getApps-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An array of apps|[[App]](#schemaapp)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

<h1 id="Saferize-API-App">App</h1>

This is an object representing an [App](#tocSapp) that implements Saferize. You can retrieve it to see it's many properties and [configuration](#tocSappconfig).

## createApp

<a id="opIdcreateApp"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://api.saferize.com/app \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
POST http://api.saferize.com/app HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Saferize Example",
  "platforms": [
    "ANDROID",
    "IOS"
  ],
  "category": "GAME",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 5,
  "email": "developer@example.com"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.post 'http://api.saferize.com/app',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.post('http://api.saferize.com/app', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://api.saferize.com/app", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /app`

*Create an App*

With a developer account you can create apps. 

Although all `App` object properties must be filled out in order to [publish](#changestatus) it, we don't expect you to have it all figured out immediately. As a matter of fact, in order to create an `App` object, the only field you need to specify is the App's `name`.

> Body parameter

```json
{
  "name": "Saferize Example",
  "platforms": [
    "ANDROID",
    "IOS"
  ],
  "category": "GAME",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 5,
  "email": "developer@example.com"
}
```

<h3 id="createApp-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|The new app to be created.|
|» name|body|string|true|The name of the app.|
|» platforms|body|[string]|false|An array of enums that specify what platforms are supported by this app.|
|» category|body|string|false|One of the predifned values indicating the category of the app.|
|» description|body|string|false|A description of the app.|
|» shortDescription|body|string|false|A short description of the app.|
|» urlName|body|string|false|The partial url name of this app on Saferize.|
|» age|body|integer(int64)|false|Minimum recommended age of app users.|
|» email|body|string|false|The app developer's email.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» platforms|ANDROID|
|» platforms|IOS|
|» platforms|WINDOWS|
|» platforms|MAC_OS|
|» platforms|LINUX|
|» platforms|APPLE_TV|
|» platforms|ANDROID_TV|
|» platforms|APPLE_WATCH|
|» platforms|ANDROID_WATCH|
|» platforms|XBOX|
|» platforms|NINTENDO|
|» platforms|PLAYSTATION|

|Parameter|Value|
|---|---|
|» category|GAME|
|» category|MEDIA|

> Example responses

```json
{
  "id": 1,
  "name": "Saferize Example",
  "platforms": [
    "ANDROID",
    "IOS"
  ],
  "category": "GAME",
  "timeRestriction": "ENABLED",
  "status": "PUBLISHED",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 5,
  "email": "developer@example.com"
}
```

<h3 id="createApp-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The created app.|[App](#schemaapp)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|The request conflicts with another request|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getApp

<a id="opIdgetApp"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/app/{id} \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/app/{id} HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/app/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/app/{id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/app/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}`

*Retrieve an App*

Retrieves the app object associated with the id.

<h3 id="getApp-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|The identifier of the app to retrieve.|

> Example responses

```json
{
  "id": 1,
  "name": "Saferize Example",
  "platforms": [
    "ANDROID",
    "IOS"
  ],
  "category": "GAME",
  "timeRestriction": "ENABLED",
  "status": "PUBLISHED",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 5,
  "email": "developer@example.com"
}
```

<h3 id="getApp-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the app object associated with the id.|[App](#schemaapp)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="success">
This operation does not require authentication
</aside>

## changeAppAttributes

<a id="opIdchangeAppAttributes"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://api.saferize.com/app/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
PUT http://api.saferize.com/app/{id} HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Saferize Example Changed",
  "platforms": [
    "MAC_OS",
    "IOS"
  ],
  "category": "MEDIA",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 4,
  "email": "developer@example.com"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.put 'http://api.saferize.com/app/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.put('http://api.saferize.com/app/{id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://api.saferize.com/app/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}`

*Change App's attributes*

Changes the descriptive attributes of the app by setting the values of the parameters passed. Bear in mind that this endpoint does not alter the core configuration of the app.
Any parameters not provided will be changed to `null`.

> Body parameter

```json
{
  "name": "Saferize Example Changed",
  "platforms": [
    "MAC_OS",
    "IOS"
  ],
  "category": "MEDIA",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 4,
  "email": "developer@example.com"
}
```

<h3 id="changeAppAttributes-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|App fields to be updated.|
|» name|body|string|true|The name of the app.|
|» platforms|body|[string]|false|An array of enums that specify what platforms are supported by this app.|
|» category|body|string|false|One of the predifned values indicating the category of the app.|
|» description|body|string|false|A description of the app.|
|» shortDescription|body|string|false|A short description of the app.|
|» urlName|body|string|false|The partial url name of this app on Saferize.|
|» age|body|integer(int64)|false|Minimum recommended age of app users.|
|» email|body|string|false|The app developer's email.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|» platforms|ANDROID|
|» platforms|IOS|
|» platforms|WINDOWS|
|» platforms|MAC_OS|
|» platforms|LINUX|
|» platforms|APPLE_TV|
|» platforms|ANDROID_TV|
|» platforms|APPLE_WATCH|
|» platforms|ANDROID_WATCH|
|» platforms|XBOX|
|» platforms|NINTENDO|
|» platforms|PLAYSTATION|
|» category|GAME|
|» category|MEDIA|

> Example responses

```json
{
  "id": 1,
  "name": "Saferize Example",
  "platforms": [
    "ANDROID",
    "IOS"
  ],
  "category": "GAME",
  "timeRestriction": "ENABLED",
  "status": "PUBLISHED",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 5,
  "email": "developer@example.com"
}
```

<h3 id="changeAppAttributes-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The updated app.|[App](#schemaapp)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## createKey

<a id="opIdcreateKey"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://api.saferize.com/app/{id}/key \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
POST http://api.saferize.com/app/{id}/key HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/key',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '-----BEGIN PUBLIC KEY----- MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEApofmdG+zACt1kHNlQciwyg3DuRW5za33FuBH+Zb8JoixthvtZNgee6+TkbCEWGmC9+cIJLTnialKdDUxlr5JpCtJnIpaiD++Ic5AINpE0zqhD4obR8eN7m5lcKGuNwShFxB/lc+IFHeEf5MkPcU+nSkJIV74F0XJIqNeewGxNayJ/bbIuOS4gMI0/lU18ua3OsLvVmJZyXObiYq3nMfSwWKuhfLqRMSSfICEDjnVAq3+F8/lxoqAxbC0gFZC3CdOjINgMJYr3XY6fo9oAkrt4yjSO9kAqQxaHiLqJ87gjjQEKaBzlejTM3/iJBamQUCF3VPZ3y7AoSCEWBEA5xhvXQIDAQAB -----END PUBLIC KEY-----';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/key',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.post 'http://api.saferize.com/app/{id}/key',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.post('http://api.saferize.com/app/{id}/key', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/key");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://api.saferize.com/app/{id}/key", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /app/{id}/key`

*Create a Key to authenticate an App*

To be able to use your app your app, you must authenticate your app by using a public-key authentication scheme (we only allows RSA encryption).  Please take a look at [how to generate a private-public key set](https://en.wikibooks.org/wiki/Cryptography/Generate_a_keypair_using_OpenSSL).

Your apps' keys carry many privileges, so be sure to keep your private key secret! Do not share your private keys in publicly accessible areas such GitHub, client-side code, and so forth.

The returned access key is a piece of your login credential and will be used to generate a Json Web Token in order for your app to interact with our platform.

> Body parameter

```json
"-----BEGIN PUBLIC KEY----- MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEApofmdG+zACt1kHNlQciwyg3DuRW5za33FuBH+Zb8JoixthvtZNgee6+TkbCEWGmC9+cIJLTnialKdDUxlr5JpCtJnIpaiD++Ic5AINpE0zqhD4obR8eN7m5lcKGuNwShFxB/lc+IFHeEf5MkPcU+nSkJIV74F0XJIqNeewGxNayJ/bbIuOS4gMI0/lU18ua3OsLvVmJZyXObiYq3nMfSwWKuhfLqRMSSfICEDjnVAq3+F8/lxoqAxbC0gFZC3CdOjINgMJYr3XY6fo9oAkrt4yjSO9kAqQxaHiLqJ87gjjQEKaBzlejTM3/iJBamQUCF3VPZ3y7AoSCEWBEA5xhvXQIDAQAB -----END PUBLIC KEY-----"
```

<h3 id="createKey-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[RSAPublicKey](#schemarsapublickey)|true|RSA public key.|

> Example responses

```json
"031e58c6-a92c-453d-920d-33ad279392de"
```

<h3 id="createKey-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Returns the newly created access key if the public key was valid.|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|The request conflicts with another request|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## rollKey

<a id="opIdrollKey"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://api.saferize.com/app/{id}/key \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
PUT http://api.saferize.com/app/{id}/key HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/key',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '-----BEGIN PUBLIC KEY----- MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEApofmdG+zACt1kHNlQciwyg3DuRW5za33FuBH+Zb8JoixthvtZNgee6+TkbCEWGmC9+cIJLTnialKdDUxlr5JpCtJnIpaiD++Ic5AINpE0zqhD4obR8eN7m5lcKGuNwShFxB/lc+IFHeEf5MkPcU+nSkJIV74F0XJIqNeewGxNayJ/bbIuOS4gMI0/lU18ua3OsLvVmJZyXObiYq3nMfSwWKuhfLqRMSSfICEDjnVAq3+F8/lxoqAxbC0gFZC3CdOjINgMJYr3XY6fo9oAkrt4yjSO9kAqQxaHiLqJ87gjjQEKaBzlejTM3/iJBamQUCF3VPZ3y7AoSCEWBEA5xhvXQIDAQAB -----END PUBLIC KEY-----';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/key',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.put 'http://api.saferize.com/app/{id}/key',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.put('http://api.saferize.com/app/{id}/key', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/key");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://api.saferize.com/app/{id}/key", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}/key`

*Roll the Key that authenticates an App*

If you believe your key has been compromised, roll the key with a newly generated public key.

Although your access key will remain the same, you will NOT be able to use your old public key any longer. For this reason, make sure you have your corresponding private key stored safely.

> Body parameter

```json
"-----BEGIN PUBLIC KEY----- MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEApofmdG+zACt1kHNlQciwyg3DuRW5za33FuBH+Zb8JoixthvtZNgee6+TkbCEWGmC9+cIJLTnialKdDUxlr5JpCtJnIpaiD++Ic5AINpE0zqhD4obR8eN7m5lcKGuNwShFxB/lc+IFHeEf5MkPcU+nSkJIV74F0XJIqNeewGxNayJ/bbIuOS4gMI0/lU18ua3OsLvVmJZyXObiYq3nMfSwWKuhfLqRMSSfICEDjnVAq3+F8/lxoqAxbC0gFZC3CdOjINgMJYr3XY6fo9oAkrt4yjSO9kAqQxaHiLqJ87gjjQEKaBzlejTM3/iJBamQUCF3VPZ3y7AoSCEWBEA5xhvXQIDAQAB -----END PUBLIC KEY-----"
```

<h3 id="rollKey-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[RSAPublicKey](#schemarsapublickey)|true|RSA public key.|

> Example responses

```json
"031e58c6-a92c-453d-920d-33ad279392de"
```

<h3 id="rollKey-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the access key if the public key was valid.|string|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## changeTimeRestriction

<a id="opIdchangeTimeRestriction"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH http://api.saferize.com/app/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
PATCH http://api.saferize.com/app/{id} HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "op": "replace",
  "path": "/status",
  "value": "PUBLISHED"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.patch 'http://api.saferize.com/app/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.patch('http://api.saferize.com/app/{id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "http://api.saferize.com/app/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /app/{id}`

*Update App time restrictions*

Time restrictions is a Saferize internal feature. If you would like parents to manage sessions, set time limits, and arbitrarily pause/resume the app, you can set the time restrictions flag value to `ENABLED`. This is also the default value set upon [app creation](/#createapp).

Otherwise, you may disable this feature by setting the time restrictions flag value to `DISABLED`.

> Body parameter

```json
{
  "op": "replace",
  "path": "/status",
  "value": "PUBLISHED"
}
```

<h3 id="changeTimeRestriction-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[JsonPatch](#schemajsonpatch)|true|A JsonPatch operation `replace`.|

> Example responses

```json
{
  "id": 1,
  "name": "Saferize Example",
  "platforms": [
    "ANDROID",
    "IOS"
  ],
  "category": "GAME",
  "timeRestriction": "ENABLED",
  "status": "PUBLISHED",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 5,
  "email": "developer@example.com"
}
```

<h3 id="changeTimeRestriction-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the app object with an updated field.|[App](#schemaapp)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## changeStatus

<a id="opIdchangeStatus"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH http://api.saferize.com/app/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
PATCH http://api.saferize.com/app/{id} HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "op": "replace",
  "path": "/status",
  "value": "PUBLISHED"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.patch 'http://api.saferize.com/app/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.patch('http://api.saferize.com/app/{id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "http://api.saferize.com/app/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /app/{id}`

*Update app status*

When the app is created, the initial status is `DRAFT`. Once the app is ready to be published, you may change the status to `IN_REVIEW` via this endpoint. This will initialize the process of publishing the app, and will remain `IN_REVIEW` until Saferize Customer Support approves it, upon which it will become `PUBLISHED`.

Firstly, you must [Authenticate the app](/#createkey). In order to publish the app, all [App](/#tocSapp) fields must be populated. In addition to this, the app must have have at least one [Screenshot](/#uploadscreenshot) and one [Logo](/#uploadlogo) uploaded. 

To delete the app, set the status to `DELETED`.

You can learn more on how to go from creating an app to publishing one in our [Saferize Quick Start](http://google.com).

If you need any help throughout this process, please contact the Saferize Customer Support.

> Body parameter

```json
{
  "op": "replace",
  "path": "/status",
  "value": "PUBLISHED"
}
```

<h3 id="changeStatus-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[JsonPatch](#schemajsonpatch)|true|A JsonPatch operation `replace`.|

> Example responses

```json
{
  "id": 1,
  "name": "Saferize Example",
  "platforms": [
    "ANDROID",
    "IOS"
  ],
  "category": "GAME",
  "timeRestriction": "ENABLED",
  "status": "PUBLISHED",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 5,
  "email": "developer@example.com"
}
```

<h3 id="changeStatus-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the app object with an updated field.|[App](#schemaapp)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## updateAppConfig

<a id="opIdupdateAppConfig"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://api.saferize.com/app/{id}/config \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
PUT http://api.saferize.com/app/{id}/config HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/config',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "webhookUrl": "https://example.saferize.com",
  "autoPauseSessionsInterval": 30,
  "autoRejectWaitTime": 259200,
  "validatorName": "Microtransaction"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/config',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.put 'http://api.saferize.com/app/{id}/config',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.put('http://api.saferize.com/app/{id}/config', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/config");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://api.saferize.com/app/{id}/config", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}/config`

*Update App configuration*

Updates the accompanying configuration object of the app. Take a look at the [AppConfig](/#tocSappconfig) for more details about the attributes of this object.

> Body parameter

```json
{
  "webhookUrl": "https://example.saferize.com",
  "autoPauseSessionsInterval": 30,
  "autoRejectWaitTime": 259200,
  "validatorName": "Microtransaction"
}
```

<h3 id="updateAppConfig-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[AppConfig](#schemaappconfig)|true|The new app configuration.|

> Example responses

```json
{
  "webhookUrl": "https://example.saferize.com",
  "autoPauseSessionsInterval": 30,
  "autoRejectWaitTime": 259200,
  "validatorName": "Microtransaction"
}
```

<h3 id="updateAppConfig-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the app configuration object if the update succeeded. This call will throw an error if update parameters are invalid.|[AppConfig](#schemaappconfig)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getAppConfig

<a id="opIdgetAppConfig"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/app/{id}/config \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/app/{id}/config HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/config',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/config',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/app/{id}/config',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/app/{id}/config', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/config");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/app/{id}/config", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/config`

*Retrieve App configuration*

<h3 id="getAppConfig-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|

> Example responses

```json
{
  "webhookUrl": "https://example.saferize.com",
  "autoPauseSessionsInterval": 30,
  "autoRejectWaitTime": 259200,
  "validatorName": "Microtransaction"
}
```

<h3 id="getAppConfig-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the app configuration object if it exists on the system.|[AppConfig](#schemaappconfig)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## uploadLogo

<a id="opIduploadLogo"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://api.saferize.com/app/{id}/logo \
  -H 'Content-Type: multipart/form-data' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
POST http://api.saferize.com/app/{id}/logo HTTP/1.1
Host: api.saferize.com
Content-Type: multipart/form-data
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'multipart/form-data',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/logo',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{}';
const headers = {
  'Content-Type':'multipart/form-data',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/logo',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'multipart/form-data',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.post 'http://api.saferize.com/app/{id}/logo',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'multipart/form-data',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.post('http://api.saferize.com/app/{id}/logo', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/logo");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"multipart/form-data"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://api.saferize.com/app/{id}/logo", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /app/{id}/logo`

*Upload App logo*

> Body parameter

```yaml
{}

```

<h3 id="uploadLogo-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[RFC2388](#schemarfc2388)|true|A file to upload. The file should follow the specifications of [RFC 2388](https://tools.ietf.org/html/rfc2388) (which defines file transfers for the `multipart/form-data protocol`).|

> Example responses

```json
{
  "id": 123456789,
  "url": "https://s3.us-west-1.amazonaws.com/path/to/a/file.jpg\"",
  "createdTime": 1522346229038,
  "width": 200,
  "height": 200
}
```

<h3 id="uploadLogo-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Returns the image object if the upload succeeded.|[ImageUpload](#schemaimageupload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|The request conflicts with another request|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getLogos

<a id="opIdgetLogos"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/app/{id}/logo \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/app/{id}/logo HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/logo',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/logo',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/app/{id}/logo',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/app/{id}/logo', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/logo");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/app/{id}/logo", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/logo`

*Retrieve App logo*

<h3 id="getLogos-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|

> Example responses

```json
{
  "id": 123456789,
  "url": "https://s3.us-west-1.amazonaws.com/path/to/a/file.jpg\"",
  "createdTime": 1522346229038,
  "width": 200,
  "height": 200
}
```

<h3 id="getLogos-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of image objects if they exist on the system.|[ImageUpload](#schemaimageupload)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="success">
This operation does not require authentication
</aside>

## deleteLogo

<a id="opIddeleteLogo"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE http://api.saferize.com/app/{id}/logo/{logoId} \
  -H 'Accept: */*' \
  -H 'Authorization: bearer {access-token}'

```

```http
DELETE http://api.saferize.com/app/{id}/logo/{logoId} HTTP/1.1
Host: api.saferize.com

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/logo/{logoId}',
  method: 'delete',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'*/*',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/logo/{logoId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.delete 'http://api.saferize.com/app/{id}/logo/{logoId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*',
  'Authorization': 'bearer {access-token}'
}

r = requests.delete('http://api.saferize.com/app/{id}/logo/{logoId}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/logo/{logoId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"*/*"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "http://api.saferize.com/app/{id}/logo/{logoId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /app/{id}/logo/{logoId}`

*Delete App logo*

<h3 id="deleteLogo-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|logoId|path|integer(int64)|true|Unique identifier for the image file to be deleted.|

> Example responses

<h3 id="deleteLogo-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Returns `No Content` if the deletion was succeeded.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## uploadScreenshot

<a id="opIduploadScreenshot"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://api.saferize.com/app/{id}/screenshots \
  -H 'Content-Type: multipart/form-data' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
POST http://api.saferize.com/app/{id}/screenshots HTTP/1.1
Host: api.saferize.com
Content-Type: multipart/form-data
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'multipart/form-data',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/screenshots',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{}';
const headers = {
  'Content-Type':'multipart/form-data',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/screenshots',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'multipart/form-data',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.post 'http://api.saferize.com/app/{id}/screenshots',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'multipart/form-data',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.post('http://api.saferize.com/app/{id}/screenshots', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/screenshots");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"multipart/form-data"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://api.saferize.com/app/{id}/screenshots", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /app/{id}/screenshots`

*Upload App screenshot*

> Body parameter

```yaml
{}

```

<h3 id="uploadScreenshot-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[RFC2388](#schemarfc2388)|true|A file to upload. The file should follow the specifications of [RFC 2388](https://tools.ietf.org/html/rfc2388) (which defines file transfers for the `multipart/form-data protocol`).|

> Example responses

```json
{
  "id": 123456789,
  "url": "https://s3.us-west-1.amazonaws.com/path/to/a/file.jpg\"",
  "createdTime": 1522346229038,
  "width": 200,
  "height": 200
}
```

<h3 id="uploadScreenshot-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the image object if the upload succeeded.|[ImageUpload](#schemaimageupload)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|The request conflicts with another request|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getScreenshots

<a id="opIdgetScreenshots"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/app/{id}/screenshots \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/app/{id}/screenshots HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/screenshots',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/screenshots',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/app/{id}/screenshots',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/app/{id}/screenshots', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/screenshots");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/app/{id}/screenshots", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/screenshots`

*Retrieve App screenshots*

<h3 id="getScreenshots-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|

> Example responses

```json
{
  "id": 123456789,
  "url": "https://s3.us-west-1.amazonaws.com/path/to/a/file.jpg\"",
  "createdTime": 1522346229038,
  "width": 200,
  "height": 200
}
```

<h3 id="getScreenshots-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of image objects if they exist on the system.|[ImageUpload](#schemaimageupload)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="success">
This operation does not require authentication
</aside>

## deleteScreenshot

<a id="opIddeleteScreenshot"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE http://api.saferize.com/app/{id}/screenshots/{screenshotId} \
  -H 'Accept: */*' \
  -H 'Authorization: bearer {access-token}'

```

```http
DELETE http://api.saferize.com/app/{id}/screenshots/{screenshotId} HTTP/1.1
Host: api.saferize.com

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/screenshots/{screenshotId}',
  method: 'delete',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'*/*',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/screenshots/{screenshotId}',
{
  method: 'DELETE',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => '*/*',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.delete 'http://api.saferize.com/app/{id}/screenshots/{screenshotId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*',
  'Authorization': 'bearer {access-token}'
}

r = requests.delete('http://api.saferize.com/app/{id}/screenshots/{screenshotId}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/screenshots/{screenshotId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"*/*"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "http://api.saferize.com/app/{id}/screenshots/{screenshotId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /app/{id}/screenshots/{screenshotId}`

*Delete App screenshot*

<h3 id="deleteScreenshot-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|screenshotId|path|integer(int64)|true|Unique identifier for the image file to be deleted.|

> Example responses

<h3 id="deleteScreenshot-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Returns `No Content` if the deletion was succeeded.|None|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getAppPlan

<a id="opIdgetAppPlan"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/app/{id}/plan \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/app/{id}/plan HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/plan',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/plan',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/app/{id}/plan',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/app/{id}/plan', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/plan");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/app/{id}/plan", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/plan`

*Retrieve App plan*

Retrieves the subscription plan associated with the app. Take a look at the [SubscriptionPlan](/#tocSsubscriptionplan) for more details about the attributes of this object.

As you have probably noticed, we haven't exposed an endpoint for creating a subscription plan. The reason for this is we have a separate process for creating the subscription plan. Please contact our [Support](mailto:devs@saferize.com) and we will help you get started.

<h3 id="getAppPlan-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|

> Example responses

```json
{
  "id": 123456,
  "name": "Platinum starter",
  "billingCycle": "YEARLY",
  "active": true,
  "price": 2.99
}
```

<h3 id="getAppPlan-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a subscription plan object if it exists on the system.|[SubscriptionPlan](#schemasubscriptionplan)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="success">
This operation does not require authentication
</aside>

## setImplementedAppFeatures

<a id="opIdsetImplementedAppFeatures"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://api.saferize.com/app/{id}/implementedFeatures \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
PUT http://api.saferize.com/app/{id}/implementedFeatures HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/implementedFeatures',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '[
  "CHAT",
  "ADVERTISING"
]';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/implementedFeatures',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.put 'http://api.saferize.com/app/{id}/implementedFeatures',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.put('http://api.saferize.com/app/{id}/implementedFeatures', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/implementedFeatures");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://api.saferize.com/app/{id}/implementedFeatures", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}/implementedFeatures`

*Set implemented app features*

The publicly visible list of implemented features is important for parents to know what features their kids will be interacting with. From this list you can specify which ones the parents can customize when you [set parental features](/#setparentalappfeatures).

WHen setting [AppFeatures](/#tocSappfeature) please make sure you set implemented features (by calling this endpoint), before setting the [parental features](/#setparentalappfeatures).

> Body parameter

```json
[
  "CHAT",
  "ADVERTISING"
]
```

<h3 id="setImplementedAppFeatures-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[AppFeatureNameArray](#schemaappfeaturenamearray)|false|An array of app feature names.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|body|ADVERTISING|
|body|CHAT|
|body|COMMENTS|
|body|DATA_COLLECTION|
|body|IN_APP_PURCHASES|
|body|LOCATION_SHARING|
|body|PAID_APP|
|body|PUSH_NOTIFICATIONS|
|body|SOCIAL_INTERACTION|
|body|SUBSCRIPTION|

> Example responses

```json
[
  {
    "id": 12345678,
    "appId": 12,
    "name": "DATA_COLLECTION",
    "implemented": true,
    "parentPrivilege": true
  }
]
```

<h3 id="setImplementedAppFeatures-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of app feature objects.|[[AppFeature]](#schemaappfeature)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## setParentalAppFeatures

<a id="opIdsetParentalAppFeatures"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT http://api.saferize.com/app/{id}/parentalFeatures \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
PUT http://api.saferize.com/app/{id}/parentalFeatures HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/parentalFeatures',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '[
  "CHAT",
  "ADVERTISING"
]';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/parentalFeatures',
{
  method: 'PUT',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.put 'http://api.saferize.com/app/{id}/parentalFeatures',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.put('http://api.saferize.com/app/{id}/parentalFeatures', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/parentalFeatures");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "http://api.saferize.com/app/{id}/parentalFeatures", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}/parentalFeatures`

*Set parental features*

Parental features allow parents to customize their child's experience with these features. It's up to the developer's discretion to determine which features they wish to expose. 

Please [set implemented features](/#setimplementedappfeatures) before setting parental features.

> Body parameter

```json
[
  "CHAT",
  "ADVERTISING"
]
```

<h3 id="setParentalAppFeatures-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[AppFeatureNameArray](#schemaappfeaturenamearray)|false|An array of app feature names.|

#### Enumerated Values

|Parameter|Value|
|---|---|
|body|ADVERTISING|
|body|CHAT|
|body|COMMENTS|
|body|DATA_COLLECTION|
|body|IN_APP_PURCHASES|
|body|LOCATION_SHARING|
|body|PAID_APP|
|body|PUSH_NOTIFICATIONS|
|body|SOCIAL_INTERACTION|
|body|SUBSCRIPTION|

> Example responses

```json
[
  {
    "id": 12345678,
    "appId": 12,
    "name": "DATA_COLLECTION",
    "implemented": true,
    "parentPrivilege": true
  }
]
```

<h3 id="setParentalAppFeatures-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of app feature objects. Bare in mind that the `parental` flag will be set to `false` initially.|[[AppFeature]](#schemaappfeature)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getAppFeatures

<a id="opIdgetAppFeatures"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/app/{id}/features \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/app/{id}/features HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/app/{id}/features',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/app/{id}/features',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/app/{id}/features',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/app/{id}/features', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/app/{id}/features");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/app/{id}/features", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/features`

*Retrieve App features*

<h3 id="getAppFeatures-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|

> Example responses

```json
[
  {
    "id": 12345678,
    "appId": 12,
    "name": "DATA_COLLECTION",
    "implemented": true,
    "parentPrivilege": true
  }
]
```

<h3 id="getAppFeatures-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of app feature objects if they exist on the system.|[[AppFeature]](#schemaappfeature)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

<h1 id="Saferize-API-Approval">Approval</h1>

The [Approval](#tocSapproval) object is the intersection of parent-child-app relationship and as such the most important object on our platform. A child exists as a user on the approval which is managed by the parent. On the other side of this interaction is the app which complies with the conditions contained in the approval.

An approval is created each time a child creates an account on the app. When this happens, the parent is given an opportunity to respond to the request by either approving or rejecting the app and validating the parent-child relationship. Moreover, parental changes on the approval object will reflect on how the child interacts with the app

## initiateApproval

<a id="opIdinitiateApproval"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://api.saferize.com/approval \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
POST http://api.saferize.com/approval HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/approval',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "appUser": {
    "id": 123,
    "token": "child_nickname_on_game_1",
    "app": {
      "id": 1,
      "name": "Saferize Example",
      "platforms": [
        "ANDROID",
        "IOS"
      ],
      "category": "GAME",
      "timeRestriction": "ENABLED",
      "status": "PUBLISHED",
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "shortDescription": "Lorem ipsum dolor sit amet.",
      "urlName": "string",
      "age": 5,
      "email": "developer@example.com"
    },
    "child": {
      "id": 1234567,
      "firstName": "Sofia",
      "lastName": "Smith",
      "birthDate": "2009-01-23T00:00:00.000Z",
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "gender": "FEMALE"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    }
  },
  "approvalParent": {
    "id": 123456,
    "firstName": "John",
    "lastName": "Smith",
    "mobilePhone": 41512345678,
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "email": "parent@example.com"
  },
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "statusTime": "2017-11-09T14:23:00.000Z",
  "createdTime": "2017-11-09T14:23:00.000Z",
  "status": "APPROVED",
  "parentEmail": "parent@myfamily.com",
  "parentMobilePhone": 4151234567,
  "currentState": "ACTIVE"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/approval',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.post 'http://api.saferize.com/approval',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.post('http://api.saferize.com/approval', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/approval");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://api.saferize.com/approval", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /approval`

*Initiate an Approval*

A new approval object is created in order to get parent consent to add a new app user (a child).

Your app will be able to initiate approvals once it is pu lished. To learn more about setting up your app, please read our [Quick Start Guide](http://google.com).

> Body parameter

```json
{
  "appUser": {
    "id": 123,
    "token": "child_nickname_on_game_1",
    "app": {
      "id": 1,
      "name": "Saferize Example",
      "platforms": [
        "ANDROID",
        "IOS"
      ],
      "category": "GAME",
      "timeRestriction": "ENABLED",
      "status": "PUBLISHED",
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "shortDescription": "Lorem ipsum dolor sit amet.",
      "urlName": "string",
      "age": 5,
      "email": "developer@example.com"
    },
    "child": {
      "id": 1234567,
      "firstName": "Sofia",
      "lastName": "Smith",
      "birthDate": "2009-01-23T00:00:00.000Z",
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "gender": "FEMALE"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    }
  },
  "approvalParent": {
    "id": 123456,
    "firstName": "John",
    "lastName": "Smith",
    "mobilePhone": 41512345678,
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "email": "parent@example.com"
  },
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "statusTime": "2017-11-09T14:23:00.000Z",
  "createdTime": "2017-11-09T14:23:00.000Z",
  "status": "APPROVED",
  "parentEmail": "parent@myfamily.com",
  "parentMobilePhone": 4151234567,
  "currentState": "ACTIVE"
}
```

<h3 id="initiateApproval-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|The new Approval|
|» appUser|body|[AppUser](#schemaappuser)|true|No description|
|»» id|body|integer(int64)|true|Unique identifier for the app user returned by the system.|
|»» token|body|string|true|App user's token (username on the app). This is defined by the app and should be user-unique.|
|»» app|body|[App](#schemaapp)|true|No description|
|»»» id|body|integer(int64)|true|Unique identifier for the app returned by the system.|
|»»» name|body|string|true|Name of the app.|
|»»» platforms|body|[string]|false|Array of enums that specify what platforms are supported by this app.|
|»»» category|body|string|false|One of the predefined values indicating the category of the app.|
|»»» timeRestriction|body|string|false|On/off flag for enabling/disabling time restrictions on the app.|
|»»» status|body|string|false|Current lifecycle status of the app. Please read more on the requirements for [publishing the app](#changestatus).|
|»»» description|body|string|false|Description of the app. (max. number of characters = 255)|
|»»» shortDescription|body|string|false|Short description of the app. (max. number of characters = 100)|
|»»» urlName|body|string|false|Partial url name of this app on Saferize.|
|»»» age|body|integer(int64)|false|Minimum recommended age of app users.|
|»»» email|body|string|false|App developer's email.|
|»» child|body|[Child](#schemachild)|true|No description|
|»»» id|body|integer(int64)|true|Unique identifier for the child returned by the system.|
|»»» firstName|body|string|true|Child's first name.|
|»»» lastName|body|string|false|Child's last name.|
|»»» birthDate|body|string(date)|true|Child's date of birth.|
|»»» family|body|[Family](#schemafamily)|true|No description|
|»»»» id|body|integer(int64)|true|Unique identifier for the family returned by the system.|
|»»»» name|body|string|true|Family name.|
|»»» gender|body|string|true|Child's gender.|
|»» family|body|[Family](#schemafamily)|true|No description|
|» approvalParent|body|[Parent](#schemaparent)|false|No description|
|»» id|body|integer(int64)|true|Unique identifier for the parent returned by the system.|
|»» firstName|body|string|true|Parent's first name.|
|»» lastName|body|string|true|Parent's last name|
|»» mobilePhone|body|string(phone)|false|Parent's phone number. The format should be XXXYYYZZZZ (no dashes or parentheses).|
|»» family|body|[Family](#schemafamily)|true|No description|
|»» email|body|string(email)|true|Parent's email address.|
|» family|body|[Family](#schemafamily)|true|No description|
|» statusTime|body|string(date-time)|true|The time and date of the last status change. The date-time notation as defined by [RFC 3339](https://tools.ietf.org/html/rfc3339).|
|» createdTime|body|string(date-time)|true|The time and date when this approval was created. The date-time notation as defined by [RFC 3339](https://tools.ietf.org/html/rfc3339).|
|» status|body|string|true|The approval status|
|» parentEmail|body|string|false|The email of the parent who received this request|
|» parentMobilePhone|body|string|false|The phone number of the parent who received this request. The format should be XXXYYYZZZZ (no dashes or parentheses).|
|» currentState|body|string|false|The approval status|

#### Enumerated Values

|Parameter|Value|
|---|---|
|»»» platforms|ANDROID|
|»»» platforms|IOS|
|»»» platforms|WINDOWS|
|»»» platforms|MAC_OS|
|»»» platforms|LINUX|
|»»» platforms|APPLE_TV|
|»»» platforms|ANDROID_TV|
|»»» platforms|APPLE_WATCH|
|»»» platforms|ANDROID_WATCH|
|»»» platforms|XBOX|
|»»» platforms|NINTENDO|
|»»» platforms|PLAYSTATION|
|»»» category|GAME|
|»»» category|MEDIA|
|»»» timeRestriction|ENABLED|
|»»» timeRestriction|DISABLED|
|»»» status|DRAFT|
|»»» status|PUBLISHED|
|»»» status|DELETED|
|»»» gender|MALE|
|»»» gender|FEMALE|
|»»» gender|UNKNOWN|
|» status|PENDING|
|» status|NOTIFIED|
|» status|APPROVED|
|» status|REJECTED|
|» currentState|ACTIVE|
|» currentState|PAUSED|

> Example responses

```json
{
  "id": 12,
  "appUser": {
    "id": 123,
    "token": "child_nickname_on_game_1",
    "app": {
      "id": 1,
      "name": "Saferize Example",
      "platforms": [
        "ANDROID",
        "IOS"
      ],
      "category": "GAME",
      "timeRestriction": "ENABLED",
      "status": "PUBLISHED",
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "shortDescription": "Lorem ipsum dolor sit amet.",
      "urlName": "string",
      "age": 5,
      "email": "developer@example.com"
    },
    "child": {
      "id": 1234567,
      "firstName": "Sofia",
      "lastName": "Smith",
      "birthDate": "2009-01-23T00:00:00.000Z",
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "gender": "FEMALE"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    }
  },
  "approvalParent": {
    "id": 123456,
    "firstName": "John",
    "lastName": "Smith",
    "mobilePhone": 41512345678,
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "email": "parent@example.com"
  },
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "statusTime": "2017-11-09T14:23:00.000Z",
  "createdTime": "2017-11-09T14:23:00.000Z",
  "status": "APPROVED",
  "parentEmail": "parent@myfamily.com",
  "parentMobilePhone": 4151234567,
  "currentState": "ACTIVE"
}
```

<h3 id="initiateApproval-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Approval Created|[Approval](#schemaapproval)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|409|[Conflict](https://tools.ietf.org/html/rfc7231#section-6.5.8)|The request conflicts with another request|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getApprovals

<a id="opIdgetApprovals"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/approval \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/approval HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/approval',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/approval',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/approval',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/approval', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/approval");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/approval", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /approval`

*List App approvals*

Retrieves all the approvals associated with the app.

> Example responses

```json
[
  {
    "id": 12,
    "appUser": {
      "id": 123,
      "token": "child_nickname_on_game_1",
      "app": {
        "id": 1,
        "name": "Saferize Example",
        "platforms": [
          "ANDROID",
          "IOS"
        ],
        "category": "GAME",
        "timeRestriction": "ENABLED",
        "status": "PUBLISHED",
        "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "shortDescription": "Lorem ipsum dolor sit amet.",
        "urlName": "string",
        "age": 5,
        "email": "developer@example.com"
      },
      "child": {
        "id": 1234567,
        "firstName": "Sofia",
        "lastName": "Smith",
        "birthDate": "2009-01-23T00:00:00.000Z",
        "family": {
          "id": 12345,
          "name": "Smith"
        },
        "gender": "FEMALE"
      },
      "family": {
        "id": 12345,
        "name": "Smith"
      }
    },
    "approvalParent": {
      "id": 123456,
      "firstName": "John",
      "lastName": "Smith",
      "mobilePhone": 41512345678,
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "email": "parent@example.com"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "statusTime": "2017-11-09T14:23:00.000Z",
    "createdTime": "2017-11-09T14:23:00.000Z",
    "status": "APPROVED",
    "parentEmail": "parent@myfamily.com",
    "parentMobilePhone": 4151234567,
    "currentState": "ACTIVE"
  }
]
```

<h3 id="getApprovals-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of approvals associated with the app.|[[Approval]](#schemaapproval)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getApprovalById

<a id="opIdgetApprovalById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/approval/{id} \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/approval/{id} HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/approval/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/approval/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/approval/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/approval/{id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/approval/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/approval/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /approval/{id}`

*Retrieve an Approval via identifier*

<h3 id="getApprovalById-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the approval.|

> Example responses

```json
{
  "id": 12,
  "appUser": {
    "id": 123,
    "token": "child_nickname_on_game_1",
    "app": {
      "id": 1,
      "name": "Saferize Example",
      "platforms": [
        "ANDROID",
        "IOS"
      ],
      "category": "GAME",
      "timeRestriction": "ENABLED",
      "status": "PUBLISHED",
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "shortDescription": "Lorem ipsum dolor sit amet.",
      "urlName": "string",
      "age": 5,
      "email": "developer@example.com"
    },
    "child": {
      "id": 1234567,
      "firstName": "Sofia",
      "lastName": "Smith",
      "birthDate": "2009-01-23T00:00:00.000Z",
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "gender": "FEMALE"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    }
  },
  "approvalParent": {
    "id": 123456,
    "firstName": "John",
    "lastName": "Smith",
    "mobilePhone": 41512345678,
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "email": "parent@example.com"
  },
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "statusTime": "2017-11-09T14:23:00.000Z",
  "createdTime": "2017-11-09T14:23:00.000Z",
  "status": "APPROVED",
  "parentEmail": "parent@myfamily.com",
  "parentMobilePhone": 4151234567,
  "currentState": "ACTIVE"
}
```

<h3 id="getApprovalById-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the approval object associated with the id.|[Approval](#schemaapproval)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## getApprovalByToken

<a id="opIdgetApprovalByToken"></a>

> Code samples

```shell
# You can also use wget
curl -X GET http://api.saferize.com/approval/token/{token} \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
GET http://api.saferize.com/approval/token/{token} HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/approval/token/{token}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/approval/token/{token}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.get 'http://api.saferize.com/approval/token/{token}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.get('http://api.saferize.com/approval/token/{token}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/approval/token/{token}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "http://api.saferize.com/approval/token/{token}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /approval/token/{token}`

*Retrieve an Approval via token*

<h3 id="getApprovalByToken-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|token|path|integer(int64)|true|The unique token assigned by the app to the user.|

> Example responses

```json
{
  "id": 12,
  "appUser": {
    "id": 123,
    "token": "child_nickname_on_game_1",
    "app": {
      "id": 1,
      "name": "Saferize Example",
      "platforms": [
        "ANDROID",
        "IOS"
      ],
      "category": "GAME",
      "timeRestriction": "ENABLED",
      "status": "PUBLISHED",
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "shortDescription": "Lorem ipsum dolor sit amet.",
      "urlName": "string",
      "age": 5,
      "email": "developer@example.com"
    },
    "child": {
      "id": 1234567,
      "firstName": "Sofia",
      "lastName": "Smith",
      "birthDate": "2009-01-23T00:00:00.000Z",
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "gender": "FEMALE"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    }
  },
  "approvalParent": {
    "id": 123456,
    "firstName": "John",
    "lastName": "Smith",
    "mobilePhone": 41512345678,
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "email": "parent@example.com"
  },
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "statusTime": "2017-11-09T14:23:00.000Z",
  "createdTime": "2017-11-09T14:23:00.000Z",
  "status": "APPROVED",
  "parentEmail": "parent@myfamily.com",
  "parentMobilePhone": 4151234567,
  "currentState": "ACTIVE"
}
```

<h3 id="getApprovalByToken-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the approval object associated with the token.|[Approval](#schemaapproval)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

<h1 id="Saferize-API-Session">Session</h1>

A session is established at the point of the authentication, and will last for an hour. To perform majority of the operations on our platform, whether it be reading or writing, you must be authenticated.

Each subsuquent call will extend the session by an extra hour. If the communication is idle for an hour, the session will expire, and will need to be established again.

## createSession

<a id="opIdcreateSession"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://api.saferize.com/session \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
POST http://api.saferize.com/session HTTP/1.1
Host: api.saferize.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/session',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "accessKey": "jane.developer@saferize.com",
  "secretKey": "SuperHardPassword!1"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/session',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.post 'http://api.saferize.com/session',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.post('http://api.saferize.com/session', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/session");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Content-Type": []string{"application/json"},
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://api.saferize.com/session", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /session`

*Create a developer session*

> Body parameter

```json
{
  "accessKey": "jane.developer@saferize.com",
  "secretKey": "SuperHardPassword!1"
}
```

<h3 id="createSession-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|object|true|Credentials of the subject that is attempting to create the session.|
|» accessKey|body|string|true|Access key of the developer that is attempting to create the session.|
|» secretKey|body|string|true|Secret key of the developer that is attempting to create the session.|

> Example responses

```json
{
  "duration": 3600,
  "subject": {
    "id": 1234,
    "firstName": "Jane",
    "lastName": "Doe",
    "email": "jane.doe@example.com",
    "mobilePhone": "415-123-4567",
    "company": "Saferize",
    "country": "CA"
  },
  "origin": "127.0.0.1",
  "signatureCode": "8479dd81-4a33-4806-902f-52cbbe93c240",
  "startedAt": "2017-07-21T17:32:28Z",
  "state": "ACTIVE",
  "uuid": "ce11cccc-1bdb-430f-8b9f-ee02079e4fe5",
  "token": "VjF8MTA5ODh8Y29tLnNhZmVyaXplLmNvcmUuZW50aXRpZXMucGFyZW50LlBhcmVudHwxNTI1MjkyNjU2MTA4fGNlMTFjY2NjLTFiZGItNDMwZi04YjlmLWVlMDIwNzllNGZlNQ=="
}
```

<h3 id="createSession-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Returns the session object if the creation succeeded.|[Session](#schemasession)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>

## createAppUserSession

<a id="opIdcreateAppUserSession"></a>

> Code samples

```shell
# You can also use wget
curl -X POST http://api.saferize.com/session/app/{token} \
  -H 'Accept: application/json' \
  -H 'Authorization: bearer {access-token}'

```

```http
POST http://api.saferize.com/session/app/{token} HTTP/1.1
Host: api.saferize.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

$.ajax({
  url: 'http://api.saferize.com/session/app/{token}',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json',
  'Authorization':'bearer {access-token}'

};

fetch('http://api.saferize.com/session/app/{token}',
{
  method: 'POST',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});

```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json',
  'Authorization' => 'bearer {access-token}'
}

result = RestClient.post 'http://api.saferize.com/session/app/{token}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json',
  'Authorization': 'bearer {access-token}'
}

r = requests.post('http://api.saferize.com/session/app/{token}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("http://api.saferize.com/session/app/{token}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());

```

```go
package main

import (
       "bytes"
       "net/http"
)

func main() {

    headers := map[string][]string{
        "Accept": []string{"application/json"},
        "Authorization": []string{"bearer {access-token}"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "http://api.saferize.com/session/app/{token}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /session/app/{token}`

*Create an app user session*

<h3 id="createAppUserSession-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|token|path|string|true|Unique username (alias) for the app user on the app.|

> Example responses

```json
{
  "id": 12345678,
  "approval": {
    "id": 12,
    "appUser": {
      "id": 123,
      "token": "child_nickname_on_game_1",
      "app": {
        "id": 1,
        "name": "Saferize Example",
        "platforms": [
          "ANDROID",
          "IOS"
        ],
        "category": "GAME",
        "timeRestriction": "ENABLED",
        "status": "PUBLISHED",
        "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "shortDescription": "Lorem ipsum dolor sit amet.",
        "urlName": "string",
        "age": 5,
        "email": "developer@example.com"
      },
      "child": {
        "id": 1234567,
        "firstName": "Sofia",
        "lastName": "Smith",
        "birthDate": "2009-01-23T00:00:00.000Z",
        "family": {
          "id": 12345,
          "name": "Smith"
        },
        "gender": "FEMALE"
      },
      "family": {
        "id": 12345,
        "name": "Smith"
      }
    },
    "approvalParent": {
      "id": 123456,
      "firstName": "John",
      "lastName": "Smith",
      "mobilePhone": 41512345678,
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "email": "parent@example.com"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "statusTime": "2017-11-09T14:23:00.000Z",
    "createdTime": "2017-11-09T14:23:00.000Z",
    "status": "APPROVED",
    "parentEmail": "parent@myfamily.com",
    "parentMobilePhone": 4151234567,
    "currentState": "ACTIVE"
  },
  "hostname": "183.241.21.10"
}
```

<h3 id="createAppUserSession-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the app usage session object if the creation succeeded.|[AppUsageSession](#schemaappusagesession)|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
BearerAuth
</aside>


<h1 id="Saferize-API-Events">Events</h1>

Events are our way of letting you know when something interesting has happened in relation to your app.

Events occur when the state of another API resource changes. The state of that resource at the time of the change is embedded in the event's data fields.

We will deliver these events to you through HTTP Post request to the **webhookURL** that you specified when [setting app configuration](#opIdupdateAppConfig).

## Types of event

This is a list of all the types of events we currently send. We may add more at any time, so in developing and maintaing your code, you should not assume that only these types exist.

<a id="eventTypes"></a>

|Event|Notes|
|---|---|
|ApprovalCreatedEvent|Gets fired when the child signs up for the game. Subsequently, and approval object is created.|
|ApprovalStatusChangedEvent|Whenever a managing parent changes the status of the Approval, your app will be notified.|
|UsageTimerCreatedEvent|Whenever a managing parent sets new time restrictions for their child (assuming you enabled [time restrictions](#opIdchangeTimeRestriction)), your app will be notified|
|ApprovalStateChangedEvent|Whenever the managing parent decides to temporarily pause the game their child is playing, your app will be notified.|



# Schemas

<h2 id="tocSapp">App</h2>

<a id="schemaapp"></a>

```json
{
  "id": 1,
  "name": "Saferize Example",
  "platforms": [
    "ANDROID",
    "IOS"
  ],
  "category": "GAME",
  "timeRestriction": "ENABLED",
  "status": "PUBLISHED",
  "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
  "shortDescription": "Lorem ipsum dolor sit amet.",
  "urlName": "string",
  "age": 5,
  "email": "developer@example.com"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|Unique identifier for the app returned by the system.|
|name|string|true|Name of the app.|
|platforms|[string]|false|Array of enums that specify what platforms are supported by this app.|
|category|string|false|One of the predefined values indicating the category of the app.|
|timeRestriction|string|false|On/off flag for enabling/disabling time restrictions on the app.|
|status|string|false|Current lifecycle status of the app. Please read more on the requirements for [publishing the app](#changestatus).|
|description|string|false|Description of the app. (max. number of characters = 255)|
|shortDescription|string|false|Short description of the app. (max. number of characters = 100)|
|urlName|string|false|Partial url name of this app on Saferize.|
|age|integer(int64)|false|Minimum recommended age of app users.|
|email|string|false|App developer's email.|

#### Enumerated Values

|Property|Value|
|---|---|
|platforms|ANDROID|
|platforms|IOS|
|platforms|WINDOWS|
|platforms|MAC_OS|
|platforms|LINUX|
|platforms|APPLE_TV|
|platforms|ANDROID_TV|
|platforms|APPLE_WATCH|
|platforms|ANDROID_WATCH|
|platforms|XBOX|
|platforms|NINTENDO|
|platforms|PLAYSTATION|

|Property|Value|
|---|---|
|category|GAME|
|category|MEDIA|

|Property|Value|
|---|---|
|timeRestriction|ENABLED|
|timeRestriction|DISABLED|

|Property|Value|
|---|---|
|status|DRAFT|
|status|PUBLISHED|
|status|DELETED|

<h2 id="tocSfamily">Family</h2>

<a id="schemafamily"></a>

```json
{
  "id": 12345,
  "name": "Smith"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|Unique identifier for the family returned by the system.|
|name|string|true|Family name.|

<h2 id="tocSparent">Parent</h2>

<a id="schemaparent"></a>

```json
{
  "id": 123456,
  "firstName": "John",
  "lastName": "Smith",
  "mobilePhone": 41512345678,
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "email": "parent@example.com"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|Unique identifier for the parent returned by the system.|
|firstName|string|true|Parent's first name.|
|lastName|string|true|Parent's last name|
|mobilePhone|string(phone)|false|Parent's phone number. The format should be XXXYYYZZZZ (no dashes or parentheses).|
|family|[Family](#schemafamily)|true|Parent's family.|
|email|string(email)|true|Parent's email address.|

<h2 id="tocSchild">Child</h2>

<a id="schemachild"></a>

```json
{
  "id": 1234567,
  "firstName": "Sofia",
  "lastName": "Smith",
  "birthDate": "2009-01-23T00:00:00.000Z",
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "gender": "FEMALE"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|Unique identifier for the child returned by the system.|
|firstName|string|true|Child's first name.|
|lastName|string|false|Child's last name.|
|birthDate|string(date)|true|Child's date of birth.|
|family|[Family](#schemafamily)|true|Child's family.|
|gender|string|true|Child's gender.|

#### Enumerated Values

|Property|Value|
|---|---|
|gender|MALE|
|gender|FEMALE|
|gender|UNKNOWN|

<h2 id="tocSdeveloper">Developer</h2>

<a id="schemadeveloper"></a>

```json
{
  "id": 1234,
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|Unique identifier for the developer returned by the system.|
|firstName|string|true|Developer's first name.|
|lastName|string|true|Developer's last name.|
|email|string|true|Developer's primary email address.|
|mobilePhone|string|true|Developer's primary mobile phone number. The format should be XXXYYYZZZZ (no dashes or parentheses).|
|company|string|false|Developer's company name.|
|country|string|false|The country in which the developer resides, or in which the company is legally established. This should be an ISO 3166-1 alpha-2 country code. For example, if you are in the United States and the business for which you're creating an account is legally represented in Canada, you would use `CA` as the country for the account being created.|

<h2 id="tocSappuser">AppUser</h2>

<a id="schemaappuser"></a>

```json
{
  "id": 123,
  "token": "child_nickname_on_game_1",
  "app": {
    "id": 1,
    "name": "Saferize Example",
    "platforms": [
      "ANDROID",
      "IOS"
    ],
    "category": "GAME",
    "timeRestriction": "ENABLED",
    "status": "PUBLISHED",
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
    "shortDescription": "Lorem ipsum dolor sit amet.",
    "urlName": "string",
    "age": 5,
    "email": "developer@example.com"
  },
  "child": {
    "id": 1234567,
    "firstName": "Sofia",
    "lastName": "Smith",
    "birthDate": "2009-01-23T00:00:00.000Z",
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "gender": "FEMALE"
  },
  "family": {
    "id": 12345,
    "name": "Smith"
  }
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|Unique identifier for the app user returned by the system.|
|token|string|true|App user's token (username on the app). This is defined by the app and should be user-unique.|
|app|[App](#schemaapp)|true|App that this app user is registered on.|
|child|[Child](#schemachild)|true|Child that represent this app user.|
|family|[Family](#schemafamily)|true|The family of the child on this app user.|

<h2 id="tocSapproval">Approval</h2>

<a id="schemaapproval"></a>

```json
{
  "id": 12,
  "appUser": {
    "id": 123,
    "token": "child_nickname_on_game_1",
    "app": {
      "id": 1,
      "name": "Saferize Example",
      "platforms": [
        "ANDROID",
        "IOS"
      ],
      "category": "GAME",
      "timeRestriction": "ENABLED",
      "status": "PUBLISHED",
      "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
      "shortDescription": "Lorem ipsum dolor sit amet.",
      "urlName": "string",
      "age": 5,
      "email": "developer@example.com"
    },
    "child": {
      "id": 1234567,
      "firstName": "Sofia",
      "lastName": "Smith",
      "birthDate": "2009-01-23T00:00:00.000Z",
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "gender": "FEMALE"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    }
  },
  "approvalParent": {
    "id": 123456,
    "firstName": "John",
    "lastName": "Smith",
    "mobilePhone": 41512345678,
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "email": "parent@example.com"
  },
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "statusTime": "2017-11-09T14:23:00.000Z",
  "createdTime": "2017-11-09T14:23:00.000Z",
  "status": "APPROVED",
  "parentEmail": "parent@myfamily.com",
  "parentMobilePhone": 4151234567,
  "currentState": "ACTIVE"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|Unique identifier for the approval returned by the system.|
|appUser|[AppUser](#schemaappuser)|true|App user on this approval.|
|approvalParent|[Parent](#schemaparent)|false|Parent managing this approval.|
|family|[Family](#schemafamily)|true|Family with which this approval is associated with.|
|statusTime|string(date-time)|true|Time and date of the last status change. The date-time notation as defined by [RFC 3339](https://tools.ietf.org/html/rfc3339).|
|createdTime|string(date-time)|true|Time and date when this approval was created. The date-time notation as defined by [RFC 3339](https://tools.ietf.org/html/rfc3339).|
|status|string|true|The approval status.|
|parentEmail|string|false|Email of the parent who received this request.|
|parentMobilePhone|string|false|Phone number of the parent who received this request. The format should be XXXYYYZZZZ (no dashes or parentheses).|
|currentState|string|false|Current state of the approval.|

#### Enumerated Values

|Property|Value|
|---|---|
|status|PENDING|
|status|NOTIFIED|
|status|APPROVED|
|status|REJECTED|

|Property|Value|
|---|---|
|currentState|ACTIVE|
|currentState|PAUSED|

<h2 id="tocSappconfig">AppConfig</h2>

<a id="schemaappconfig"></a>

```json
{
  "webhookUrl": "https://example.saferize.com",
  "autoPauseSessionsInterval": 30,
  "autoRejectWaitTime": 259200,
  "validatorName": "Microtransaction"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|webhookUrl|string|false|Valid HTTPS endpoint for receiving webhooks.|
|autoPauseSessionsInterval|integer(int64)|false|Undefined.|
|autoRejectWaitTime|integer(int64)|false|Time in seconds after which an unattended approval will be automatically rejected.|
|validatorName|[Validator](#schemavalidator)|false|Validator defines a specific way that the developer has chosen for the app to confirm parent-child relationship.|

<h2 id="tocSsession">Session</h2>

<a id="schemasession"></a>

```json
{
  "duration": 3600,
  "subject": {
    "id": 1234,
    "firstName": "Jane",
    "lastName": "Doe",
    "email": "jane.doe@example.com",
    "mobilePhone": "415-123-4567",
    "company": "Saferize",
    "country": "CA"
  },
  "origin": "127.0.0.1",
  "signatureCode": "8479dd81-4a33-4806-902f-52cbbe93c240",
  "startedAt": "2017-07-21T17:32:28Z",
  "state": "ACTIVE",
  "uuid": "ce11cccc-1bdb-430f-8b9f-ee02079e4fe5",
  "token": "VjF8MTA5ODh8Y29tLnNhZmVyaXplLmNvcmUuZW50aXRpZXMucGFyZW50LlBhcmVudHwxNTI1MjkyNjU2MTA4fGNlMTFjY2NjLTFiZGItNDMwZi04YjlmLWVlMDIwNzllNGZlNQ=="
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|duration|integer(int64)|true|Duration of the session before it expires and is no longer valid.|
|subject|[Developer](#schemadeveloper)|true|Developer on whom the session is created on.|
|origin|string|false|Origin of the requester that created the session.|
|signatureCode|string|true|Unique session signature.|
|startedAt|string(date-time)|true|Timestamp when the session was started. The date-time notation as defined by [RFC 3339](https://tools.ietf.org/html/rfc3339)|
|state|string|true|The current state of the approval.|
|uuid|string|true|Unique [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) of the session.|
|token|string|true|Unique token of the session.|

#### Enumerated Values

|Property|Value|
|---|---|
|state|ACTIVE,|
|state|PAUSED|

<h2 id="tocSappusagesession">AppUsageSession</h2>

<a id="schemaappusagesession"></a>

```json
{
  "id": 12345678,
  "approval": {
    "id": 12,
    "appUser": {
      "id": 123,
      "token": "child_nickname_on_game_1",
      "app": {
        "id": 1,
        "name": "Saferize Example",
        "platforms": [
          "ANDROID",
          "IOS"
        ],
        "category": "GAME",
        "timeRestriction": "ENABLED",
        "status": "PUBLISHED",
        "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.",
        "shortDescription": "Lorem ipsum dolor sit amet.",
        "urlName": "string",
        "age": 5,
        "email": "developer@example.com"
      },
      "child": {
        "id": 1234567,
        "firstName": "Sofia",
        "lastName": "Smith",
        "birthDate": "2009-01-23T00:00:00.000Z",
        "family": {
          "id": 12345,
          "name": "Smith"
        },
        "gender": "FEMALE"
      },
      "family": {
        "id": 12345,
        "name": "Smith"
      }
    },
    "approvalParent": {
      "id": 123456,
      "firstName": "John",
      "lastName": "Smith",
      "mobilePhone": 41512345678,
      "family": {
        "id": 12345,
        "name": "Smith"
      },
      "email": "parent@example.com"
    },
    "family": {
      "id": 12345,
      "name": "Smith"
    },
    "statusTime": "2017-11-09T14:23:00.000Z",
    "createdTime": "2017-11-09T14:23:00.000Z",
    "status": "APPROVED",
    "parentEmail": "parent@myfamily.com",
    "parentMobilePhone": 4151234567,
    "currentState": "ACTIVE"
  },
  "hostname": "183.241.21.10"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|false|Unique identifier for the app usage session returned by the system.|
|approval|[Approval](#schemaapproval)|false|Approval associated with this app usage session.|
|hostname|string|false|IP address where the request to create an app usage session originated from.|

<h2 id="tocSappfeature">AppFeature</h2>

<a id="schemaappfeature"></a>

```json
{
  "id": 12345678,
  "appId": 12,
  "name": "DATA_COLLECTION",
  "implemented": true,
  "parentPrivilege": true
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|false|Unique identifier for the app feature returned by the system.|
|appId|integer(int64)|false|Unique identifier for the app that this app feature is associated with.|
|name|[AppFeatureName](#schemaappfeaturename)|false|Name of the app feature.|
|implemented|boolean|false|Boolean flag indicating whether the feature is implemented.|
|parentPrivilege|boolean|false|Boolean flag indicating whether the parents are allowed to turn on/off the feature.|

<h2 id="tocSsubscriptionplan">SubscriptionPlan</h2>

<a id="schemasubscriptionplan"></a>

```json
{
  "id": 123456,
  "name": "Platinum starter",
  "billingCycle": "YEARLY",
  "active": true,
  "price": 2.99
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|false|Unique identifier for the subscription plan returned by the system.|
|name|string|false|The plans name, displayable to the customer.|
|billingCycle|string|false|Specifies billing frequency.|
|active|boolean|false|Boolean flag representing whether the plan is active.|
|price|number(float)|false|The cost of the item as a positive float.|

#### Enumerated Values

|Property|Value|
|---|---|
|billingCycle|WEEKLY|
|billingCycle|MONTHLY|
|billingCycle|YEARLY|

<h2 id="tocSimageupload">ImageUpload</h2>

<a id="schemaimageupload"></a>

```json
{
  "id": 123456789,
  "url": "https://s3.us-west-1.amazonaws.com/path/to/a/file.jpg\"",
  "createdTime": 1522346229038,
  "width": 200,
  "height": 200
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|false|Unique identifier for the image returned by the system.|
|url|string|false|A read-only URL where the uploaded file can be accessed.|
|createdTime|string|false|Time at which the object was created. Measured in seconds since the Unix epoch.|
|width|integer(int64)|false|The width in pixels of the image object.|
|height|integer(int64)|false|The height in pixels of the image object.|

<h2 id="tocSvalidator">Validator</h2>

<a id="schemavalidator"></a>

```json
"Microtransaction"
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|name|string|false|Validator defines a specific way that the developer has chosen for the app to confirm parent-child relationship.|

#### Enumerated Values

|Property|Value|
|---|---|
|name|Microtransaction|
|name|SMS|

<h2 id="tocSappfeaturename">AppFeatureName</h2>

<a id="schemaappfeaturename"></a>

```json
"DATA_COLLECTION"
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|name|string|false|App feature name.|

#### Enumerated Values

|Property|Value|
|---|---|
|name|ADVERTISING|
|name|CHAT|
|name|COMMENTS|
|name|DATA_COLLECTION|
|name|IN_APP_PURCHASES|
|name|LOCATION_SHARING|
|name|PAID_APP|
|name|PUSH_NOTIFICATIONS|
|name|SOCIAL_INTERACTION|
|name|SUBSCRIPTION|

<h2 id="tocSjsonpatch">JsonPatch</h2>

<a id="schemajsonpatch"></a>

```json
{
  "op": "replace",
  "path": "/status",
  "value": "PUBLISHED"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|op|string|false|Predifined JsonPatch operation.|
|path|string|false|The path to be updated using JsonPatch syntax.|
|value|string|false|New resource value.|

#### Enumerated Values

|Property|Value|
|---|---|
|op|add|
|op|replace|
|op|remove|

<h2 id="tocSerror">Error</h2>

<a id="schemaerror"></a>

```json
{
  "message": "There is already an app with those attributes.",
  "type": "DuplicateEntityException"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|message|string|false|A human-readable message providing more details about the error.|
|type|string|true|Error type.|

