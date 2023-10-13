---
description: Issuing Verifiable Credentials
---

# Issuing Credentials

## Process Flow for Issuance

<figure><img src="../../.gitbook/assets/Programatiacally issuance (1).png" alt="" width="476"><figcaption></figcaption></figure>

## Single Credential Issuance

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credential" method="post" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

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

### Successful Response

```json
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

## Batch Credential Issuance

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credentials" method="post" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
```bash
curl --location 'https://api.disco.xyz/v1/credentials' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--header 'Authorization: Bearer <your Disco API key>' \
--data '{
  "issuer": "did:3:123abcexample",
  "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
  "suite": "jwt",
  "subjects": [
    {
      "subject": {
        "id": "did:3:456defexample"
      },
      "recipient": "did:3:456defexample",
      "expirationDate": ""
    },
    {
      "subject": {
        "id": "did:3:789ghiexample"
      },
      "recipient": "789ghiexample",
      "expirationDate": ""
    }
  ]
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
  "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
  "suite": "jwt",
  "subjects": [
    {
      "subject": {
        "id": "did:3:456defexample"
      },
      "recipient": "did:3:456defexample",
      "expirationDate": ""
    },
    {
      "subject": {
        "id": "did:3:789ghiexample"
      },
      "recipient": "did:3:789ghiexample",
      "expirationDate": ""
    }
  ]
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/credentials", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endtab %}
{% endtabs %}

### Successful Response

```json
[
    {
        "vc": {
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "type": [
                "VerifiableCredential",
                "GmCredential"
            ],
            "issuer": {
                "id": "did:3:123abcexample"
            },
            "issuanceDate": "2023-10-10T14:11:38.056Z",
            "id": "https://api.disco.xyz/credential/9c65e3d4-4232-4129-9681-3004b94ceaa1",
            "credentialSubject": {
                "id": "did:3:456defexample"
            },
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            }
        },
        "isPublic": false,
        "issuer": "did:3:123abcexample",
        "recipient": "did:3:456defexample",
        "subject": "did:3:456defexample",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
        "isDeleted": false,
        "genId": "64ca2748-2f19-42c2-9108-b392b9861d8e",
        "updatedAt": "2023-10-10T14:11:38.056Z",
        "history": [],
        "jwt": "eyJhbGciOiJFUzI1NksiLCJ0eXAiOiJKV1QifQ.eyJ2Y ... 3kA7BMNbns6vA",
        "_id": "65255b9ab8ffec6244182e04"
    },
    {
        "vc": {
            "@context": [
                "https://www.w3.org/2018/credentials/v1"
            ],
            "type": [
                "VerifiableCredential",
                "GmCredential"
            ],
            "issuer": {
                "id": "did:3:123abcexample"
            },
            "issuanceDate": "2023-10-10T14:11:38.063Z",
            "id": "https://api.disco.xyz/credential/28facd33-f7cf-45f9-b1da-da9d08a45f20",
            "credentialSubject": {
                "id": "did:3:789ghiexample"
            },
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            }
        },
        "isPublic": false,
        "issuer": "did:3:123abcexample",
        "recipient": "did:3:789ghiexample",
        "subject": "did:3:789ghiexample",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
        "isDeleted": false,
        "genId": "84748837-7f5d-4b6c-9267-b75a3155c145",
        "updatedAt": "2023-10-10T14:11:38.063Z",
        "history": [],
        "jwt": "eyJhbGciOiJFUzI1NksiLCJ0eXAiOiJKV1 ... EVVcpKy4Hrrx-3_jcnzteLqFPIO7xA",
        "_id": "65255b9ab8ffec6244182e05"
    }
]
```
