---
description: This page contains all relevant endpoints interacting with Disco Personas.
---

# Personas

### Get Profile by DID&#x20;

{% swagger expanded="true" method="get" path="  " baseUrl="https://api.disco.xyz/v1/profile/{DID}" summary="Given a valid DID, return Disco profile data." %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="DID" required="true" %}
A decentralized identifier. This can be fetched from the URL of the Disco profile. It usually contains `did:3` to start. An example: `did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful Operation!" %}
**Example Response**

```json
{
  "profile": [
    {
      "profile": {
        "bio": "Me in the metaverse. Me in IRL!",
        "name": "the-web3-yogi",
        "avatar": "https://pbs.twimg.com/profile_images/1503385343730540544/dWdiICQX_400x400.jpg",
        "ethAddress": "0xe6ff2d91f6eeee8bda4bcc562d63c431496fcf2a"
      },
      "linksPending": {
        "discord": {
          "handle": "ericc572#8044",
          "signedVcString": "{\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"type\":[\"VerifiableCredential\",\"AccountLinkageCredential\"],\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96\"},\"issuanceDate\":\"2022-06-06T05:10:21.601Z\",\"id\":\"did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96#9fd90dea-1d44-41a5-9e18-29a3500fbf5f\",\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96\",\"type\":\"Discord\",\"username\":\"ericc572#8044\"},\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/AccountLinkageCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"proof\":{\"verificationMethod\":\"did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96#controller\",\"created\":\"2022-06-06T05:10:21.611Z\",\"proofPurpose\":\"assertionMethod\",\"type\":\"EthereumEip712Signature2021\",\"proofValue\":\"0xfe70a99157971f9c6ea3ad035f024f47fa58d77190e76a9fadca21c2db75c76a4e23900cd2834462cabcc515a97076b95fc965ef5522f449f36a24c3a3e1f4e21b\",\"eip712Domain\":{\"domain\":{\"chainId\":1,\"name\":\"Sign to link this account to your identifier\",\"version\":\"1\"},\"messageSchema\":{\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"username\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}]},\"primaryType\":\"VerifiableCredential\"}}}"
        },
        "twitter": {
          "handle": "the-web3-yogi",
          "signedVcString": "{\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"type\":[\"VerifiableCredential\",\"AccountLinkageCredential\"],\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96\"},\"issuanceDate\":\"2022-06-28T17:30:50.890Z\",\"id\":\"did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96#ca4a4d45-d75f-4f8d-a6cd-3cac99c7e9fb\",\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96\",\"type\":\"Twitter\",\"username\":\"the-web3-yogi\"},\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/AccountLinkageCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"proof\":{\"verificationMethod\":\"did:3:kjzl6cwe1jw149mq5riadts0nk6glwype5j2cnib0qobc9hju3ufqtmwi75lk96#controller\",\"created\":\"2022-06-28T17:30:50.896Z\",\"proofPurpose\":\"assertionMethod\",\"type\":\"EthereumEip712Signature2021\",\"proofValue\":\"0x40dd7ba73009aa5978f1064688280d6d181de1ed19cbbf7f41a395bfd68fe2dc5de4c90f91bd6a35714b2e2c14bc2c5afeb501664cf143daef036adbaf0553ac1c\",\"eip712Domain\":{\"domain\":{\"chainId\":1,\"name\":\"Sign to link this account to your identifier\",\"version\":\"1\"},\"messageSchema\":{\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"username\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}]},\"primaryType\":\"VerifiableCredential\"}}}"
        }
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

### Get Profile by Ethereum address

{% swagger method="get" path="/address/{eth_address}" baseUrl="https://api.disco.xyz/v1/profile" summary="Get Profile via Ethereum address" expanded="true" %}
{% swagger-description %}
Returns a Disco profile if it exists given its linked ETH Address. This only works if you've created a data backpack at http://app.disco.xyz and linked your ETH address!
{% endswagger-description %}

{% swagger-parameter in="path" name="address" required="true" %}
&#x20;Ethereum address, like `0xABC1234567890`
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful Operation" %}
```json
{
    "profile": {
        "ethAddress": "0xc5e46e48f1ef5f305afba45c3122021dd09ed3de",
        "avatar": "https://media.giphy.com/media/MF1kR4YmC2Z20/giphy.gif",
        "bio": "assistant to the regional manager (crayon department))))",
        "name": "carlf#3326"
    },
    "creds": [
        {
            "id": "did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#0ec2b522-b9f0-475e-87c2-29faa2716c5f",
            "type": [
                "VerifiableCredential",
                "OfficialDisconautCredential"
            ],
            "genId": "e09b5cd0-aecc-4ca3-80b9-9241f18c1b8a",
            "proof": {
                "type": "EthereumEip712Signature2021",
                "created": "2022-12-01T20:16:47.198Z",
                "proofValue": "0x41523d06b15476fbe015770cdc5f481b25afdcf98c653765771093f10ad693455dc3760980dfe0a3cb433ef1579c45558c38626024ec217eb03d57f7a320a9ea1c",
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
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "isPublic": true,
            "recipient": "did:3:kjzl6cwe1jw147em2rs0sekomnapwb1s4rym9mnib0trdwzr2njq0vgak9ugwxo",
            "issuanceDate": "2022-12-01T20:16:47.197Z",
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OfficialDisconautCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            },
            "credentialSubject": {
                "id": "did:3:kjzl6cwe1jw147em2rs0sekomnapwb1s4rym9mnib0trdwzr2njq0vgak9ugwxo",
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
