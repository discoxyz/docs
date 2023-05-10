---
description: Here are API endpoints interacting with Disco Credentials
---

# Credentials

### Get all credentials

{% swagger method="get" path="" baseUrl="https://api.disco.xyz/v1/profile/{did}/credentials" summary="Gets credentials by did." %}
{% swagger-description %}
Given a did, return all 

_**public**_

 credentials belonging to that user
{% endswagger-description %}

{% swagger-parameter in="path" name="did" required="true" %}
A decentralized identifier. This can be fetched from the URL of the Disco profile. It usually contains 

`did:3`

 to start. An example: 

`did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful Operation" %}
**Example Response**

```json
{
  "credentials": [
    {
      "id": "did:3:kjzl6cwe1jw14bfc93dsmejffll3j687kpq3te8ntmcjb98erxj9x8mdrdompf6#7cec6d96-d829-427b-bb3d-941637316b07",
      "type": [
        "VerifiableCredential",
        "OfficialDisconautCredential"
      ],
      "proof": {
        "type": "EthereumEip712Signature2021",
        "created": "2022-08-03T01:43:20.784Z",
        "proofValue": "0x758f9c664b838426ad74411ec454a19cfec70708da212be4e6639af65b5851e63bfff3c85790f60b5a808b2c30c35991dc970656d9c9a3a0910242167ebc25a31b",
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
        "verificationMethod": "did:3:kjzl6cwe1jw14bfc93dsmejffll3j687kpq3te8ntmcjb98erxj9x8mdrdompf6#controller"
      },
      "issuer": {
        "id": "did:3:kjzl6cwe1jw14bfc93dsmejffll3j687kpq3te8ntmcjb98erxj9x8mdrdompf6"
      },
      "@context": [
        "https://www.w3.org/2018/credentials/v1"
      ],
      "issuanceDate": "2022-08-03T01:43:20.784Z",
      "credentialSchema": {
        "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OfficialDisconautCredential/1-0-0.json",
        "type": "JsonSchemaValidator2018"
      },
      "credentialSubject": {
        "id": "did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96",
        "edition": 1
      }
    }
  ]
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized. Request not authenticated, API token is missing or invalid!" %}

{% endswagger-response %}

{% swagger-response status="403: Forbidden" description=" Forbidden. You don't have access to the relevant resource. " %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Resource not found" %}

{% endswagger-response %}
{% endswagger %}

### Get a credential type

{% swagger method="get" path="" baseUrl="http://api.disco.xyz/v1/profile/{did}/credentials/byTypes?types={type} " summary="Get credentials by DID and type" %}
{% swagger-description %}
Given a did and credential type, return all 

_**public**_

 credentials of that type belonging to that user.
{% endswagger-description %}

{% swagger-parameter in="path" name="did" required="true" %}
A decentralized identifier. This can be fetched from the URL of the Disco profile. It usually contains 

`did:3`

 to start. An example: 

`did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96`
{% endswagger-parameter %}

{% swagger-parameter in="path" name="type" type="String" required="true" %}
schema type to search for: e.g: 

`OfficialDisconautCredential, GMCredential.`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful Operation" %}
**Example Response**

```json
[
    {
        "id": "did:3:kjzl6cwe1jw14bfc93dsmejffll3j687kpq3te8ntmcjb98erxj9x8mdrdompf6#7c7c05e7-4a4c-4f7e-95b5-0e3950de426a",
        "type": [
            "VerifiableCredential",
            "OfficialDisconautCredential"
        ],
        "proof": {
            "type": "EthereumEip712Signature2021",
            "created": "2022-08-11T14:01:37.343Z",
            "proofValue": "0x3cbe53bdcf45af8402a5367aefe3ac3321df9ad23527f73f2207c643ef5a4c0f7fea5ed2d3713fe544bb622edabef277e0ffa89f0bd38e91d053eda96e0b3cf91b",
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
            "verificationMethod": "did:3:kjzl6cwe1jw14bfc93dsmejffll3j687kpq3te8ntmcjb98erxj9x8mdrdompf6#controller"
        },
        "issuer": {
            "id": "did:3:kjzl6cwe1jw14bfc93dsmejffll3j687kpq3te8ntmcjb98erxj9x8mdrdompf6",
            "name": "Discoxyz",
            "profilePicture": "https://pbs.twimg.com/profile_images/1544599788464766976/Ib49kkdh_400x400.jpg"
        },
        "@context": [
            "https://www.w3.org/2018/credentials/v1"
        ],
        "issuanceDate": "2022-08-11T14:01:37.343Z",
        "credentialSchema": {
            "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OfficialDisconautCredential/1-0-0.json",
            "type": "JsonSchemaValidator2018"
        },
        "credentialSubject": {
            "id": "did:3:kjzl6cwe1jw147kthg20siutrwer96rvuo57q9v3nab8n3dvllibjwekivh1wmy",
            "edition": 1
        }
    }
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

### Verify a Credential



{% swagger method="post" path="" baseUrl="https://api.disco.xyz/v1/credential/verify" summary="Verify a Credential" %}
{% swagger-description %}
Given a credential signed by a 3id in JSON format, verify its contents and signature. Returns true/false if valid.
{% endswagger-description %}

{% swagger-parameter in="body" name="vc" type="String" required="true" %}
Stringified VC, see example below

&#x20;


{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful Operation" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Unauthorized. Request not authenticated, API token is missing or invalid!" %}

{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="Forbidden. You don't have access to the relevant resource. " %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="Resource not found" %}

{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="InternalServerError: Bad or Missing VC" %}

{% endswagger-response %}
{% endswagger %}

<details>

<summary><em>Sample Request Body</em></summary>

{% code title="BoysClub MembershipCredential.json" overflow="wrap" lineNumbers="true" %}
```json
{
  "vc": "{\"id\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t#eaf7052b-4da3-4a20-accb-370cd3841ef8\",\"type\":[\"VerifiableCredential\",\"MembershipCredential\"],\"genId\":\"d35d51c2-cbc8-40bb-8644-b65d97c23c15\",\"proof\":{\"type\":\"EthereumEip712Signature2021\",\"created\":\"2022-10-21T19:08:38.053Z\",\"proofValue\":\"0x4291116c532f56dec309c849351f1ab41685b67064e84a71e54a95b6c10bdb1333659ae48000a0afd75557af9d64bbc0cb4637c686889e840efaf4de2dc88b081b\",\"eip712Domain\":{\"domain\":{\"name\":\"\",\"chainId\":1,\"version\":\"1\"},\"primaryType\":\"VerifiableCredential\",\"messageSchema\":{\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"organization\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}]}},\"proofPurpose\":\"assertionMethod\",\"verificationMethod\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t#controller\"},\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t\"},\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"isPublic\":true,\"recipient\":\"did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb\",\"issuanceDate\":\"2022-10-21T19:08:37.287Z\",\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb\",\"organization\":\"BoysClub\"}}"
}
```
{% endcode %}

</details>
