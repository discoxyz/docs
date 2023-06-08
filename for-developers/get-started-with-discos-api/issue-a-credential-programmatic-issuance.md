---
description: May 5, 2023
---

# Issue a Credential (Programmatic Issuance)

**Welcome to pilot beta of our Programmatic Issuance for Partners, we are so excited to deliver this feature for you all.**&#x20;

**Thank you for your continued patience!**



**You will need:**

* A valid API key (please reach out to Masha/Eric for one)
* any HTTP library, curl, or Postman
* the schema URL to issue
* fields and descriptions for your schemas to issue.

### Find your Schema URL

Determine your schema you'd like to issue by visiting our schemas [repo](https://github.com/discoxyz/disco-schemas/tree/main/json) (If you'd like a custom schema not here already, please reach out to us).

Find the schema, and find the raw json. Example [here](https://github.com/discoxyz/disco-schemas/blob/main/json/GMCredential/1-0-0.json) of a GM credential.

Save this link, you'll need to reference this later.



### Authentication

Remember that we use Bearer Auth. This should be in the Auth header as follows:

```
Authorization: Bearer <your-token-here>
```

### Creating your Request

{% swagger method="post" path="" baseUrl="https://api.disco.xyz/v1/credential" summary=" Generate and return a signed credential programmatically. " %}
{% swagger-description %}
Given a request body with a schema url and fields, generate and return a signed credential. This will also write to the recipient's data backpack
{% endswagger-description %}

{% swagger-parameter in="body" name="schemaUrl" required="true" type="String" %}
Schema URL of which schema you'd like to create. 
{% endswagger-parameter %}

{% swagger-parameter in="body" name="recipientDID" type="String" required="true" %}
DID of which recipient you'd like to receive the credential. Supports did:ethr:<eth_address> for now.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="subjectData " type="JSON" %}
data about the subject, specific to each credential. May include things like Organization Name, etc.
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Response Successful. Returns the signed credential, in JSON and writes to the recipient's inbox." %}
**Example Response**

```json
{
    "@context": [
        "https://www.w3.org/2018/credentials/v1"
    ],
    "type": [
        "VerifiableCredential",
        "GmCredential"
    ],
    "issuer": {
        "id": "did:3:kjzl6cwe1jw145l0eotzxw28znn1zcis2khwa1rf56ss5a8e55ffhqht25fmk66"
    },
    "issuanceDate": "2023-05-08T15:54:56.431Z",
    "id": "did:3:kjzl6cwe1jw145l0eotzxw28znn1zcis2khwa1rf56ss5a8e55ffhqht25fmk66#fe0b5bab-a850-40ac-a5bc-46d779feda41",
    "credentialSubject": {
        "id": "did:3:kjzl6cwe1jw147pkworv5ff70zkwjne15b4ww4xwyof4cdgvgsw8xl1srg287wj"
    },
    "credentialSchema": {
        "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
        "type": "JsonSchemaValidator2018"
    },
    "proof": {
        "verificationMethod": "did:3:kjzl6cwe1jw145l0eotzxw28znn1zcis2khwa1rf56ss5a8e55ffhqht25fmk66#controller",
        "created": "2023-05-08T15:54:56.538Z",
        "proofPurpose": "assertionMethod",
        "type": "EthereumEip712Signature2021",
        "proofValue": "0x8808c6ed2f471e2d8bfbde026ce787e39b638959e9174b88d8a14d9742fe3840079345cea7c120c71f3b50689806f9c4ab25d5bbc2722018f35ba9d22b913a551c",
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
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="Internal Server Error, Missing fields or bad schema input" %}
**Example Response**

```json
{
    "name": "Error",
    "message": "Failed to fetch JSON Schema from htt://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json: Only HTTP(S) protocols are supported",
    "status": 500,
    "errors": [],
    "stack": "Error: Failed to fetch JSON Schema from htt://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json: Only HTTP(S) protocols are supported\n    at /Users/echen/eric-dev/disco-backend/node_modules/disco-schemas/src/validateVc.ts:78:11\n    at step (/Users/echen/eric-dev/disco-backend/node_modules/disco-schemas/dist/validateVc.js:44:23)\n    at Object.throw (/Users/echen/eric-dev/disco-backend/node_modules/disco-schemas/dist/validateVc.js:25:53)\n    at rejected (/Users/echen/eric-dev/disco-backend/node_modules/disco-schemas/dist/validateVc.js:17:65)"
}
```
{% endswagger-response %}
{% endswagger %}



Here are some example code snippets:

<details>

<summary><strong>Example cURL request</strong></summary>

```sh
curl --location 'http://api.disco.xyz/v1/credential/' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <redacted>' \
--data '{ 
   
    "schemaUrl": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
    "subjectData":{},
    "recipientDID":"did:3:kjzl6cwe1jw147pkworv5ff70zkwjne15b4ww4xwyof4cdgvgsw8xl1srg287wj"
}'
```

</details>

<details>

<summary>Example Javascript (node using fetch) request</summary>

````javascript

var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Authorization", "Bearer <redacted>");

var raw = JSON.stringify({
  "schemaUrl": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
  "subjectData": {},
  "recipientDID": "did:3:kjzl6cwe1jw147pkworv5ff70zkwjne15b4ww4xwyof4cdgvgsw8xl1srg287wj"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("http://api.disco.xyz/v1/credential/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
````

</details>

<details>

<summary>Example Response</summary>

```json

{
    "@context": [
        "https://www.w3.org/2018/credentials/v1"
    ],
    "type": [
        "VerifiableCredential",
        "GmCredential"
    ],
    "issuer": {
        "id": "did:3:kjzl6cwe1jw145l0eotzxw28znn1zcis2khwa1rf56ss5a8e55ffhqht25fmk66"
    },
    "issuanceDate": "2023-05-08T15:54:56.431Z",
    "id": "did:3:kjzl6cwe1jw145l0eotzxw28znn1zcis2khwa1rf56ss5a8e55ffhqht25fmk66#fe0b5bab-a850-40ac-a5bc-46d779feda41",
    "credentialSubject": {
        "id": "did:3:kjzl6cwe1jw147pkworv5ff70zkwjne15b4ww4xwyof4cdgvgsw8xl1srg287wj"
    },
    "credentialSchema": {
        "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
        "type": "JsonSchemaValidator2018"
    },
    "proof": {
        "verificationMethod": "did:3:kjzl6cwe1jw145l0eotzxw28znn1zcis2khwa1rf56ss5a8e55ffhqht25fmk66#controller",
        "created": "2023-05-08T15:54:56.538Z",
        "proofPurpose": "assertionMethod",
        "type": "EthereumEip712Signature2021",
        "proofValue": "0x8808c6ed2f471e2d8bfbde026ce787e39b638959e9174b88d8a14d9742fe3840079345cea7c120c71f3b50689806f9c4ab25d5bbc2722018f35ba9d22b913a551c",
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
}
```

</details>

```json
```
