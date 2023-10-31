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

# Quick Start Guide

## Introduction

The Disco API enables developers to issue verifiable credentials to addresses, and to fetch and validate credentials about those addresses. These credentials use standard data models (_schemas),_ contain event metadata or attestations, and can be later fetched and relied upon to bootstrap onboarding, manage access control, and understand community insights. &#x20;

## Prerequisites

Create an API Key&#x20;

1. Create a data backpack at [app.disco.xyz](https://app.disco.xyz/)&#x20;
2. Go to  '`Edit Profile`'&#x20;
3. Generate API Key&#x20;

\[include a video]&#x20;

## Schemas&#x20;

[Github repository](https://github.com/discoxyz/disco-schemas/tree/main/json) of schemas.

[Schemas 101](../for-builders/disco-apis/schemas-101.md)

\[outline the purpose of schemas]

## Start using Disco's API

Use [Disco’s API ](https://docs.disco.xyz/disco-docs/for-builders/disco-apis)to build and sign or fetch credentials. This method constructs credentials signed by Disco-controlled keys. To issue credentials via API with keys you control, see [DID:WEB. ](#user-content-fn-1)[^1]

### Credential Subjects&#x20;

Issue credentials to an ETH address or Decentralized Identifier (DID).

### Fetch Credentials

Fetch a public credential based on its `ID`&#x20;

{% swagger src="../.gitbook/assets/swagger.json" path="/v1/credential/{id}" method="get" expanded="true" %}
[swagger.json](../.gitbook/assets/swagger.json)
{% endswagger %}

#### Usage example&#x20;

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

#### Successful response&#x20;

<details>

<summary>Response </summary>

```javascript
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



</details>



## Sign credentials with your keys

## Community and Support&#x20;

Join our [Discord](https://discord.com/invite/dPPrZp2efJ)! You can also contact us at ask@disco.xyz.&#x20;

{% embed url="https://discord.com/invite/dPPrZp2efJ" %}







&#x20;



[^1]: add link
