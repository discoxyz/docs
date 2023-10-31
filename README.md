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

You will need the following to start using our API:

1. Create a data backpack at [app.disco.xyz](https://app.disco.xyz/)&#x20;
2. Go to  '`Edit Profile`'&#x20;
3. Generate API Key&#x20;

## Schemas&#x20;

Schemas defines the structure and contents of a credential. Enabling the verifiable credentials to be consistent, verifiable, and interoperable. More details in [Schemas 101](for-builders/disco-apis/schemas-101.md)

[Github repository](https://github.com/discoxyz/disco-schemas/tree/main/json) of schemas.

{% hint style="info" %}
Always use Schemas raw files, [example](https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/AccountLinkageCredential/1-0-0.json).&#x20;
{% endhint %}

## Start using Disco's API

Use Disco’s API to build and sign or fetch credentials. This method constructs credentials signed by Disco-controlled keys. To issue credentials via API with keys you control, see [DID:WEB. ](#user-content-fn-1)[^1]

### Credential Subject&#x20;

Generate and issue credentials to an ETH address or Decentralized Identifier (DID).

{% swagger src=".gitbook/assets/swagger.json" path="/v1/credential" method="post" expanded="true" %}
[swagger.json](.gitbook/assets/swagger.json)
{% endswagger %}

#### Usage example

{% tabs %}
{% tab title="Curl" %}
```bash
curl --location 'https://api.disco.xyz/v1/credential' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--header 'Authorization: Bearer <your Disco API key>' \
--data '{
    "issuer": "did:3:123abcexample",
    "schemaUrl": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
    "recipientDID": "did:3:456defexample",
    "subjectData": {
        "memberId": "123XYZ",
        "membershipDescription": "Demo membership to showcase Disco API",
        "membershipLevel": "Permanent",
        "membershipType": "Developer",
        "organization": "Disco.xyz"
    },
    "expirationDate": ""
}'
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Accept", "*/*");
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var raw = JSON.stringify({
  "issuer": "did:3:123abcexample",
  "schemaUrl": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
  "recipientDID": "did:3:456defexample",
  "subjectData": {
    "memberId": "123XYZ",
    "membershipDescription": "Demo membership to showcase Disco API",
    "membershipLevel": "Permanent",
    "membershipType": "Developer",
    "organization": "Disco.xyz"
  },
  "expirationDate": ""
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/credential", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}
{% endtabs %}

#### Successful Response&#x20;

<details>

<summary>Response</summary>

```javascript
{
    "vc": {
        "@context": [
            "https://www.w3.org/2018/credentials/v1"
        ],
        "type": [
            "VerifiableCredential",
            "MembershipCredential"
        ],
        "issuer": {
            "id": "did:3:123abcexample"
        },
        "issuanceDate": "2023-10-10T12:53:15.718Z",
        "id": "https://api.disco.xyz/credential/5c7cca5e-56ab-4e08-87f6-817e9f89f507",
        "credentialSubject": {
            "id": "did:3:456defexample",
            "memberId": "123XYZ",
            "membershipDescription": "Demo membership to showcase Disco API",
            "membershipLevel": "Permanent",
            "membershipType": "Developer",
            "organization": "Disco.xyz"
        },
        "credentialSchema": {
            "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
            "type": "JsonSchemaValidator2018"
        },
        "proof": {
            "verificationMethod": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#controller",
            "created": "2023-10-10T12:53:15.745Z",
            "proofPurpose": "assertionMethod",
            "type": "EthereumEip712Signature2021",
            "proofValue": "0x487aa8ad7c90aa34a108b52cd7e23c5ef6cf9cfbdc01d7741d70d6b8f79763dc65df429e558af4c2d7a54c7f4040cf874ecffa95f17d87d8dc07823b23324bfe1b",
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
    "isPublic": false,
    "issuer": "did:3:123abcexample",
    "recipient": "did:3:456defexample",
    "subject": "did:3:456defexample",
    "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
    "isDeleted": false,
    "genId": "a4282add-ed1f-429d-a80d-abdd675b2eef",
    "updatedAt": "2023-10-10T12:53:15.748Z",
    "history": [],
    "_id": "6525493bb8ffec6244182e03"
}
```

</details>

### Fetch Credentials

Fetch a public credential based on its `ID`&#x20;

{% swagger src=".gitbook/assets/swagger.json" path="/v1/credential/{id}" method="get" expanded="true" %}
[swagger.json](.gitbook/assets/swagger.json)
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

## Community and Support&#x20;

Join our [Discord](https://discord.com/invite/dPPrZp2efJ)! You can also contact us at ask@disco.xyz.&#x20;







&#x20;



[^1]: add link
