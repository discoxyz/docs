---
description: This page contains all relevant APIs interacting with Disco Personas.
---

# Personas

### Get Profile by DID&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/persona/did/{did}" method="get" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
{% code overflow="wrap" %}
```bash
curl --location 'https://api.disco.xyz/v1/credential/verify' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--header 'Authorization: Bearer <your Disco API key>' \
curl --location 'https://api.disco.xyz/v1/persona/did/did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb' \
--header 'Authorization: Bearer <your Disco API key>'
```
{% endcode %}
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/persona/did/did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}
{% endtabs %}

### Successful Response

```json
{
    "id": "3045c158-af4a-417f-a67f-bc8f916b5408",
    "user": {
        "id": "12a9e548-a2fb-42c6-ba4b-e931127baa4a"
    },
    "dids": [
        {
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "ethAddr": "0x9c7b16e49c2f579453c45ca0bf7771a43dc61449"
        }
    ],
    "handle": "provenauthority",
    "avatarUri": "https://uploads-ssl.webflow.com/634f227dc666d2739c1c3959/634f227dc666d26bd21c3a55_14-%20Evin%20McMullen%20original%20BW.png",
    "bio": "GM and welcome to the Disco! ",
    "ethAddress": "0x9c7b16e49c2f579453c45ca0bf7771a43dc61449",
    "links": [
        {
            "accountType": "Discord",
            "handle": "heyevin",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "proof": "https://discord.com/channels/947857036257935390/975763597529600041/1128736725682892930"
        },
        {
            "accountType": "Discord",
            "handle": "heyevin",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "proof": "https://twitter.com/provenauthority/status/1674454543420260352"
        },
        {
            "accountType": "Twitter",
            "handle": "provenauthority",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "proof": "https://twitter.com/provenauthority/status/1674454543420260352"
        }
    ],
    "metadata": {
        "orgBrand": {
            "textColor": null,
            "brandColor": null,
            "backgroundImage": null
        },
        "avatar": "https://uploads-ssl.webflow.com/634f227dc666d2739c1c3959/634f227dc666d26bd21c3a55_14-%20Evin%20McMullen%20original%20BW.png",
        "accountLinks": [
            {
                "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
                "type": "Discord",
                "handle": "heyevin"
            },
            {
                "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
                "type": "Discord",
                "handle": "heyevin"
            },
            {
                "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
                "type": "Twitter",
                "handle": "provenauthority"
            }
        ],
        "username": "provenauthority"
    },
    "isOrg": true
}
```

### Get Profile by Ethereum address

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/persona/find/eth/{eoa}" method="get" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
{% code overflow="wrap" %}
```bash
curl --location 'https://api.disco.xyz/v1/persona/find/eth/0x9c7b16e49c2f579453c45ca0bf7771a43dc61449' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer <your Disco API key>'

```
{% endcode %}
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Accept", "application/json");
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/persona/find/eth/0x9c7b16e49c2f579453c45ca0bf7771a43dc61449", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}
{% endtabs %}

### Successful Response

```json
{
    "id": "3045c158-af4a-417f-a67f-bc8f916b5408",
    "user": {
        "id": "12a9e548-a2fb-42c6-ba4b-e931127baa4a"
    },
    "dids": [
        {
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "ethAddr": "0x9c7b16e49c2f579453c45ca0bf7771a43dc61449"
        }
    ],
    "handle": "provenauthority",
    "avatarUri": "https://uploads-ssl.webflow.com/634f227dc666d2739c1c3959/634f227dc666d26bd21c3a55_14-%20Evin%20McMullen%20original%20BW.png",
    "bio": "GM and welcome to the Disco! ",
    "ethAddress": "0x9c7b16e49c2f579453c45ca0bf7771a43dc61449",
    "links": [
        {
            "accountType": "Discord",
            "handle": "heyevin",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "proof": "https://discord.com/channels/947857036257935390/975763597529600041/1128736725682892930"
        },
        {
            "accountType": "Discord",
            "handle": "heyevin",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "proof": "https://twitter.com/provenauthority/status/1674454543420260352"
        },
        {
            "accountType": "Twitter",
            "handle": "provenauthority",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "proof": "https://twitter.com/provenauthority/status/1674454543420260352"
        }
    ],
    "metadata": {
        "orgBrand": {
            "textColor": null,
            "brandColor": null,
            "backgroundImage": null
        },
        "avatar": "https://uploads-ssl.webflow.com/634f227dc666d2739c1c3959/634f227dc666d26bd21c3a55_14-%20Evin%20McMullen%20original%20BW.png",
        "accountLinks": [
            {
                "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
                "type": "Discord",
                "handle": "heyevin"
            },
            {
                "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
                "type": "Discord",
                "handle": "heyevin"
            },
            {
                "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
                "type": "Twitter",
                "handle": "provenauthority"
            }
        ],
        "username": "provenauthority"
    },
    "isOrg": true
}
```

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/persona/did/metadata/{did}" method="get" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
{% code overflow="wrap" %}
```bash
curl --location 'https://api.disco.xyz/v1/persona/did/metadata/did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb' \
--header 'Authorization: Bearer <your Disco API key>'
```
{% endcode %}
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/persona/did/metadata/did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}
{% endtabs %}

### Successful Response

```json
{
    "orgBrand": {
        "textColor": null,
        "brandColor": null,
        "backgroundImage": null
    },
    "avatar": "https://uploads-ssl.webflow.com/634f227dc666d2739c1c3959/634f227dc666d26bd21c3a55_14-%20Evin%20McMullen%20original%20BW.png",
    "accountLinks": [
        {
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "type": "Discord",
            "handle": "heyevin"
        },
        {
            "did": "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb",
            "type": "Twitter",
            "handle": "provenauthority"
        }
    ],
    "username": "provenauthority"
}
```

###

###

### Search for Profile by account linkages

Returns DIDs of matching handles given search input. Can search for Twitter, Discord, or Domain handle in one endpoint.

{% swagger method="get" path="" baseUrl="https://api.disco.xyz/v1/search/?handle=provenauthority" summary="Search by any handle" expanded="true" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="handle" type="String" %}
handle of Account Linked to search for. This can be a twitter, discord, or domain.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful Operation" %}
**Example Response**

```json
[
    "did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb"
]
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized. Request not authenticated, API token is missing or invalid!" %}

{% endswagger-response %}

{% swagger-response status="403: Forbidden" description=" Forbidden. You don't have access to the relevant resource. " %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Resource not found" %}

{% endswagger-response %}
{% endswagger %}
