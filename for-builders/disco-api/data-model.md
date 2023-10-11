---
description: A deep dive into the data components in Disco Data Backpacks
---

# Data Model

## User&#x20;

A `User` on the Disco platform is the holder and owner of its own identity. A `User` can be an individual or an organization. `User` have an Ethereum Address that used with their wallet for access to their Credentials.  `Users` may, or may not, have a `www` domain and/or Ethereum Name Service (ENS) linked to their identity.&#x20;

A `Persona` is a set of attributes that describes a `User` in a particular context. Currently Disco supports one `Persona` per `User` (extendable to N `Personas` per `User` in future releases).  A `Persona` may have multiple DIDs and account `Linkages` assigned.&#x20;

<picture><source srcset="broken-reference" media="(prefers-color-scheme: dark)"><img src="broken-reference" alt=""></picture>

An example of a `User` document:

```json
{
    "id": "de0eae21-b88f-4f22-ad92-7ed99f7ea05c",
    // Unique user ID assigned by Disco
    "user": {
        "id": "ae541371-590b-4dba-b783-5cde41cc0d3c"
    },
    // The User's DID(s) - most users will have a did:3 or a did:pkr ID, whereas
    // organiozations may have a did:web ID
    "dids": [
        {
            "did": "did:web:api.disco.xyz/v1/disco"
        }
    ],
    // Disco user handle
    "handle": "Disco",
    // Link to user's avatar
    "avatarUri": "https://pbs.twimg.com/profile_images/1544599788464766976/Ib49kkdh_400x400.jpg",
    // User bio
    "bio": "Disco's ecosystem is build around our Verifiable Data Registry.",
    // The User's DID and accossiated Ethereum Address
    "ethAddress": "0x08936438bfb8e9b269f978d5327ad687f47g8c08",
    // External account links that the user has linked to one their Disco DIDs 
    "links": [
        {
            "accountType": "Discord",
            // Linked account handle
            "handle": "Disco#1234",
            // Verified by Disco
            "verified": true,
            // The user DID the linked to the account
            "did": "did:web:api.disco.xyz/v1/disco",
            "proof": "https://discord.com/channels/947857036257935390/975763597529600041/1078306074618236980"
        },
        {
            "accountType": "Twitter",
            "handle": "DiscoXYZ",
            "verified": true,
            "did": "did:web:api.disco.xyz/v1/disco",
            "proof": "https://twitter.com/DiscoXYZ/status/1667219955002032136"
        }
    ]
}
```

## Verifiable Credentials

A `Verifiable Credential` (aka  `Credential`) is a set of one or more (tamper-evident) claims made by someone or something. `Credentials` includes an identifier and properties such as `issuer`, `type`, `subject`, `issuance date`.  The credential claim is assigned a `proof` in that it's cryptographically signed by the `issuer` (who may or may not be the owner of the signing key).

<figure><picture><source srcset="broken-reference" media="(prefers-color-scheme: dark)"><img src="broken-reference" alt=""></picture><figcaption><p>Verifiable Credential Overview</p></figcaption></figure>

An example of a `Verifiable Credential` document:

```json
{
  "vc": {
    "@context": [
      "https://www.w3.org/2018/credentials/v1"
    ],
    // The Credential type(s) which declare what data (schema) to expect 
    // in the Credential. The second item in the array is waht's interesting
    // to most. The first item (VerifiableCredential) is more of a formality.
    "type": [
      "VerifiableCredential",
      "MembershipCredential"
    ],
    // Who (or what) that issued the credential. Note this could be the DID for an 
    // individual or an organization.
    "issuer": {
      "id": "did:web:api.disco.xyz/v1/disco"
    },
    // When the credential was issued.
    "issuanceDate": "2023-09-29T18:28:00.853Z",
    // The unique identifier for the Credential.
    "id": "https://api.disco.xyz/credential/de5eb800-a023-483b-88a2-39a062fec13e",
    // Detailed claims about the subject of the Credential. These details varies based 
    // on the credential type (i.e., credential schema, see below). 
    "credentialSubject": {
      // Identifier for the subject of the credential (in many use cases this is the 
      // same as the recipient identifier).
      "id": "did:web:api.disco.xyz/v1/jane",
      // Assertions about the subject of the credential
      "memberId": "123XYZ",
      "membershipDescription": "Demo membership to showcase Disco API",
      "membershipLevel": "Permanent",
      "membershipType": "Developer",
      "organization": "Disco.xyz"
    },
    // The credential schema that represents the credential type.
    "credentialSchema": {
      "id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
      "type": "JsonSchemaValidator2018"
    },
    // Digital proof that makes the credential tamper-evident. Disco uses 
    // EIP-712 or JWT.
    "proof": {
      // The identifier of the public key that can verify the signature.
      "verificationMethod": "did:web:api.disco.xyz/v1/disco#controller",
      "created": "2023-09-29T18:28:00.870Z",
      "proofPurpose": "assertionMethod",
      // Signed with EIP-712. Also support JWT.
      "type": "EthereumEip712Signature2021",
      "proofValue": "0xa0c0552a9d58b030e4f8a .... 621ee0f671a85e3bc1f7970c53a1b",
      "eip712Domain": {
        "domain": {
          "chainId": 1,
          "name": "Disco Verifiable Credential",
          "version": "1"
        },
        "messageSchema": {...},
        "primaryType": "VerifiableCredential"
      }
    }
  },
  // If isPublic is false the credential is only accessible to the issuer 
  // and recipient.
  "isPublic": true,
  // The DID for whom or what issued the credential.
  "issuer": "did:web:api.disco.xyz/v1/disco",
  // The DID for whom or what recieved the credential.
  "recipient": "did:web:api.disco.xyz/v1/jane",
  // The DID for the subject of the credential (most cases the same as the recipient).
  "subject": "did:web:api.disco.xyz/v1/jane",
  // Disco supported schemas can be found at https://github.com/discoxyz/disco-schemas
  "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
  "genId": "440994e8-fa9a-494c-83cd-2732f8c0cdba",
  "updatedAt": "2023-09-29T18:28:00.877Z"
}
```
