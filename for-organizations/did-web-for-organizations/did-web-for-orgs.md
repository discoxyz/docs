---
description: >-
  With our partner account you are able to sign credentials with your own keys!
  It only requires you to set up an alias and to host your Decentralized
  Identifier (DID).
---

# did:web for Orgs

**To get started you will need:**

* Your organization's `did:web` ID
* Your `did:web` API key
* Any HTTP library, curl, or Postman
* The credential schema URL you want to issue credentials for

### Find your Schema URL

Determine which type of credential you'd like to issue. A full set of supported credential schemas can be found by visiting our [schema repository on github](https://github.com/discoxyz/disco-schemas/tree/main/json).

### Authentication

We use Bearer Authentication. This should be in the Authentication header as follows (using your API key):

```bash
Authorization: Bearer <your did:web API key here>
```

### Creating your Request

Here are some example code snippets for issuing a single GM credential to `did:3:abc123example` using `did:web`

<details>

<summary><strong>did:web example using curl</strong> </summary>

```sh
curl --location 'http://api.disco.xyz/v1/credentials/' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <your did:web api key>' \
--data '{ 
    "issuer": "did:web:api.disco.xyz/v1/<your-org-alias>",
    "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
    "suite": "jwt",
    "subjects": [
        {
            "subject": { "id": "did:3:abc123example" },
            "recipient": "did:3:abc123example",
            "expirationDate": ""
        }
    ]
}'
```

</details>

To send a batch of GM credentials add multiple recipients to the subjects array, as follows:

```json
{ 
    "issuer": "did:web:api.disco.xyz/v1/<your-org-alias>",
    "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
    "suite": "jwt",
    "subjects": [
        {
            "subject": { "id": "did:3:abc123example" },
            "recipient": "did:3:abc123example",
            "expirationDate": ""
        },
        {
            "subject": { "id": "did:3:xyz987example" },
            "recipient": "did:3:xyz987example",
            "expirationDate": ""
        }, 
        ....
    ]
}
```

<details>

<summary><strong>did:web</strong> example using Javascript</summary>

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Authorization", "Bearer <your did:web api key>");

var raw = JSON.stringify({ 
    "issuer": "did:web:api.disco.xyz/v1/<your-org-alias>",
    "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
    "suite": "jwt",
    "subjects": [
        {
            "subject": { "id": "did:3:abc123example" },
            "recipient": "did:3:abc123example",
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

fetch("http://api.disco.xyz/v1/credentials/", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

</details>

<details>

<summary>Example Response</summary>

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
                "id": "did:web:api.disco.xyz/v1/ididitorg"
            },
            "issuanceDate": "2023-09-22T16:16:56.442Z",
            "id": "https://api.disco.xyz/credential/bfbae1f1-a86f-4023-9844-549237a6734b",
            "credentialSubject": {
                "id": "did:3:abc123example"
            },
            "credentialSchema": {
                "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
                "type": "JsonSchemaValidator2018"
            }
        },
        "isPublic": false,
        "issuer": "did:web:api.disco.xyz/v1/ididitorg",
        "recipient": "did:3:abc123example",
        "subject": "did:3:abc123example",
        "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/GMCredential/1-0-0.json",
        "isDeleted": false,
        "genId": "d6bee666-e197-44d7-a932-3c3a4e215c64",
        "updatedAt": "2023-09-22T16:16:56.443Z",
        "history": [],
        "jwt": "xoHYP...............XCKE1hrA",
        "_id": "650dbdf822bed6b55eb5477f"
    }
]
```

</details>
