---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Retrieving Credentials

## Introduction

Access to credentials is based on API key ownership:

* If a Credential is is marked `public` (`isPublic=true`) any API key can be used to retrieve it
* If a Credential is is marked `private` (`isPublic=false`) only the API keys for the `issuer` and the `recipient` will have access to retrieve it.

## Get a single Credential based on its ID.&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credential/{id}" method="get" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
{% code overflow="wrap" %}
```bash
# Looking up id=https://api.disco.xyz/credential/22d9187b-8a33-4e17-b05f-c8192107ab28
curl --location 'https://api.disco.xyz/v1/credential/https%3A%2F%2Fapi.disco.xyz%2Fcredential%2F22d9187b-8a33-4e17-b05f-c8192107ab28' \
--header 'Authorization: Bearer <your Disco API key>'
```
{% endcode %}
{% endtab %}

{% tab title="JavaScript" %}
{% code overflow="wrap" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/credential/https%3A%2F%2Fapi.disco.xyz%2Fcredential%2F3f929a36-8e1c-46c1-9981-120b43241c13", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endcode %}
{% endtab %}
{% endtabs %}

Credential returned on successful call:

```json
{
    "_id": "65099e2e52bf698c21aeeb91",
    "vc": {
        "@context": [
            "https://www.w3.org/2018/credentials/v1"
        ],
        "type": [
            "VerifiableCredential",
            "MembershipCredential"
        ],
        "issuer": {
            "id": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt"
        },
        "issuanceDate": "2023-09-19T13:12:14.801Z",
        "id": "https://api.disco.xyz/credential/22d9187b-8a33-4e17-b05f-c8192107ab28",
        "credentialSubject": {
            "id": "did:ethr:0x08936438bfb8e9b269f978d5327ad684f47f8c05",
            "organization": "House of Leroy"
        },
        "expirationDate": "2024-08-29T00:00:00.000Z",
        "credentialSchema": {
            "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
            "type": "JsonSchemaValidator2018"
        },
        "proof": {
            "verificationMethod": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#controller",
            "created": "2023-09-19T13:12:14.827Z",
            "proofPurpose": "assertionMethod",
            "type": "EthereumEip712Signature2021",
            "proofValue": "0x3aa89255fe63d7ca70c43b0603aa3d004978bc0815b35ae5dcbf84a3df4867f133b6f0d717916cf84b8f6b3dcbf6a7643f18fa00557c0ddb5f5571cc8f678d291c",
            "eip712Domain": {
                "domain": {
                    "chainId": 1,
                    "name": "Disco Verifiable Credential",
                    "version": "1"
                },
                "messageSchema": {
                    "EIP712Domain": [
                        {
                            "name": "name",
                            "type": "string"
                        },
                        {
                            "name": "version",
                            "type": "string"
                        },
                        {
                            "name": "chainId",
                            "type": "uint256"
                        }
                    ],
                    "Proof": [
                        {
                            "name": "created",
                            "type": "string"
                        },
                        {
                            "name": "proofPurpose",
                            "type": "string"
                        },
                        {
                            "name": "type",
                            "type": "string"
                        },
                        {
                            "name": "verificationMethod",
                            "type": "string"
                        }
                    ],
                    "Issuer": [
                        {
                            "name": "id",
                            "type": "string"
                        }
                    ],
                    "CredentialSubject": [
                        {
                            "name": "id",
                            "type": "string"
                        },
                        {
                            "name": "organization",
                            "type": "string"
                        }
                    ],
                    "VerifiableCredential": [
                        {
                            "name": "@context",
                            "type": "string[]"
                        },
                        {
                            "name": "credentialSubject",
                            "type": "CredentialSubject"
                        },
                        {
                            "name": "id",
                            "type": "string"
                        },
                        {
                            "name": "issuanceDate",
                            "type": "string"
                        },
                        {
                            "name": "issuer",
                            "type": "Issuer"
                        },
                        {
                            "name": "proof",
                            "type": "Proof"
                        },
                        {
                            "name": "type",
                            "type": "string[]"
                        }
                    ]
                },
                "primaryType": "VerifiableCredential"
            }
        }
    },
    "isPublic": true,
    "issuer": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt",
    "recipient": "did:ethr:0x08936438bfb8e9B269F978D5327Ad684f47F8C05",
    "subject": "did:ethr:0x08936438bfb8e9B269F978D5327Ad684f47F8C05",
    "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
    "isDeleted": false,
    "genId": "9af80795-09f5-48a7-abd7-d713a8cd2447",
    "updatedAt": "2023-09-20T18:34:29.629Z",
    "history": [
        "{\"field\":\"isPublic\",\"oldValue\":false,\"newValue\":true,\"updatedAt\":\"2023-09-20T18:34:29.629Z\"}"
    ]
}
```

## Get a multiple Credentials&#x20;

### Get a multiple Credentials for a single DID&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credentials/{did}" method="get" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
{% code overflow="wrap" %}
```bash
curl --location 'https://api.disco.xyz/v1/credentials/did:3:kjzl6cwe1jw145lzc8sbpnziei0t76kthtp4ep5xhlewakg385sno7ndm5qjsd2?page=1&size=2000' \
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

fetch("https://api.disco.xyz/v1/credentials/did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6?page=1&size=2000", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}
{% endtabs %}

Credential returned on successful call:

<pre class="language-json"><code class="lang-json"><strong>[
</strong>    {
        "_id": "6512f130b8ffec6244182a80",
        "vc": {
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "type": [
                "VerifiableCredential",
                "GmCredential"
            ],
            "issuer": {
                "id": "did:web:api.disco.xyz/v1/mick"
            },
            "issuanceDate": "2023-09-26T14:56:48.624Z",
            "id": "https://api.disco.xyz/credential/f0067c2c-beef-4c82-a541-60d2c31b280f",
            "credentialSubject": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6"
            },
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            }
        },
        "isPublic": true,
        "issuer": "did:web:api.disco.xyz/v1/mick",
        "recipient": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "subject": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
        "isDeleted": false,
        "genId": "72825873-0ae9-4394-8227-30e641d40b14",
        "updatedAt": "2023-09-26T15:00:27.383Z",
        "history": [
            "{\"field\":\"isPublic\",\"oldValue\":false,\"newValue\":true,\"updatedAt\":\"2023-09-26T15:00:27.383Z\"}"
        ],
        "jwt": "eyJhbGciOiJFUzI1NksiLCJ0eXAiOiJKV1QifQ.eyJ2YyI6eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSJdLCJ0eXBlIjpbIlZlcmlmaWFibGVDcmVkZW50aWFsIiwiR21DcmVkZW50aWFsIl0sImNyZWRlbnRpYWxTdWJqZWN0Ijp7ImlkIjoiZGlkOjM6a2p6bDZjd2UxancxNDlseWxpeWZoNG1iamd5NTlyaG9rdGtoc29jN3N1dTJ0cnFqZTJ3aWdyZ2VhMjFicXk2In0sImNyZWRlbnRpYWxTY2hlbWEiOnsiaWQiOiJodHRwczovL3Jhdy5naXRodWJ1c2VyY29udGVudC5jb20vZGlzY294eXovZGlzY28tc2NoZW1hcy9tYWluL2pzb24vR01DcmVkZW50aWFsLzEtMC0wLmpzb24iLCJ0eXBlIjoiSnNvblNjaGVtYVZhbGlkYXRvcjIwMTgifX0sIkBjb250ZXh0IjpbImh0dHBzOi8vd3d3LnczLm9yZy8yMDE4L2NyZWRlbnRpYWxzL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJHbUNyZWRlbnRpYWwiXSwiaXNzdWVyIjp7ImlkIjoiZGlkOndlYjphcGkuZGlzY28ueHl6L3YxL21pY2sifSwiaXNzdWFuY2VEYXRlIjoiMjAyMy0wOS0yNlQxNDo1Njo0OC42MjRaIiwiaWQiOiJodHRwczovL2FwaS5kaXNjby54eXovY3JlZGVudGlhbC9mMDA2N2MyYy1iZWVmLTRjODItYTU0MS02MGQyYzMxYjI4MGYiLCJjcmVkZW50aWFsU3ViamVjdCI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiJ9LCJjcmVkZW50aWFsU2NoZW1hIjp7ImlkIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Rpc2NveHl6L2Rpc2NvLXNjaGVtYXMvbWFpbi9qc29uL0dNQ3JlZGVudGlhbC8xLTAtMC5qc29uIiwidHlwZSI6Ikpzb25TY2hlbWFWYWxpZGF0b3IyMDE4In0sInN1YiI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiIsImp0aSI6Imh0dHBzOi8vYXBpLmRpc2NvLnh5ei9jcmVkZW50aWFsL2YwMDY3YzJjLWJlZWYtNGM4Mi1hNTQxLTYwZDJjMzFiMjgwZiIsIm5iZiI6MTY5NTc0MDIwOCwiaXNzIjoiZGlkOndlYjphcGkuZGlzY28ueHl6L3YxL21pY2sifQ.UOeY-tcmUCZoHlgrIvqGonuD3OPbXBwAAWLhVcB9BYUZibSS6OzKhSmTLKfUePEUqfsnwf7mFouSef8aJ2AM3Q"
    },
    {
        "_id": "6511fa409983d3667ee2f577",
        "vc": {
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "type": [
                "VerifiableCredential",
                "DarkModePreferenceCredential"
            ],
            "issuer": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6"
            },
            "issuanceDate": "2023-09-25T21:23:12.769Z",
            "id": "https://api.disco.xyz/credential/b37572b8-cdf3-4181-8f25-7518ed3dac4f",
            "credentialSubject": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "preference": "Light"
            },
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/DarkModePrefCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            }
        },
        "recipient": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "subject": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "isPublic": true,
        "isDeleted": false,
        "issuer": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/DarkModePrefCredential/1-0-0.json",
        "genId": "4f7fb2f4-3b01-4800-9c0d-d523f7f9dbc1",
        "updatedAt": "2023-09-25T21:23:37.747Z",
        "history": [
            "{\"field\":\"jwt\",\"newValue\":\"eyJraWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTY_dmVyc2lvbi1pZD0wIzRjaDdlTkZXY0d6UzNnMyIsImFsZyI6IkVTMjU2SyJ9.eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSJdLCJjcmVkZW50aWFsU2NoZW1hIjp7ImlkIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Rpc2NveHl6L2Rpc2NvLXNjaGVtYXMvbWFpbi9qc29uL0RhcmtNb2RlUHJlZkNyZWRlbnRpYWwvMS0wLTAuanNvbiIsInR5cGUiOiJKc29uU2NoZW1hVmFsaWRhdG9yMjAxOCJ9LCJjcmVkZW50aWFsU3ViamVjdCI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiIsInByZWZlcmVuY2UiOiJMaWdodCJ9LCJpZCI6Imh0dHBzOi8vYXBpLmRpc2NvLnh5ei9jcmVkZW50aWFsL2IzNzU3MmI4LWNkZjMtNDE4MS04ZjI1LTc1MThlZDNkYWM0ZiIsImlzc3VhbmNlRGF0ZSI6IjIwMjMtMDktMjVUMjE6MjM6MTIuNzY5WiIsImlzc3VlciI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiJ9LCJ0eXBlIjpbIlZlcmlmaWFibGVDcmVkZW50aWFsIiwiRGFya01vZGVQcmVmZXJlbmNlQ3JlZGVudGlhbCJdfQ.JbxtL84rA30yB_zw8qlkAR-qSFN6aBuHElv2wvItc91gaKunRmr8MxD65v_mjgwWtsDrCgpsaoucfqe5I9fylw\",\"updatedAt\":\"2023-09-25T21:23:14.285Z\"}",
            "{\"field\":\"isPublic\",\"oldValue\":false,\"newValue\":true,\"updatedAt\":\"2023-09-25T21:23:37.747Z\"}"
        ],
        "jwt": "eyJraWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTY_dmVyc2lvbi1pZD0wIzRjaDdlTkZXY0d6UzNnMyIsImFsZyI6IkVTMjU2SyJ9.eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSJdLCJjcmVkZW50aWFsU2NoZW1hIjp7ImlkIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Rpc2NveHl6L2Rpc2NvLXNjaGVtYXMvbWFpbi9qc29uL0RhcmtNb2RlUHJlZkNyZWRlbnRpYWwvMS0wLTAuanNvbiIsInR5cGUiOiJKc29uU2NoZW1hVmFsaWRhdG9yMjAxOCJ9LCJjcmVkZW50aWFsU3ViamVjdCI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiIsInByZWZlcmVuY2UiOiJMaWdodCJ9LCJpZCI6Imh0dHBzOi8vYXBpLmRpc2NvLnh5ei9jcmVkZW50aWFsL2IzNzU3MmI4LWNkZjMtNDE4MS04ZjI1LTc1MThlZDNkYWM0ZiIsImlzc3VhbmNlRGF0ZSI6IjIwMjMtMDktMjVUMjE6MjM6MTIuNzY5WiIsImlzc3VlciI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiJ9LCJ0eXBlIjpbIlZlcmlmaWFibGVDcmVkZW50aWFsIiwiRGFya01vZGVQcmVmZXJlbmNlQ3JlZGVudGlhbCJdfQ.JbxtL84rA30yB_zw8qlkAR-qSFN6aBuHElv2wvItc91gaKunRmr8MxD65v_mjgwWtsDrCgpsaoucfqe5I9fylw"
    }
<strong>]
</strong></code></pre>

### Get a multiple Credentials for multiple DIDs&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credentials/multi" method="post" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
```bash
curl --location 'https://api.disco.xyz/v1/credentials/multi' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your Disco API key>' \
--data '{
  "dids": [
      "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6", 
      "did:ethr:0x08936438bfb8e9B269F978D5327Ad684f47F8C05"
  ],
  "tab": "public",
  "page": 1,
  "size": 0
}'

```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var raw = JSON.stringify({
  "dids": [
    "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
    "did:ethr:0x08936438bfb8e9B269F978D5327Ad684f47F8C05"
  ],
  "tab": "public",
  "page": 1,
  "size": 0
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/credentials/multi", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}
{% endtabs %}

Credential returned on successful call:

```json
[
    {
        "_id": "6512f130b8ffec6244182a80",
        "vc": {
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "type": [
                "VerifiableCredential",
                "GmCredential"
            ],
            "issuer": {
                "id": "did:web:api.disco.xyz/v1/mick"
            },
            "issuanceDate": "2023-09-26T14:56:48.624Z",
            "id": "https://api.disco.xyz/credential/f0067c2c-beef-4c82-a541-60d2c31b280f",
            "credentialSubject": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6"
            },
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            }
        },
        "isPublic": true,
        "issuer": "did:web:api.disco.xyz/v1/mick",
        "recipient": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "subject": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
        "isDeleted": false,
        "genId": "72825873-0ae9-4394-8227-30e641d40b14",
        "updatedAt": "2023-09-26T15:00:27.383Z",
        "history": [
            "{\"field\":\"isPublic\",\"oldValue\":false,\"newValue\":true,\"updatedAt\":\"2023-09-26T15:00:27.383Z\"}"
        ],
        "jwt": "eyJhbGciOiJFUzI1NksiLCJ0eXAiOiJKV1QifQ.eyJ2YyI6eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSJdLCJ0eXBlIjpbIlZlcmlmaWFibGVDcmVkZW50aWFsIiwiR21DcmVkZW50aWFsIl0sImNyZWRlbnRpYWxTdWJqZWN0Ijp7ImlkIjoiZGlkOjM6a2p6bDZjd2UxancxNDlseWxpeWZoNG1iamd5NTlyaG9rdGtoc29jN3N1dTJ0cnFqZTJ3aWdyZ2VhMjFicXk2In0sImNyZWRlbnRpYWxTY2hlbWEiOnsiaWQiOiJodHRwczovL3Jhdy5naXRodWJ1c2VyY29udGVudC5jb20vZGlzY294eXovZGlzY28tc2NoZW1hcy9tYWluL2pzb24vR01DcmVkZW50aWFsLzEtMC0wLmpzb24iLCJ0eXBlIjoiSnNvblNjaGVtYVZhbGlkYXRvcjIwMTgifX0sIkBjb250ZXh0IjpbImh0dHBzOi8vd3d3LnczLm9yZy8yMDE4L2NyZWRlbnRpYWxzL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJHbUNyZWRlbnRpYWwiXSwiaXNzdWVyIjp7ImlkIjoiZGlkOndlYjphcGkuZGlzY28ueHl6L3YxL21pY2sifSwiaXNzdWFuY2VEYXRlIjoiMjAyMy0wOS0yNlQxNDo1Njo0OC42MjRaIiwiaWQiOiJodHRwczovL2FwaS5kaXNjby54eXovY3JlZGVudGlhbC9mMDA2N2MyYy1iZWVmLTRjODItYTU0MS02MGQyYzMxYjI4MGYiLCJjcmVkZW50aWFsU3ViamVjdCI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiJ9LCJjcmVkZW50aWFsU2NoZW1hIjp7ImlkIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Rpc2NveHl6L2Rpc2NvLXNjaGVtYXMvbWFpbi9qc29uL0dNQ3JlZGVudGlhbC8xLTAtMC5qc29uIiwidHlwZSI6Ikpzb25TY2hlbWFWYWxpZGF0b3IyMDE4In0sInN1YiI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiIsImp0aSI6Imh0dHBzOi8vYXBpLmRpc2NvLnh5ei9jcmVkZW50aWFsL2YwMDY3YzJjLWJlZWYtNGM4Mi1hNTQxLTYwZDJjMzFiMjgwZiIsIm5iZiI6MTY5NTc0MDIwOCwiaXNzIjoiZGlkOndlYjphcGkuZGlzY28ueHl6L3YxL21pY2sifQ.UOeY-tcmUCZoHlgrIvqGonuD3OPbXBwAAWLhVcB9BYUZibSS6OzKhSmTLKfUePEUqfsnwf7mFouSef8aJ2AM3Q"
    }, 

          ...

    {
        "_id": "6501f286152e472a385895f1",
        "vc": {
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "id": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#31c2cc7e-ae16-4480-a43f-8559378f57fd",
            "type": [
                "VerifiableCredential",
                "OfficialDisconautCredential"
            ],
            "proof": {
                "type": "EthereumEip712Signature2021",
                "created": "2023-02-24T13:17:04.896Z",
                "proofValue": "0xc2536cae06a7b55c6ae664a1b18e91d6599c19843c40d4dfc6ffe9cd767078744f0b0f44577497f46204289ed2c01ca83f956a1e801579e8e99d982662c22b2e1c",
                "eip712Domain": {
                    "domain": {
                        "name": "Disco Verifiable Credential",
                        "chainId": 1,
                        "version": "1"
                    },
                    "primaryType": "VerifiableCredential",
                    "messageSchema": {
                        "Proof": [
                            {
                                "name": "created",
                                "type": "string"
                            },
                            {
                                "name": "proofPurpose",
                                "type": "string"
                            },
                            {
                                "name": "type",
                                "type": "string"
                            },
                            {
                                "name": "verificationMethod",
                                "type": "string"
                            }
                        ],
                        "Issuer": [
                            {
                                "name": "id",
                                "type": "string"
                            }
                        ],
                        "EIP712Domain": [
                            {
                                "name": "name",
                                "type": "string"
                            },
                            {
                                "name": "version",
                                "type": "string"
                            },
                            {
                                "name": "chainId",
                                "type": "uint256"
                            }
                        ],
                        "CredentialSubject": [
                            {
                                "name": "id",
                                "type": "string"
                            }
                        ],
                        "VerifiableCredential": [
                            {
                                "name": "@context",
                                "type": "string[]"
                            },
                            {
                                "name": "credentialSubject",
                                "type": "CredentialSubject"
                            },
                            {
                                "name": "id",
                                "type": "string"
                            },
                            {
                                "name": "issuanceDate",
                                "type": "string"
                            },
                            {
                                "name": "issuer",
                                "type": "Issuer"
                            },
                            {
                                "name": "proof",
                                "type": "Proof"
                            },
                            {
                                "name": "type",
                                "type": "string[]"
                            }
                        ]
                    }
                },
                "proofPurpose": "assertionMethod",
                "verificationMethod": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#controller"
            },
            "issuer": {
                "id": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt"
            },
            "issuanceDate": "2023-02-24T13:17:04.895Z",
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OfficialDisconautCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            },
            "credentialSubject": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "edition": 1
            }
        },
        "genId": "c26c72ba-3fc1-452b-b473-f648e178b07d",
        "isPublic": true,
        "isDeleted": false,
        "issuer": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt",
        "recipient": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "subject": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "updatedAt": "2023-02-24T13:17:04.895Z",
        "jwt": "",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OfficialDisconautCredential/1-0-0.json",
        "history": [
            "Migrated from ceramic public tile on 2023-09-13T17:33:58.133Z"
        ]
    }
]
```

### Get a multiple Credentials searching on a Credential attribute&#x20;

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credentials/search" method="get" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credentials/search" method="post" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
{% code overflow="wrap" %}
```bash
# Using GET with query parameters
curl --location 'https://api.disco.xyz/v1/credentials/search?field=issuer&op=%3D&value=did%3A3%3Akjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6&page=1&size=10' \
--header 'Authorization: Bearer <your Disco API key>'

# Using POST with body parameters
curl --location 'https://api.disco.xyz/v1/credentials/search' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your Disco API key>' \
--data '{
    "criteria": [
        {
            "field": "issuer",
            "operator": "=",
            "value": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6"
        }
    ],
    "conjunction": "and",
    "page": 1,
    "size": 100
}'
```
{% endcode %}
{% endtab %}

{% tab title="JavaScript" %}
{% code overflow="wrap" %}
```javascript
/*** Using GET with query parameters ***/
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/credentials/search?field=issuer&op==&value=did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6&page=1&size=10", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));


/*** Using POST with body parameters ***/
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Authorization", "Bearer b499e2ff-92a9-49b3-b4f7-e7cf756b7b5d");

var raw = JSON.stringify({
  "criteria": [
    {
      "field": "issuer",
      "operator": "=",
      "value": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6"
    }
  ],
  "conjunction": "and",
  "page": 1,
  "size": 100
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/credentials/search", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endcode %}
{% endtab %}
{% endtabs %}

Credentials returned on successful call:

```json
[
    {
        "_id": "6501f286152e472a385895f2",
        "vc": {
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6#8208d6eb-fd0e-447a-a57a-f7518cfa02cc",
            "type": [
                "VerifiableCredential",
                "TshirtSizeCredential"
            ],
            "proof": {
                "jwt": "eyJraWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTY_dmVyc2lvbi1pZD0wIzRjaDdlTkZXY0d6UzNnMyIsImFsZyI6IkVTMjU2SyJ9.eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSJdLCJjcmVkZW50aWFsU2NoZW1hIjp7ImlkIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Rpc2NveHl6L2Rpc2NvLXNjaGVtYXMvbWFpbi9qc29uL1RzaGlydFNpemVDcmVkZW50aWFsLzEtMC0wLmpzb24iLCJ0eXBlIjoiSnNvblNjaGVtYVZhbGlkYXRvcjIwMTgifSwiY3JlZGVudGlhbFN1YmplY3QiOnsiaWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTYiLCJ0c2hpcnRTaXplIjoiTCAtIFVuaXNleCJ9LCJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiM4MjA4ZDZlYi1mZDBlLTQ0N2EtYTU3YS1mNzUxOGNmYTAyY2MiLCJpc3N1YW5jZURhdGUiOiIyMDIzLTAyLTI0VDIxOjQ0OjI1Ljc4NloiLCJpc3N1ZXIiOnsiaWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTYifSwidHlwZSI6WyJWZXJpZmlhYmxlQ3JlZGVudGlhbCIsIlRzaGlydFNpemVDcmVkZW50aWFsIl19._2FzJso_mxjdIN4Lh0ZsJhAINe3gL89qLwgLodlKhxc5G7sZyY0dObQTjiS2J378dxi6nk6KmGXmUymJ8-OrsQ"
            },
            "issuer": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6"
            },
            "issuanceDate": "2023-02-24T21:44:25.786Z",
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/TshirtSizeCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            },
            "credentialSubject": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "tshirtSize": "L - Unisex"
            }
        },
        "genId": "41bffd60-0567-4c77-9b9b-f7ca8daf96dc",
        "isPublic": true,
        "isDeleted": false,
        "issuer": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "recipient": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "subject": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "updatedAt": "2023-02-24T21:44:25.786Z",
        "jwt": "eyJraWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTY_dmVyc2lvbi1pZD0wIzRjaDdlTkZXY0d6UzNnMyIsImFsZyI6IkVTMjU2SyJ9.eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSJdLCJjcmVkZW50aWFsU2NoZW1hIjp7ImlkIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Rpc2NveHl6L2Rpc2NvLXNjaGVtYXMvbWFpbi9qc29uL1RzaGlydFNpemVDcmVkZW50aWFsLzEtMC0wLmpzb24iLCJ0eXBlIjoiSnNvblNjaGVtYVZhbGlkYXRvcjIwMTgifSwiY3JlZGVudGlhbFN1YmplY3QiOnsiaWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTYiLCJ0c2hpcnRTaXplIjoiTCAtIFVuaXNleCJ9LCJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiM4MjA4ZDZlYi1mZDBlLTQ0N2EtYTU3YS1mNzUxOGNmYTAyY2MiLCJpc3N1YW5jZURhdGUiOiIyMDIzLTAyLTI0VDIxOjQ0OjI1Ljc4NloiLCJpc3N1ZXIiOnsiaWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTYifSwidHlwZSI6WyJWZXJpZmlhYmxlQ3JlZGVudGlhbCIsIlRzaGlydFNpemVDcmVkZW50aWFsIl19._2FzJso_mxjdIN4Lh0ZsJhAINe3gL89qLwgLodlKhxc5G7sZyY0dObQTjiS2J378dxi6nk6KmGXmUymJ8-OrsQ",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/TshirtSizeCredential/1-0-0.json",
        "history": [
            "Migrated from ceramic public tile on 2023-09-13T17:33:58.133Z"
        ]
    },

    ...

    {
        "_id": "6501f286152e472a385895f6",
        "vc": {
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6#cc7fdef8-1eb0-461e-81fc-7a3dc6ca7166",
            "type": [
                "VerifiableCredential",
                "DarkModePreferenceCredential"
            ],
            "proof": {
                "jwt": "eyJraWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTY_dmVyc2lvbi1pZD0wIzRjaDdlTkZXY0d6UzNnMyIsImFsZyI6IkVTMjU2SyJ9.eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSJdLCJjcmVkZW50aWFsU2NoZW1hIjp7ImlkIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Rpc2NveHl6L2Rpc2NvLXNjaGVtYXMvbWFpbi9qc29uL0RhcmtNb2RlUHJlZkNyZWRlbnRpYWwvMS0wLTAuanNvbiIsInR5cGUiOiJKc29uU2NoZW1hVmFsaWRhdG9yMjAxOCJ9LCJjcmVkZW50aWFsU3ViamVjdCI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiIsInByZWZlcmVuY2UiOiJEYXJrIn0sImlkIjoiZGlkOjM6a2p6bDZjd2UxancxNDlseWxpeWZoNG1iamd5NTlyaG9rdGtoc29jN3N1dTJ0cnFqZTJ3aWdyZ2VhMjFicXk2I2NjN2ZkZWY4LTFlYjAtNDYxZS04MWZjLTdhM2RjNmNhNzE2NiIsImlzc3VhbmNlRGF0ZSI6IjIwMjMtMDItMjRUMjE6NDM6MjUuNDg4WiIsImlzc3VlciI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiJ9LCJ0eXBlIjpbIlZlcmlmaWFibGVDcmVkZW50aWFsIiwiRGFya01vZGVQcmVmZXJlbmNlQ3JlZGVudGlhbCJdfQ.yjNmJRq6TryjOx8T-mj-bVYV439J5dk3S_P2374_mV1rSvuvjZJIQjtzseXoyQiiVol7Qpr4GRyZ5DI1ZCO2NQ"
            },
            "issuer": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6"
            },
            "issuanceDate": "2023-02-24T21:43:25.488Z",
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/DarkModePrefCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            },
            "credentialSubject": {
                "id": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "preference": "Dark"
            }
        },
        "genId": "42ce2ef2-7aa4-42af-80b5-010a43c40d95",
        "isPublic": true,
        "isDeleted": false,
        "issuer": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "recipient": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "subject": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
        "updatedAt": "2023-02-24T21:43:25.488Z",
        "jwt": "eyJraWQiOiJkaWQ6MzpranpsNmN3ZTFqdzE0OWx5bGl5Zmg0bWJqZ3k1OXJob2t0a2hzb2M3c3V1MnRycWplMndpZ3JnZWEyMWJxeTY_dmVyc2lvbi1pZD0wIzRjaDdlTkZXY0d6UzNnMyIsImFsZyI6IkVTMjU2SyJ9.eyJAY29udGV4dCI6WyJodHRwczovL3d3dy53My5vcmcvMjAxOC9jcmVkZW50aWFscy92MSJdLCJjcmVkZW50aWFsU2NoZW1hIjp7ImlkIjoiaHR0cHM6Ly9yYXcuZ2l0aHVidXNlcmNvbnRlbnQuY29tL2Rpc2NveHl6L2Rpc2NvLXNjaGVtYXMvbWFpbi9qc29uL0RhcmtNb2RlUHJlZkNyZWRlbnRpYWwvMS0wLTAuanNvbiIsInR5cGUiOiJKc29uU2NoZW1hVmFsaWRhdG9yMjAxOCJ9LCJjcmVkZW50aWFsU3ViamVjdCI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiIsInByZWZlcmVuY2UiOiJEYXJrIn0sImlkIjoiZGlkOjM6a2p6bDZjd2UxancxNDlseWxpeWZoNG1iamd5NTlyaG9rdGtoc29jN3N1dTJ0cnFqZTJ3aWdyZ2VhMjFicXk2I2NjN2ZkZWY4LTFlYjAtNDYxZS04MWZjLTdhM2RjNmNhNzE2NiIsImlzc3VhbmNlRGF0ZSI6IjIwMjMtMDItMjRUMjE6NDM6MjUuNDg4WiIsImlzc3VlciI6eyJpZCI6ImRpZDozOmtqemw2Y3dlMWp3MTQ5bHlsaXlmaDRtYmpneTU5cmhva3RraHNvYzdzdXUydHJxamUyd2lncmdlYTIxYnF5NiJ9LCJ0eXBlIjpbIlZlcmlmaWFibGVDcmVkZW50aWFsIiwiRGFya01vZGVQcmVmZXJlbmNlQ3JlZGVudGlhbCJdfQ.yjNmJRq6TryjOx8T-mj-bVYV439J5dk3S_P2374_mV1rSvuvjZJIQjtzseXoyQiiVol7Qpr4GRyZ5DI1ZCO2NQ",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/DarkModePrefCredential/1-0-0.json",
        "history": [
            "Migrated from ceramic public tile on 2023-09-13T17:33:58.133Z"
        ]
    }
]
```
