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

To make the API as explorable as possible, accounts have test mode and live mode API keys. There is No "switch" for changing between modes, just use the appropriate key to perform a live or test transaction.

Be sure to subscribe to Saferize's API announce mailing list to receive information on new additions and changes to Saferize's API.

The requests in the right sidebar are designed to work as is.

Base URLs:

<a href="https://saferize.com/terms-of-service/">Terms of service</a>
Email: <a href="mailto:dev@saferize.com">Support</a> 

# Authentication

- HTTP Authentication, scheme: bearer 

<h1 id="Saferize-API-Developer">Developer</h1>

The `Developer` object represents the publisher. You can create, retrieve and update a developer. You may also view all the apps associated with the developer.

## createDeveloper

<a id="opIdcreateDeveloper"></a>

> Code samples

```shell
# You can also use wget
curl -X POST ///developer \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST ///developer HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///developer',
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
  "id": 1234,
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///developer',
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
  'Accept' => 'application/json'
}

result = RestClient.post '///developer',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('///developer', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///developer");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///developer", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /developer`

*Create a developer*

The developer object is created when a new developer registers.

> Body parameter

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

<h3 id="createDeveloper-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Developer](#schemadeveloper)|true|The new developer to be created|

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
None, None ( Scopes: read write )
</aside>

## getDeveloper

<a id="opIdgetDeveloper"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///developer/me \
  -H 'Accept: */*'

```

```http
GET ///developer/me HTTP/1.1
Host: null

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*'

};

$.ajax({
  url: '///developer/me',
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
  'Accept':'*/*'

};

fetch('///developer/me',
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
  'Accept' => '*/*'
}

result = RestClient.get '///developer/me',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('///developer/me', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///developer/me");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///developer/me", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /developer/me`

*Retreieve the developer*

Retrieves the developer object associated with the current session.

> Example responses

<h3 id="getDeveloper-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The developer object|[Developer](#schemadeveloper)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## updateDeveloper

<a id="opIdupdateDeveloper"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///developer/me \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT ///developer/me HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///developer/me',
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
  "id": 1234,
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///developer/me',
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
  'Accept' => 'application/json'
}

result = RestClient.put '///developer/me',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('///developer/me', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///developer/me");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///developer/me", data)
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
  "id": 1234,
  "firstName": "Jane",
  "lastName": "Doe",
  "email": "jane.doe@example.com",
  "mobilePhone": "415-123-4567",
  "company": "Saferize",
  "country": "CA"
}
```

<h3 id="updateDeveloper-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Developer](#schemadeveloper)|true|The developer to be updated to.|

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
None, None ( Scopes: read write )
</aside>

## getApps

<a id="opIdgetApps"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///developer/me/apps \
  -H 'Accept: */*'

```

```http
GET ///developer/me/apps HTTP/1.1
Host: null

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*'

};

$.ajax({
  url: '///developer/me/apps',
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
  'Accept':'*/*'

};

fetch('///developer/me/apps',
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
  'Accept' => '*/*'
}

result = RestClient.get '///developer/me/apps',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('///developer/me/apps', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///developer/me/apps");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///developer/me/apps", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /developer/me/apps`

*Retreieve developer's apps*

Retrieves the apps associated with the developer.

> Example responses

<h3 id="getApps-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|An array of apps|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|

<h3 id="getApps-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[App](#schemaapp)]|false|No description|
|» id|integer(int64)|true|Unique identifier for the app returned by the system.|
|» name|string|true|The name of the app.|
|» platforms|[string]|false|An array of enums that specify what platforms are supported by this app.|
|» category|string|false|One of the predifned values indicating the category of the app.|
|» timeRestriction|string|false|On/Off flag for enabling/disabling time restrictions on the app.|
|» status|string|false|Current lifecycle status of the app. Please read more on the requirements for publishing the app.|
|» description|string|false|A description of the app.|
|» urlName|string|false|The partial url name of this app on Saferize.|
|» details|[string]|false|Features implemented on the app.|
|» email|string|false|The app developer's email.|

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
|category|GAME|
|category|MEDIA|
|timeRestriction|ENABLED|
|timeRestriction|DISABLED|
|status|DRAFT|
|status|PUBLISHED|
|status|DELETED|
|details|SOCIAL_INTERACTION|
|details|IN_APP_PURCHASES|
|details|ADVERTISING|
|details|PAID_APP|
|details|SUBSCRIPTION|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

<h1 id="Saferize-API-App">App</h1>

This is an object representing an App that implements Saferize. You can retreive it to see it's many properties state, configuration, platforms etc.

## createApp

<a id="opIdcreateApp"></a>

> Code samples

```shell
# You can also use wget
curl -X POST ///app \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST ///app HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app',
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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
  "email": "developer@example.com"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///app',
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
  'Accept' => 'application/json'
}

result = RestClient.post '///app',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('///app', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///app", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /app`

*Create an app*

> Body parameter

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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
  "email": "developer@example.com"
}
```

<h3 id="createApp-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[App](#schemaapp)|true|The new app to be created.|

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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
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
None, None ( Scopes: read write )
</aside>

## changeAppAttributes

<a id="opIdchangeAppAttributes"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///app \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT ///app HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app',
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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
  "email": "developer@example.com"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///app',
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
  'Accept' => 'application/json'
}

result = RestClient.put '///app',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('///app', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///app", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app`

*Changes some of the descriptive attributes of the app. Bear in mind that this endpoint does not alter the core configuration of the app.*

> Body parameter

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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
  "email": "developer@example.com"
}
```

<h3 id="changeAppAttributes-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[App](#schemaapp)|true|App fields to be updated.|

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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
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
None, None ( Scopes: read write )
</aside>

## createKey

<a id="opIdcreateKey"></a>

> Code samples

```shell
# You can also use wget
curl -X POST ///app/{id}/key \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST ///app/{id}/key HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/key',
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
  'Accept':'application/json'

};

fetch('///app/{id}/key',
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
  'Accept' => 'application/json'
}

result = RestClient.post '///app/{id}/key',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('///app/{id}/key', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/key");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///app/{id}/key", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /app/{id}/key`

*Authenticate an app*

Authenticate your app by using a public-key authentication. Your apps' keys carry many privileges, so be sure to keep your private key secret! Do not share your private keys in publicly accessible areas such GitHub, client-side code, and so forth.

> Body parameter

```json
"-----BEGIN PUBLIC KEY----- MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEApofmdG+zACt1kHNlQciwyg3DuRW5za33FuBH+Zb8JoixthvtZNgee6+TkbCEWGmC9+cIJLTnialKdDUxlr5JpCtJnIpaiD++Ic5AINpE0zqhD4obR8eN7m5lcKGuNwShFxB/lc+IFHeEf5MkPcU+nSkJIV74F0XJIqNeewGxNayJ/bbIuOS4gMI0/lU18ua3OsLvVmJZyXObiYq3nMfSwWKuhfLqRMSSfICEDjnVAq3+F8/lxoqAxbC0gFZC3CdOjINgMJYr3XY6fo9oAkrt4yjSO9kAqQxaHiLqJ87gjjQEKaBzlejTM3/iJBamQUCF3VPZ3y7AoSCEWBEA5xhvXQIDAQAB -----END PUBLIC KEY-----"
```

<h3 id="createKey-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[createKeyPublicKey](#schemacreatekeypublickey)|true|RSA public key.|

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
None, None ( Scopes: read write )
</aside>

## rollKey

<a id="opIdrollKey"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///app/{id}/key \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT ///app/{id}/key HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/key',
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
  'Accept':'application/json'

};

fetch('///app/{id}/key',
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
  'Accept' => 'application/json'
}

result = RestClient.put '///app/{id}/key',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('///app/{id}/key', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/key");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///app/{id}/key", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}/key`

*Roll app authentication*

If you believe your key is compromised, roll the key with a newly generated public key.

> Body parameter

```json
"-----BEGIN PUBLIC KEY----- MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEApofmdG+zACt1kHNlQciwyg3DuRW5za33FuBH+Zb8JoixthvtZNgee6+TkbCEWGmC9+cIJLTnialKdDUxlr5JpCtJnIpaiD++Ic5AINpE0zqhD4obR8eN7m5lcKGuNwShFxB/lc+IFHeEf5MkPcU+nSkJIV74F0XJIqNeewGxNayJ/bbIuOS4gMI0/lU18ua3OsLvVmJZyXObiYq3nMfSwWKuhfLqRMSSfICEDjnVAq3+F8/lxoqAxbC0gFZC3CdOjINgMJYr3XY6fo9oAkrt4yjSO9kAqQxaHiLqJ87gjjQEKaBzlejTM3/iJBamQUCF3VPZ3y7AoSCEWBEA5xhvXQIDAQAB -----END PUBLIC KEY-----"
```

<h3 id="rollKey-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[createKeyPublicKey](#schemacreatekeypublickey)|true|RSA public key.|

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
None, None ( Scopes: read write )
</aside>

## getAppBy

<a id="opIdgetAppBy"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///app/{id} \
  -H 'Accept: application/json'

```

```http
GET ///app/{id} HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}',
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
  'Accept':'application/json'

};

fetch('///app/{id}',
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
  'Accept' => 'application/json'
}

result = RestClient.get '///app/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('///app/{id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///app/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}`

*Retrieve an app*

<h3 id="getAppBy-parameters">Parameters</h3>

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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
  "email": "developer@example.com"
}
```

<h3 id="getAppBy-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the app object.|[App](#schemaapp)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## changeTimeRestriction

<a id="opIdchangeTimeRestriction"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH ///app/{id}[timeRestriction]* \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH ///app/{id}[timeRestriction]* HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}[timeRestriction]*',
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
  "value": {}
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///app/{id}[timeRestriction]*',
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
  'Accept' => 'application/json'
}

result = RestClient.patch '///app/{id}[timeRestriction]*',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('///app/{id}[timeRestriction]*', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}[timeRestriction]*");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "///app/{id}[timeRestriction]*", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /app/{id}[timeRestriction]*`

*Update app time restrictions*

Time restrictions is a Saferize internal feature. If you would like parents to manage sessions, set time limits, and arbitrary pause/resume the app, you can set the time restrictions flag value to `ENABLED`. This is also the default value set upon [app creation](/#operation--app-post).

Otherwise, you may disable this feature by setting the time restrictions flag value to `DISABLED`.
* The path in brackets not included in the actual path, but in the JsonPatch operation

> Body parameter

```json
{
  "op": "replace",
  "path": "/status",
  "value": {}
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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
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
None, None ( Scopes: read write )
</aside>

## changeStatus

<a id="opIdchangeStatus"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH ///app/{id}[status]* \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH ///app/{id}[status]* HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}[status]*',
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
  "value": {}
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///app/{id}[status]*',
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
  'Accept' => 'application/json'
}

result = RestClient.patch '///app/{id}[status]*',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('///app/{id}[status]*', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}[status]*");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "///app/{id}[status]*", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /app/{id}[status]*`

*Update app status*

* The path in square brackets not included in the actual path, but in the JsonPatch operation.

When the app is created, the initial status is `DRAFT`. Once the app is configured, you may change the status to ```PUBLISHED``` via this endpoint. This will initialize the process of publishing the app, and the status will be `IN_REVIEW` until Saferize Customer Support approves it.

Firstly, you must [Authenticate the app](). In order to publish the app, all [App](/#/definitions/App) fields must be populated. In addition to this, the app must have have at least one [Screenshot](/#uploadscreenshot) and one [Logo](/#uploadlogo) uploaded. 

To delete the app, set the status to `DELETED`.

If you need any help throughout this process, please contact the Saferize Customer Support.

> Body parameter

```json
{
  "op": "replace",
  "path": "/status",
  "value": {}
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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
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
None, None ( Scopes: read write )
</aside>

## updateAppConfig

<a id="opIdupdateAppConfig"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///app/{id}/config \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT ///app/{id}/config HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/config',
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
  'Accept':'application/json'

};

fetch('///app/{id}/config',
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
  'Accept' => 'application/json'
}

result = RestClient.put '///app/{id}/config',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('///app/{id}/config', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/config");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///app/{id}/config", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}/config`

*Update app configuration*

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
None, None ( Scopes: read write )
</aside>

## getAppConfig

<a id="opIdgetAppConfig"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///app/{id}/config \
  -H 'Accept: application/json'

```

```http
GET ///app/{id}/config HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/config',
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
  'Accept':'application/json'

};

fetch('///app/{id}/config',
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
  'Accept' => 'application/json'
}

result = RestClient.get '///app/{id}/config',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('///app/{id}/config', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/config");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///app/{id}/config", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/config`

*Retrieve app configuration*

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
None, None ( Scopes: read write )
</aside>

## uploadLogo

<a id="opIduploadLogo"></a>

> Code samples

```shell
# You can also use wget
curl -X POST ///app/{id}/logo \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST ///app/{id}/logo HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/logo',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///app/{id}/logo',
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
  'Accept' => 'application/json'
}

result = RestClient.post '///app/{id}/logo',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('///app/{id}/logo', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/logo");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///app/{id}/logo", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /app/{id}/logo`

*Upload app logo*

> Body parameter

```json
"string"
```

<h3 id="uploadLogo-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[uploadLogoBody](#schemauploadlogobody)|true|A file to upload. The file should follow the specifications of RFC 2388 (which defines file transfers for the `multipart/form-data protocol`.|

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
None, None ( Scopes: read write )
</aside>

## getLogos

<a id="opIdgetLogos"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///app/{id}/logo \
  -H 'Accept: application/json'

```

```http
GET ///app/{id}/logo HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/logo',
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
  'Accept':'application/json'

};

fetch('///app/{id}/logo',
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
  'Accept' => 'application/json'
}

result = RestClient.get '///app/{id}/logo',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('///app/{id}/logo', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/logo");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///app/{id}/logo", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/logo`

*Retrieve app logo*

<h3 id="getLogos-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|

> Example responses

```json
[
  {
    "id": 123456789,
    "url": "https://s3.us-west-1.amazonaws.com/path/to/a/file.jpg\"",
    "createdTime": 1522346229038,
    "width": 200,
    "height": 200
  }
]
```

<h3 id="getLogos-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of image objects if they exist on the system.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="getLogos-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[ImageUpload](#schemaimageupload)]|false|No description|
|» id|integer(int64)|false|Unique identifier for the image returned by the system.|
|» url|string|false|A read-only URL where the uploaded file can be accessed.|
|» createdTime|string|false|Time at which the object was created. Measured in seconds since the Unix epoch.|
|» width|integer(int64)|false|The witdh in pixels of the image object.|
|» height|integer(int64)|false|The witdh in pixels of the image object.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## deleteLogo

<a id="opIddeleteLogo"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE ///app/{id}/logo/{logoId}

```

```http
DELETE ///app/{id}/logo/{logoId} HTTP/1.1
Host: null

```

```javascript

$.ajax({
  url: '///app/{id}/logo/{logoId}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

fetch('///app/{id}/logo/{logoId}',
{
  method: 'DELETE'

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

result = RestClient.delete '///app/{id}/logo/{logoId}',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.delete('///app/{id}/logo/{logoId}', params={

)

print r.json()

```

```java
URL obj = new URL("///app/{id}/logo/{logoId}");
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

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "///app/{id}/logo/{logoId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /app/{id}/logo/{logoId}`

*Delete app logo*

<h3 id="deleteLogo-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|logoId|path|integer(int64)|true|Unique identifier for the image file to be deleted.|

<h3 id="deleteLogo-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Returns `No Content` if the deletion was succeeded.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## uploadScreenshot

<a id="opIduploadScreenshot"></a>

> Code samples

```shell
# You can also use wget
curl -X POST ///app/{id}/screenshots \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST ///app/{id}/screenshots HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/screenshots',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = 'string';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///app/{id}/screenshots',
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
  'Accept' => 'application/json'
}

result = RestClient.post '///app/{id}/screenshots',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('///app/{id}/screenshots', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/screenshots");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///app/{id}/screenshots", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /app/{id}/screenshots`

*Upload app screenshot*

> Body parameter

```json
"string"
```

<h3 id="uploadScreenshot-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[uploadLogoBody](#schemauploadlogobody)|true|A file to upload. The file should follow the specifications of RFC 2388 (which defines file transfers for the `multipart/form-data protocol`.|

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
None, None ( Scopes: read write )
</aside>

## getScreenshots

<a id="opIdgetScreenshots"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///app/{id}/screenshots \
  -H 'Accept: application/json'

```

```http
GET ///app/{id}/screenshots HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/screenshots',
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
  'Accept':'application/json'

};

fetch('///app/{id}/screenshots',
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
  'Accept' => 'application/json'
}

result = RestClient.get '///app/{id}/screenshots',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('///app/{id}/screenshots', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/screenshots");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///app/{id}/screenshots", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/screenshots`

*Retrieve app screenshots*

<h3 id="getScreenshots-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|

> Example responses

```json
[
  {
    "id": 123456789,
    "url": "https://s3.us-west-1.amazonaws.com/path/to/a/file.jpg\"",
    "createdTime": 1522346229038,
    "width": 200,
    "height": 200
  }
]
```

<h3 id="getScreenshots-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of image objects if they exist on the system.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="getScreenshots-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[ImageUpload](#schemaimageupload)]|false|No description|
|» id|integer(int64)|false|Unique identifier for the image returned by the system.|
|» url|string|false|A read-only URL where the uploaded file can be accessed.|
|» createdTime|string|false|Time at which the object was created. Measured in seconds since the Unix epoch.|
|» width|integer(int64)|false|The witdh in pixels of the image object.|
|» height|integer(int64)|false|The witdh in pixels of the image object.|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## deleteScreenshot

<a id="opIddeleteScreenshot"></a>

> Code samples

```shell
# You can also use wget
curl -X DELETE ///app/{id}/screenshots/{screenshotId}

```

```http
DELETE ///app/{id}/screenshots/{screenshotId} HTTP/1.1
Host: null

```

```javascript

$.ajax({
  url: '///app/{id}/screenshots/{screenshotId}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})

```

```javascript--nodejs
const request = require('node-fetch');

fetch('///app/{id}/screenshots/{screenshotId}',
{
  method: 'DELETE'

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

result = RestClient.delete '///app/{id}/screenshots/{screenshotId}',
  params: {
  }

p JSON.parse(result)

```

```python
import requests

r = requests.delete('///app/{id}/screenshots/{screenshotId}', params={

)

print r.json()

```

```java
URL obj = new URL("///app/{id}/screenshots/{screenshotId}");
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

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("DELETE", "///app/{id}/screenshots/{screenshotId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`DELETE /app/{id}/screenshots/{screenshotId}`

*Delete app screenshot*

<h3 id="deleteScreenshot-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|screenshotId|path|integer(int64)|true|Unique identifier for the image file to be deleted.|

<h3 id="deleteScreenshot-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|Returns `No Content` if the deletion was succeeded.|None|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## getAppPlan

<a id="opIdgetAppPlan"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///app/{id}/plan \
  -H 'Accept: application/json'

```

```http
GET ///app/{id}/plan HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/plan',
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
  'Accept':'application/json'

};

fetch('///app/{id}/plan',
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
  'Accept' => 'application/json'
}

result = RestClient.get '///app/{id}/plan',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('///app/{id}/plan', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/plan");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///app/{id}/plan", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/plan`

*Retrieve app plan*

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
  "price": 299
}
```

<h3 id="getAppPlan-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns a subscription plan object if it exists on the system.|[SubscriptionPlan](#schemasubscriptionplan)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## getAppFeatures

<a id="opIdgetAppFeatures"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///app/{id}/features \
  -H 'Accept: application/json'

```

```http
GET ///app/{id}/features HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/features',
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
  'Accept':'application/json'

};

fetch('///app/{id}/features',
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
  'Accept' => 'application/json'
}

result = RestClient.get '///app/{id}/features',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('///app/{id}/features', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/features");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///app/{id}/features", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /app/{id}/features`

*Retrieve app features*

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
    "name": "CHAT",
    "implemented": true,
    "parentPrivilege": true
  }
]
```

<h3 id="getAppFeatures-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of app feature objects if they exist on the system.|Inline|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="getAppFeatures-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[AppFeature](#schemaappfeature)]|false|No description|
|» id|integer(int64)|false|Unique identifier for the app feature returned by the system.|
|» appId|integer(int64)|false|Unique identifier for the app that this app feature is associated with.|
|» name|[AppFeature/properties/name](#schemaappfeature/properties/name)|false|The app feature's name, meant to be displayable to the customer.|
|» implemented|boolean|false|Boolean flag indicating whether the feature is implemented.|
|» parentPrivilege|boolean|false|Boolean flag indicating whether the parents are allowed to turn off/on the feature.|

#### Enumerated Values

|Property|Value|
|---|---|
|name|ADVERTISING,|
|name|CHAT,|
|name|COMMENTS,|
|name|DATA_COLLECTION,|
|name|IN_APP_PURCHASES,|
|name|LOCATION_SHARING,|
|name|PAID_APP,|
|name|PUSH_NOTIFICATIONS,|
|name|SOCIAL_INTERACTION,|
|name|SUBSCRIPTION|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## setImplementedAppFeatures

<a id="opIdsetImplementedAppFeatures"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///app/{id}/implementedFeatures \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT ///app/{id}/implementedFeatures HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/implementedFeatures',
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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///app/{id}/implementedFeatures',
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
  'Accept' => 'application/json'
}

result = RestClient.put '///app/{id}/implementedFeatures',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('///app/{id}/implementedFeatures', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/implementedFeatures");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///app/{id}/implementedFeatures", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}/implementedFeatures`

*Set implemented features*

The publicly visible list of implemented features is important for transparency. From this list you can specify which ones the parents can customize their experience when you [Set parental features](/#operation--app--id--parentalFeatures-put).

> Body parameter

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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}
```

<h3 id="setImplementedAppFeatures-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[Approval](#schemaapproval)|true|The new Approval|

> Example responses

```json
[
  {
    "id": 12345678,
    "appId": 12,
    "name": "CHAT",
    "implemented": true,
    "parentPrivilege": true
  }
]
```

<h3 id="setImplementedAppFeatures-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of app feature objects.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="setImplementedAppFeatures-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[AppFeature](#schemaappfeature)]|false|No description|
|» id|integer(int64)|false|Unique identifier for the app feature returned by the system.|
|» appId|integer(int64)|false|Unique identifier for the app that this app feature is associated with.|
|» name|[AppFeature/properties/name](#schemaappfeature/properties/name)|false|The app feature's name, meant to be displayable to the customer.|
|» implemented|boolean|false|Boolean flag indicating whether the feature is implemented.|
|» parentPrivilege|boolean|false|Boolean flag indicating whether the parents are allowed to turn off/on the feature.|

#### Enumerated Values

|Property|Value|
|---|---|
|name|ADVERTISING,|
|name|CHAT,|
|name|COMMENTS,|
|name|DATA_COLLECTION,|
|name|IN_APP_PURCHASES,|
|name|LOCATION_SHARING,|
|name|PAID_APP,|
|name|PUSH_NOTIFICATIONS,|
|name|SOCIAL_INTERACTION,|
|name|SUBSCRIPTION|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## setParentalAppFeatures

<a id="opIdsetParentalAppFeatures"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///app/{id}/parentalFeatures \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT ///app/{id}/parentalFeatures HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///app/{id}/parentalFeatures',
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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///app/{id}/parentalFeatures',
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
  'Accept' => 'application/json'
}

result = RestClient.put '///app/{id}/parentalFeatures',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.put('///app/{id}/parentalFeatures', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///app/{id}/parentalFeatures");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///app/{id}/parentalFeatures", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /app/{id}/parentalFeatures`

*Set parental features*

Parental features allow parents to customize their experience with these features. It's up to developer's discretion to determine which features they wish to expose. Please [Set implemented features](/#operation--app--id--implementedFeatures-put) before setting parental features.

> Body parameter

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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}
```

<h3 id="setParentalAppFeatures-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|Unique identifier for the app.|
|body|body|[Approval](#schemaapproval)|true|The new Approval|

> Example responses

```json
[
  {
    "id": 12345678,
    "appId": 12,
    "name": "CHAT",
    "implemented": true,
    "parentPrivilege": true
  }
]
```

<h3 id="setParentalAppFeatures-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of app feature objects. Bare in mind that the `parental` flag will be set to `false` initially.|Inline|
|400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|The request was unacceptable, likely due to missing a required parameter.|[Error](#schemaerror)|
|401|[Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1)|No valid `Authentication` header provided.|[Error](#schemaerror)|
|404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|The specified resource was not found.|[Error](#schemaerror)|

<h3 id="setParentalAppFeatures-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[AppFeature](#schemaappfeature)]|false|No description|
|» id|integer(int64)|false|Unique identifier for the app feature returned by the system.|
|» appId|integer(int64)|false|Unique identifier for the app that this app feature is associated with.|
|» name|[AppFeature/properties/name](#schemaappfeature/properties/name)|false|The app feature's name, meant to be displayable to the customer.|
|» implemented|boolean|false|Boolean flag indicating whether the feature is implemented.|
|» parentPrivilege|boolean|false|Boolean flag indicating whether the parents are allowed to turn off/on the feature.|

#### Enumerated Values

|Property|Value|
|---|---|
|name|ADVERTISING,|
|name|CHAT,|
|name|COMMENTS,|
|name|DATA_COLLECTION,|
|name|IN_APP_PURCHASES,|
|name|LOCATION_SHARING,|
|name|PAID_APP,|
|name|PUSH_NOTIFICATIONS,|
|name|SOCIAL_INTERACTION,|
|name|SUBSCRIPTION|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

<h1 id="Saferize-API-Approval">Approval</h1>

An approval is created each time a child creates an account on the app. When this happens, the parent is given an opportunity to respond to the request by either approving or rejecting the app and validating relationship. Moreover, changes on the approval object by the parent reflect child's interaction with the app. The approval object is the intersection of Saferize (reword).

## initiateApproval

<a id="opIdinitiateApproval"></a>

> Code samples

```shell
# You can also use wget
curl -X POST ///approval \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST ///approval HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///approval',
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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///approval',
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
  'Accept' => 'application/json'
}

result = RestClient.post '///approval',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('///approval', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///approval");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///approval", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /approval`

*Initiate an approval*

To get parent consent to add a new app user (a child), a new approval object is created.

> Body parameter

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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}
```

<h3 id="initiateApproval-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Approval](#schemaapproval)|true|The new Approval|

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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}
```

<h3 id="initiateApproval-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Approval Created|[Approval](#schemaapproval)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## getApprovals

<a id="opIdgetApprovals"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///approval \
  -H 'Accept: */*'

```

```http
GET ///approval HTTP/1.1
Host: null

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*'

};

$.ajax({
  url: '///approval',
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
  'Accept':'*/*'

};

fetch('///approval',
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
  'Accept' => '*/*'
}

result = RestClient.get '///approval',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('///approval', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///approval");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///approval", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /approval`

*List all approvals*

> Example responses

<h3 id="getApprovals-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns all approvals|Inline|

<h3 id="getApprovals-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[Approval](#schemaapproval)]|false|No description|
|» id|integer(int64)|true|The Approval Id returned by the system|
|» appUser|[AppUser](#schemaappuser)|true|No description|
|»» id|integer(int64)|true|The AppUser Id returned by the system|
|»» token|string|true|A client token for the app. This is defined by the app and should be unique per user of the app.|
|»» app|[App](#schemaapp)|true|No description|
|»»» id|integer(int64)|true|Unique identifier for the app returned by the system.|
|»»» name|string|true|The name of the app.|
|»»» platforms|[string]|false|An array of enums that specify what platforms are supported by this app.|
|»»» category|string|false|One of the predifned values indicating the category of the app.|
|»»» timeRestriction|string|false|On/Off flag for enabling/disabling time restrictions on the app.|
|»»» status|string|false|Current lifecycle status of the app. Please read more on the requirements for publishing the app.|
|»»» description|string|false|A description of the app.|
|»»» urlName|string|false|The partial url name of this app on Saferize.|
|»»» details|[string]|false|Features implemented on the app.|
|»»» email|string|false|The app developer's email.|
|»» child|[Child](#schemachild)|true|No description|
|»»» id|integer(int64)|true|Unique identifier for the child returned by the system.|
|»»» firstName|string|true|Child's first name|
|»»» lastName|string|false|Child's last Name|
|»»» birthDate|string(date)|true|The childs date of birth|
|»»» family|[Family](#schemafamily)|true|No description|
|»»»» id|integer(int64)|true|Unique identifier for the family returned by the system.|
|»»»» name|string|true|The family name|
|»»» gender|string|true|The child's gender|
|»» family|[Family](#schemafamily)|true|No description|
|» approvalParent|[Parent](#schemaparent)|false|No description|
|»» id|integer(int64)|true|Unique identifier for the parent returned by the system.|
|»» firstName|string|true|First Name|
|»» lastName|string|true|Last Name|
|»» mobilePhone|string(phone)|false|Mobile Phone. The format should be XXXYYYZZZZ (no dashes or parenthesis)|
|»» family|[Family](#schemafamily)|true|No description|
|»» email|string(email)|true|No description|
|» family|[Family](#schemafamily)|true|No description|
|» statusTime|string(date-time)|true|The time and date of the last status change|
|» createdTime|string(date-time)|true|The time and date when this approval was created|
|» status|string|true|The approval status|
|» parentEmail|string|false|The email of the parent who received this request|
|» parentMobilePhone|string|false|The phone number of the parent who received this request|

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
|category|GAME|
|category|MEDIA|
|timeRestriction|ENABLED|
|timeRestriction|DISABLED|
|status|DRAFT|
|status|PUBLISHED|
|status|DELETED|
|details|SOCIAL_INTERACTION|
|details|IN_APP_PURCHASES|
|details|ADVERTISING|
|details|PAID_APP|
|details|SUBSCRIPTION|
|gender|MALE|
|gender|FEMALE|
|gender|UNKNOWN|
|status|PENDING|
|status|NOTIFIED|
|status|APPROVED|
|status|REJECTED|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## getApprovalById

<a id="opIdgetApprovalById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///approval/{id} \
  -H 'Accept: application/json'

```

```http
GET ///approval/{id} HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '///approval/{id}',
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
  'Accept':'application/json'

};

fetch('///approval/{id}',
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
  'Accept' => 'application/json'
}

result = RestClient.get '///approval/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('///approval/{id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///approval/{id}");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///approval/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /approval/{id}`

*Retrieve an approval*

<h3 id="getApprovalById-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|The identifier of the approval to retrieve.|

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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}
```

<h3 id="getApprovalById-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Return a single approval|[Approval](#schemaapproval)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## changeApproval

<a id="opIdchangeApproval"></a>

> Code samples

```shell
# You can also use wget
curl -X PATCH ///approval/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH ///approval/{id} HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///approval/{id}',
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
  "value": {}
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///approval/{id}',
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
  'Accept' => 'application/json'
}

result = RestClient.patch '///approval/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('///approval/{id}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///approval/{id}");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PATCH", "///approval/{id}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PATCH /approval/{id}`

*Update an approval*

> Body parameter

```json
{
  "op": "replace",
  "path": "/status",
  "value": {}
}
```

<h3 id="changeApproval-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|id|path|integer(int64)|true|The approval Id to get|
|body|body|[JsonPatch](#schemajsonpatch)|true|A JsonPatch array with the fields to be changed. Current supported fields are ~ status, child, features|

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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}
```

<h3 id="changeApproval-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Return the changed approval|[Approval](#schemaapproval)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## getApprovalByToken

<a id="opIdgetApprovalByToken"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///approval/token/{token} \
  -H 'Accept: application/json'

```

```http
GET ///approval/token/{token} HTTP/1.1
Host: null

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: '///approval/token/{token}',
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
  'Accept':'application/json'

};

fetch('///approval/token/{token}',
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
  'Accept' => 'application/json'
}

result = RestClient.get '///approval/token/{token}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('///approval/token/{token}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///approval/token/{token}");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///approval/token/{token}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /approval/token/{token}`

*Retrieve an approval via token*

<h3 id="getApprovalByToken-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|token|path|integer(int64)|true|The unique token assigned by the app to the approval.|

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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}
```

<h3 id="getApprovalByToken-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Return approval|[Approval](#schemaapproval)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

<h1 id="Saferize-API-Family">Family</h1>

Family methods provide access to information and operations relating to the Family. You can create, retrieve and update a family as well as list all it's members. You may also view all the validations of this family (such as Microtransaction, Email, SMS & Questionnaire)

## createFamily

<a id="opIdcreateFamily"></a>

> Code samples

```shell
# You can also use wget
curl -X POST ///family \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST ///family HTTP/1.1
Host: null
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: '///family',
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
  "id": 12345,
  "name": "Smith"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('///family',
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
  'Accept' => 'application/json'
}

result = RestClient.post '///family',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.post('///family', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///family");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///family", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /family`

*Create a family*

The family object is created when a child becomes an app user by parent consent. The family members are associated with this object.

> Body parameter

```json
{
  "id": 12345,
  "name": "Smith"
}
```

<h3 id="createFamily-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Family](#schemafamily)|true|The new Family to be created|

> Example responses

```json
{
  "id": 12345,
  "name": "Smith"
}
```

<h3 id="createFamily-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Return the new Family|[Family](#schemafamily)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## getFamily

<a id="opIdgetFamily"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///family/me \
  -H 'Accept: */*'

```

```http
GET ///family/me HTTP/1.1
Host: null

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*'

};

$.ajax({
  url: '///family/me',
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
  'Accept':'*/*'

};

fetch('///family/me',
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
  'Accept' => '*/*'
}

result = RestClient.get '///family/me',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('///family/me', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///family/me");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///family/me", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /family/me`

*Retrieve your family*

> Example responses

<h3 id="getFamily-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Return the Family|[Family](#schemafamily)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## updateFamily

<a id="opIdupdateFamily"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///family/me \
  -H 'Content-Type: application/json' \
  -H 'Accept: */*'

```

```http
PUT ///family/me HTTP/1.1
Host: null
Content-Type: application/json
Accept: */*

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

$.ajax({
  url: '///family/me',
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
  "id": 12345,
  "name": "Smith"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

fetch('///family/me',
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
  'Accept' => '*/*'
}

result = RestClient.put '///family/me',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': '*/*'
}

r = requests.put('///family/me', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///family/me");
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
        "Accept": []string{"*/*"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///family/me", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /family/me`

*Update your family*

> Body parameter

```json
{
  "id": 12345,
  "name": "Smith"
}
```

<h3 id="updateFamily-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Family](#schemafamily)|true|The changed family.|

> Example responses

<h3 id="updateFamily-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|The changed Family|[Family](#schemafamily)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

<h1 id="Saferize-API-Child">Child</h1>

The child object represents a child who can be on many different approvals (correlating to the number of the apps the user is registered on). You can create, retrieve and update a child. You may also view all the approvals associated with the child.

## getChildren

<a id="opIdgetChildren"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///child \
  -H 'Accept: */*'

```

```http
GET ///child HTTP/1.1
Host: null

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*'

};

$.ajax({
  url: '///child',
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
  'Accept':'*/*'

};

fetch('///child',
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
  'Accept' => '*/*'
}

result = RestClient.get '///child',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('///child', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///child");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///child", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /child`

*Get all children members of the family*

> Example responses

<h3 id="getChildren-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns an array of Child|Inline|

<h3 id="getChildren-responseschema">Response Schema</h3>

Status Code **200**

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|[[Child](#schemachild)]|false|No description|
|» id|integer(int64)|true|Unique identifier for the child returned by the system.|
|» firstName|string|true|Child's first name|
|» lastName|string|false|Child's last Name|
|» birthDate|string(date)|true|The childs date of birth|
|» family|[Family](#schemafamily)|true|No description|
|»» id|integer(int64)|true|Unique identifier for the family returned by the system.|
|»» name|string|true|The family name|
|» gender|string|true|The child's gender|

#### Enumerated Values

|Property|Value|
|---|---|
|gender|MALE|
|gender|FEMALE|
|gender|UNKNOWN|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## createChild

<a id="opIdcreateChild"></a>

> Code samples

```shell
# You can also use wget
curl -X POST ///child \
  -H 'Content-Type: application/json' \
  -H 'Accept: */*'

```

```http
POST ///child HTTP/1.1
Host: null
Content-Type: application/json
Accept: */*

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

$.ajax({
  url: '///child',
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
  "id": 1234567,
  "firstName": "Sofia",
  "lastName": "Smith",
  "birthDate": "2009-01-23T00:00:00.000Z",
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "gender": "FEMALE"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

fetch('///child',
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
  'Accept' => '*/*'
}

result = RestClient.post '///child',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': '*/*'
}

r = requests.post('///child', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///child");
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
        "Accept": []string{"*/*"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///child", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /child`

*Creates a new Child*

> Body parameter

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

<h3 id="createChild-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Child](#schemachild)|true|The Child to be created.|

> Example responses

<h3 id="createChild-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|The created Child|[Child](#schemachild)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## GetChildById

<a id="opIdGetChildById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///child/{childId} \
  -H 'Accept: */*'

```

```http
GET ///child/{childId} HTTP/1.1
Host: null

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*'

};

$.ajax({
  url: '///child/{childId}',
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
  'Accept':'*/*'

};

fetch('///child/{childId}',
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
  'Accept' => '*/*'
}

result = RestClient.get '///child/{childId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('///child/{childId}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///child/{childId}");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///child/{childId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /child/{childId}`

*Get a child via identifier*

<h3 id="GetChildById-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|childId|path|integer(int64)|true|The identifier of the child to retrieve.|

> Example responses

<h3 id="GetChildById-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the child|[Child](#schemachild)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## updateChild

<a id="opIdupdateChild"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///child/{childId} \
  -H 'Content-Type: application/json' \
  -H 'Accept: */*'

```

```http
PUT ///child/{childId} HTTP/1.1
Host: null
Content-Type: application/json
Accept: */*

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

$.ajax({
  url: '///child/{childId}',
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
  "id": 1234567,
  "firstName": "Sofia",
  "lastName": "Smith",
  "birthDate": "2009-01-23T00:00:00.000Z",
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "gender": "FEMALE"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

fetch('///child/{childId}',
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
  'Accept' => '*/*'
}

result = RestClient.put '///child/{childId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': '*/*'
}

r = requests.put('///child/{childId}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///child/{childId}");
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
        "Accept": []string{"*/*"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///child/{childId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /child/{childId}`

*Update a child via identifier*

> Body parameter

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

<h3 id="updateChild-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|childId|path|integer(int64)|true|Unique identifier for the child.|
|body|body|[Child](#schemachild)|true|The Child to be updated.|

> Example responses

<h3 id="updateChild-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the child|[Child](#schemachild)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

<h1 id="Saferize-API-Parent">Parent</h1>

The parent object administrates approval objects and child objects. You can create, retrieve and update a parent. You may also invite other parents, join them to the family and have them co-administrate approvals.

## post__parent

> Code samples

```shell
# You can also use wget
curl -X POST ///parent \
  -H 'Content-Type: application/json' \
  -H 'Accept: */*'

```

```http
POST ///parent HTTP/1.1
Host: null
Content-Type: application/json
Accept: */*

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

$.ajax({
  url: '///parent',
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
  "id": 123456,
  "firstName": "John",
  "lastName": "Smith",
  "mobilePhone": 41512345678,
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "email": "parent@example.com"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

fetch('///parent',
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
  'Accept' => '*/*'
}

result = RestClient.post '///parent',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': '*/*'
}

r = requests.post('///parent', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///parent");
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
        "Accept": []string{"*/*"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("POST", "///parent", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`POST /parent`

*Creates a new Parent*

> Body parameter

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

<h3 id="post__parent-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Parent](#schemaparent)|true|The parent to be created.|

> Example responses

<h3 id="post__parent-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the new Parent|[Parent](#schemaparent)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## getParentById

<a id="opIdgetParentById"></a>

> Code samples

```shell
# You can also use wget
curl -X GET ///parent/{parentId} \
  -H 'Accept: */*'

```

```http
GET ///parent/{parentId} HTTP/1.1
Host: null

Accept: */*

```

```javascript
var headers = {
  'Accept':'*/*'

};

$.ajax({
  url: '///parent/{parentId}',
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
  'Accept':'*/*'

};

fetch('///parent/{parentId}',
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
  'Accept' => '*/*'
}

result = RestClient.get '///parent/{parentId}',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Accept': '*/*'
}

r = requests.get('///parent/{parentId}', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///parent/{parentId}");
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
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("GET", "///parent/{parentId}", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`GET /parent/{parentId}`

*Gets a Parent by Id*

<h3 id="getParentById-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|parentId|path|integer(int64)|true|Unique identifier for the parent.|

> Example responses

<h3 id="getParentById-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Parent|[Parent](#schemaparent)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

## UpdateParent

<a id="opIdUpdateParent"></a>

> Code samples

```shell
# You can also use wget
curl -X PUT ///parent/me \
  -H 'Content-Type: application/json' \
  -H 'Accept: */*'

```

```http
PUT ///parent/me HTTP/1.1
Host: null
Content-Type: application/json
Accept: */*

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

$.ajax({
  url: '///parent/me',
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
  "id": 123456,
  "firstName": "John",
  "lastName": "Smith",
  "mobilePhone": 41512345678,
  "family": {
    "id": 12345,
    "name": "Smith"
  },
  "email": "parent@example.com"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'*/*'

};

fetch('///parent/me',
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
  'Accept' => '*/*'
}

result = RestClient.put '///parent/me',
  params: {
  }, headers: headers

p JSON.parse(result)

```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': '*/*'
}

r = requests.put('///parent/me', params={

}, headers = headers)

print r.json()

```

```java
URL obj = new URL("///parent/me");
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
        "Accept": []string{"*/*"},
        
    }

    data := bytes.NewBuffer([]byte{jsonReq})
    req, err := http.NewRequest("PUT", "///parent/me", data)
    req.Header = headers

    client := &http.Client{}
    resp, err := client.Do(req)
    // ...
}

```

`PUT /parent/me`

*Change the Parent*

> Body parameter

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

<h3 id="UpdateParent-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|body|body|[Parent](#schemaparent)|true|The Parent to be updated.|

> Example responses

<h3 id="UpdateParent-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Returns the changed Parent|[Parent](#schemaparent)|

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
None, None ( Scopes: read write )
</aside>

# Schemas

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
|name|string|true|The family name|

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
  "urlName": "string",
  "details": [
    "SOCIAL_INTERACTION",
    "IN_APP_PURCHASES"
  ],
  "email": "developer@example.com"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|Unique identifier for the app returned by the system.|
|name|string|true|The name of the app.|
|platforms|[string]|false|An array of enums that specify what platforms are supported by this app.|
|category|string|false|One of the predifned values indicating the category of the app.|
|timeRestriction|string|false|On/Off flag for enabling/disabling time restrictions on the app.|
|status|string|false|Current lifecycle status of the app. Please read more on the requirements for publishing the app.|
|description|string|false|A description of the app.|
|urlName|string|false|The partial url name of this app on Saferize.|
|details|[string]|false|Features implemented on the app.|
|email|string|false|The app developer's email.|

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
|category|GAME|
|category|MEDIA|
|timeRestriction|ENABLED|
|timeRestriction|DISABLED|
|status|DRAFT|
|status|PUBLISHED|
|status|DELETED|
|details|SOCIAL_INTERACTION|
|details|IN_APP_PURCHASES|
|details|ADVERTISING|
|details|PAID_APP|
|details|SUBSCRIPTION|

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
|firstName|string|true|First Name|
|lastName|string|true|Last Name|
|mobilePhone|string(phone)|false|Mobile Phone. The format should be XXXYYYZZZZ (no dashes or parenthesis)|
|family|[Family](#schemafamily)|true|No description|
|email|string(email)|true|No description|

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
|firstName|string|true|Child's first name|
|lastName|string|false|Child's last Name|
|birthDate|string(date)|true|The childs date of birth|
|family|[Family](#schemafamily)|true|No description|
|gender|string|true|The child's gender|

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
|mobilePhone|string|true|Developer's primary mobile phone number.|
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
    "urlName": "string",
    "details": [
      "SOCIAL_INTERACTION",
      "IN_APP_PURCHASES"
    ],
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
|id|integer(int64)|true|The AppUser Id returned by the system|
|token|string|true|A client token for the app. This is defined by the app and should be unique per user of the app.|
|app|[App](#schemaapp)|true|No description|
|child|[Child](#schemachild)|true|No description|
|family|[Family](#schemafamily)|true|No description|

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
      "urlName": "string",
      "details": [
        "SOCIAL_INTERACTION",
        "IN_APP_PURCHASES"
      ],
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
  "parentMobilePhone": 4151234567
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|true|The Approval Id returned by the system|
|appUser|[AppUser](#schemaappuser)|true|No description|
|approvalParent|[Parent](#schemaparent)|false|No description|
|family|[Family](#schemafamily)|true|No description|
|statusTime|string(date-time)|true|The time and date of the last status change|
|createdTime|string(date-time)|true|The time and date when this approval was created|
|status|string|true|The approval status|
|parentEmail|string|false|The email of the parent who received this request|
|parentMobilePhone|string|false|The phone number of the parent who received this request|

#### Enumerated Values

|Property|Value|
|---|---|
|status|PENDING|
|status|NOTIFIED|
|status|APPROVED|
|status|REJECTED|

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
|validatorName|[Validator](#schemavalidator)|false|No description|

<h2 id="tocSappfeature">AppFeature</h2>

<a id="schemaappfeature"></a>

```json
{
  "id": 12345678,
  "appId": 12,
  "name": "CHAT",
  "implemented": true,
  "parentPrivilege": true
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|false|Unique identifier for the app feature returned by the system.|
|appId|integer(int64)|false|Unique identifier for the app that this app feature is associated with.|
|name|string|false|The app feature's name, meant to be displayable to the customer.|
|implemented|boolean|false|Boolean flag indicating whether the feature is implemented.|
|parentPrivilege|boolean|false|Boolean flag indicating whether the parents are allowed to turn off/on the feature.|

#### Enumerated Values

|Property|Value|
|---|---|
|name|ADVERTISING,|
|name|CHAT,|
|name|COMMENTS,|
|name|DATA_COLLECTION,|
|name|IN_APP_PURCHASES,|
|name|LOCATION_SHARING,|
|name|PAID_APP,|
|name|PUSH_NOTIFICATIONS,|
|name|SOCIAL_INTERACTION,|
|name|SUBSCRIPTION|

<h2 id="tocSsubscriptionplan">SubscriptionPlan</h2>

<a id="schemasubscriptionplan"></a>

```json
{
  "id": 123456,
  "name": "Platinum starter",
  "billingCycle": "YEARLY",
  "active": true,
  "price": 299
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|id|integer(int64)|false|Unique identifier for the subscription plan returned by the system.|
|name|string|false|The plans’s name, meant to be displayable to the customer.|
|billingCycle|string|false|Specifies billing frequency.|
|active|boolean|false|Boolean flag representing whether the plan is active.|
|price|number(float)|false|The cost of the item as a positive float in the smallest currency unit (i.e. $2.99 will be represented as 299 cents).|

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
|width|integer(int64)|false|The witdh in pixels of the image object.|
|height|integer(int64)|false|The witdh in pixels of the image object.|

<h2 id="tocSvalidator">Validator</h2>

<a id="schemavalidator"></a>

```json
"Microtransaction"
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|*anonymous*|string|false|No description|

#### Enumerated Values

|Property|Value|
|---|---|
|*anonymous*|Microtransaction|
|*anonymous*|SMS|

<h2 id="tocSjsonpatch">JsonPatch</h2>

<a id="schemajsonpatch"></a>

```json
{
  "op": "replace",
  "path": "/status",
  "value": {}
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|op|string|false|Sort order:  * add - Ascending, from A to Z.  * replace - Descending, from Z to A.|
|path|string|false|the field to be updated using JsonPath syntax|
|value|object|false|No description|

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
  "type": "com.saferize.core.shared.DuplicateEntityException"
}
```

### Properties

|Name|Type|Required|Description|
|---|---|---|---|
|message|any|false|A human-readable message providing more details about the error.|
|type|string|true|No description|

