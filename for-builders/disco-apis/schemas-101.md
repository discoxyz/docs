---
description: The basics of working with existing Credential schemas.
---

# Schemas 101

## Introduction

For Verifiable Credentials schemas there are generally two types usages; 1) data verification and 2) data encoding. Data Verification is of interest here. Schemas per W3C Verifiable Credential spec includes a vast amount of metadata. With that in mind we will be focusing on pieces relevant to most developers - `credentialSubject`.

Disco manages all  schemas in a [github repo](https://github.com/discoxyz/disco-schemas). Developers can use any of these schemas in their development.  Working with the myriad of available schemas can be overwhelming at first, so let's take a look at an example first - [MembershipCredential](https://github.com/discoxyz/disco-schemas/blob/main/json/MembershipCredential/latest.json).&#x20;

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

As mentioned above, much of this is boilerplate per [W3C specification](https://www.w3.org/TR/vc-data-model/#basic-concepts), what is unique to [MembershipCredential](https://github.com/discoxyz/disco-schemas/blob/main/json/MembershipCredential/latest.json) (and any other schemas for that matter) is in the `credentialSubject` object. Note that the last object, named `required` in the `credentialSubject` list the fields which _must_ be provided for this particular schema.

{% code overflow="wrap" lineNumbers="true" %}
```json
{ 
  ...
    "credentialSubject": { // The Verifiable Credential payload object. This is where all fields pertaining to the specific credential type resides. 
      "properties": { 
        "expiration": { // Standard to the W3C VC protocol - an optional expiration date for the Credential.
          "format": "date",
          "title": "Expiration",
          "type": "string"
        },
        "id": ... , // Standard to the W3C VC protocol - a unique credential identifier assigned by the system. As a developer you do NOT include this in API calls for creating your Credential.
        "memberId": { // Optional and unique to this particular schema - use whatever membership ID you want to refer to - or may be left out if not used.
          "title": "Member ID",
          "type": "string"
        },
        "membershipDescription": { // Optional and unique to this particular schema - describe what the membership is for to the recipient and verifiers - or may be left out if not used.
          "title": "Membership Description",
          "type": "string"
        },
        "membershipLevel": { // Optional and unique to this particular schema - if your membership is hierarchical you can use this to indicate the level - or may be left out if not used.
          "title": "Membership Level",
          "type": "string"
        },
        "membershipType": { // Optional and unique to this particular schema - can be used to describe the membership type issued- or may be left out if not used.
          "title": "Membership Type",
          "type": "string"
        },
        "organization": { // Required and unique to this particular schema - the name of the organization for which this membership is issued for.
          "title": "Organization Name",
          "type": "string"
        }
      },
      "required": [ // Required fields Unique to this particular schema
        "id", // ALWAYS system generated
        "organization" // Provided by you, the developer
      ],
      "type": "object"
    }, 
  ... 
  }
```
{% endcode %}

Let's take a look at how to use this particular schema in programmatic issuance of a single Credential.

{% code overflow="wrap" lineNumbers="true" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Accept", "*/*");
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var raw = JSON.stringify({
  // The issueing DID - the owner of the API Key used in "Authorization"
  "issuer": "did:3:123abcexample",
  // Link to schema in Disco's repository hosted on Github 
  "schemaUrl": "https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json",
  // The recipient DID to issue the Credential to
  "recipientDID": "did:3:456defexample",
  // The Credential payload unique to this particular schema - SEE ABOVE
  "subjectData": {
    "memberId": "123XYZ", // Optional
    "membershipDescription": "Demo membership to showcase Disco API", // Optional
    "membershipLevel": "Permanent", // Optional
    "membershipType": "Developer", // Optional
    "organization": "Disco.xyz" // Required 
  },
  // Expiration date of Credential, if any
  "expirationDate": "" // Field is required, BUT can be left empty to indicate no expiration
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

// Fire-and-forget
fetch("https://api.disco.xyz/v1/credential", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
{% endcode %}

