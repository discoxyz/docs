---
description: The basics of working with existing Credential schemas.
---

# Using Credentials

## Introduction

For Verifiable Credentials there are generally two types of data schemas used; 1) data verification schemas and 2) data encoding schemas. The former type is where we will focus as 99% of non-complex use cases do not require mappings to alternative representation formats (e.g., binary). Disco manages all your schemas in a [github repo](https://github.com/discoxyz/disco-schemas). Developers can use any of these schemas in their development. Also, the selection is constantly growing - if you have requests for new schemas reach out to us on [Discord](https://discord.com/channels/947857036257935390/1091134162590769253).&#x20;

Working with the myriad of available Credential schemas (i.e., Credential types) can be overwhelming at first, so let's take a look at an example first - [MembershipCredential](https://github.com/discoxyz/disco-schemas/blob/main/json/MembershipCredential/latest.json).&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```json
{
  "$id": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "description": "General Membership attests that the subject is a member in good standing of the issuing organization or group.",
  "properties": {
    "@context": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "type": "array"
        },
        {
          "type": "object"
        }
      ]
    },
    "credentialSchema": {
      "properties": {
        "id": {
          "format": "uri",
          "type": "string"
        },
        "type": {
          "type": "string"
        }
      },
      "required": [
        "id",
        "type"
      ],
      "type": "object"
    },
    "credentialSubject": {
      "properties": {
        "expiration": {
          "format": "date",
          "title": "Expiration",
          "type": "string"
        },
        "id": {
          "format": "uri",
          "title": "Member DID",
          "type": "string"
        },
        "memberId": {
          "title": "Member ID",
          "type": "string"
        },
        "membershipDescription": {
          "title": "Membership Description",
          "type": "string"
        },
        "membershipLevel": {
          "title": "Membership Level",
          "type": "string"
        },
        "membershipType": {
          "title": "Membership Type",
          "type": "string"
        },
        "organization": {
          "title": "Organization Name",
          "type": "string"
        }
      },
      "required": [
        "id",
        "organization"
      ],
      "type": "object"
    },
    "expirationDate": {
      "format": "date-time",
      "type": "string"
    },
    "id": {
      "format": "uri",
      "type": "string"
    },
    "issuanceDate": {
      "format": "date-time",
      "type": "string"
    },
    "issuer": {
      "anyOf": [
        {
          "format": "uri",
          "type": "string"
        },
        {
          "properties": {
            "id": {
              "format": "uri",
              "type": "string"
            }
          },
          "required": [
            "id"
          ],
          "type": "object"
        }
      ]
    },
    "type": {
      "anyOf": [
        {
          "type": "string"
        },
        {
          "items": {
            "type": "string"
          },
          "type": "array"
        }
      ]
    }
  },
  "required": [
    "@context",
    "type",
    "issuer",
    "issuanceDate",
    "credentialSubject"
  ],
  "title": "Membership Credential",
  "type": "object"
}
```
{% endcode %}

Much of this is boilerplate per [W3C specification](https://www.w3.org/TR/vc-data-model/#basic-concepts), so let's take a closer look at the fields unique to   [MembershipCredential](https://github.com/discoxyz/disco-schemas/blob/main/json/MembershipCredential/latest.json)  Credentials schema which are all in the `credentialSubject` object:

{% code overflow="wrap" lineNumbers="true" %}
```json
{ 
  ...
    "credentialSubject": { // The Verifiable Credential payload object. This is where all fields pertaining to the specific credential type resides. 
      "properties": { 
        "expiration": { // Standard to the VC Credential protocol - an optional expiration date for the Credential.
          "format": "date",
          "title": "Expiration",
          "type": "string"
        },
        "id": ... , // Standard to the VC Credential protocol - a unique credential identifier assigned by the system
        "memberId": { // Unique to this particular Credential schema
          "title": "Member ID",
          "type": "string"
        },
        "membershipDescription": { // Unique to this particular Credential schema
          "title": "Membership Description",
          "type": "string"
        },
        "membershipLevel": { // Unique to this particular Credential schema
          "title": "Membership Level",
          "type": "string"
        },
        "membershipType": { // Unique to this particular Credential schema
          "title": "Membership Type",
          "type": "string"
        },
        "organization": { // Unique to this particular Credential schema
          "title": "Organization Name",
          "type": "string"
        }
      },
      "required": [ // Required fields Unique to this particular Credential schema
        "id", 
        "organization"
      ],
      "type": "object"
    }, 
  ... 
  }
```
{% endcode %}

Let's take a look at how to use this particular schema in programmatic issuance of a single Credential and multiple Credentials.

**Single Credential Issuance**&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Accept", "*/*");
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var raw = JSON.stringify({
  // The issueing DID, for example your Org's DID
  "issuer": "did:3:123abcexample",
  // Link to schema in Disco's repository hosted on Github 
  "schemaUrl": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
  // The recipient DID you want to issue the Credential to
  "recipientDID": "did:3:456defexample",
  // The Credential payload unique to this particular schema
  "subjectData": {
    "memberId": "123XYZ", // Optional
    "membershipDescription": "Demo membership to showcase Disco API", // Optional
    "membershipLevel": "Permanent", // Optional
    "membershipType": "Developer", // Optional
    "organization": "Disco.xyz" // Required per schema spec
  },
  "expirationDate": "" // Required, but can be left empty for no expiration
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
{% endcode %}

**Multiple Credential Issuance**&#x20;

{% code overflow="wrap" lineNumbers="true" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Accept", "*/*");
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var raw = JSON.stringify({
  // The issueing DID, for example your Org's DID
  "issuer": "did:3:123abcexample",
  // Link to schema in Disco's repository hosted on Github 
  "schema": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
  // Encryption suite to use 712 or jwt are support - we encourage using jwt
  "suite": "jwt",
  // An array of recipients and their credential payloads unique to this particular schema
  "subjects": [
    {
      "subject": {
        "id": "did:3:789efexample",
        "memberId": "123XYZ", // Optional
        "membershipDescription": "Demo membership to showcase Disco API", // Optional
        "membershipLevel": "Permanent", // Optional
        "membershipType": "Developer", // Optional
        "organization": "Disco.xyz" // Required per schema spec
      },
      "recipient": "did:3:789efexample", // Required
      "expirationDate": "" // Required, but can be left empty for no expiration
    },
    {
      "subject": {
        "id": "did:3:1011hijexample",
        "memberId": "678XYZ", // Optional
        "membershipDescription": "Demo membership to showcase Disco API", // Optional
        "membershipLevel": "Permanent", // Optional
        "membershipType": "Developer", // Optional
        "organization": "Disco.xyz"
      },
      "recipient": "did:3:1011hijexample", // Required per schema spec
      "expirationDate": "" // Required, but can be left empty for no expiration
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
{% endcode %}

