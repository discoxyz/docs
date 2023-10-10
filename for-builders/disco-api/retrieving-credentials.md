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

## Get a single Credential based on Credential ID.&#x20;

{% swagger src="../../.gitbook/assets/swagger (1).json" path="/v1/credential/{id}" method="get" expanded="true" %}
[swagger (1).json](<../../.gitbook/assets/swagger (1).json>)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
```bash
# Looking up id=https://api.disco.xyz/credential/22d9187b-8a33-4e17-b05f-c8192107ab28
curl --location 'https://api.disco.xyz/v1/credential/https%3A%2F%2Fapi.disco.xyz%2Fcredential%2F22d9187b-8a33-4e17-b05f-c8192107ab28' \
--header 'Authorization: Bearer <your Disco API key>'
```
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

{% swagger src="../../.gitbook/assets/swagger (1).json" path="/v1/credentials/{did}" method="get" expanded="true" %}
[swagger (1).json](<../../.gitbook/assets/swagger (1).json>)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
```bash
curl --location 'https://api.disco.xyz/v1/credentials/did:3:kjzl6cwe1jw145lzc8sbpnziei0t76kthtp4ep5xhlewakg385sno7ndm5qjsd2?page=1&size=2000' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer <your Disco API key>'
```
{% endtab %}
{% endtabs %}

Credential returned on successful call:

```json
```

### Get a multiple Credentials for multiple DIDs&#x20;

{% swagger src="../../.gitbook/assets/swagger (1).json" path="/v1/credentials/multi" method="post" expanded="true" %}
[swagger (1).json](<../../.gitbook/assets/swagger (1).json>)
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

{% swagger src="../../.gitbook/assets/swagger (1).json" path="/v1/credentials/search" method="post" expanded="true" %}
[swagger (1).json](<../../.gitbook/assets/swagger (1).json>)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
```bash
curl --location 'https://api.disco.xyz/v1/credentials/search?field=issuer&op=%3D&value=did%3A3%3Akjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6&page=1&size=10' \
--header 'Authorization: Bearer <your Disco API key>'
```
{% endtab %}
{% endtabs %}

Credential returned on successful call:

```json
```

### Get a multiple Credentials for multiple DIDs&#x20;







