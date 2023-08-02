---
description: This page shows you how to verify a credential using the Disco API
---

# Verify a Credential

### Verify a Credential

{% hint style="success" %}
**Why verify a credential?**\
\
We can verify a credential to check that the statement is valid, the attestation + signature has not been tampered with, it is still valid, and has not been revoked.
{% endhint %}

The following is a Disco-hosted API endpoint for you to verify your credential.

If you'd like to use a library to self-verify a credential in your app without relying on Disco as a central authority, [here](https://gist.github.com/aldigjo/41a20d8fced39d4c47e7ac088f0c35c0) is a snippet. \
\
Reminder that JWT (JSON Web Tokens) can be decoded using something like [https://jwt.io/](https://jwt.io/).



**API Endpoint**&#x20;

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

Pass the JSON body while making the request:

{% code title="BoysClub MembershipCredential.json" overflow="wrap" lineNumbers="true" %}
```json
{
  "vc": "{\"id\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t#eaf7052b-4da3-4a20-accb-370cd3841ef8\",\"type\":[\"VerifiableCredential\",\"MembershipCredential\"],\"genId\":\"d35d51c2-cbc8-40bb-8644-b65d97c23c15\",\"proof\":{\"type\":\"EthereumEip712Signature2021\",\"created\":\"2022-10-21T19:08:38.053Z\",\"proofValue\":\"0x4291116c532f56dec309c849351f1ab41685b67064e84a71e54a95b6c10bdb1333659ae48000a0afd75557af9d64bbc0cb4637c686889e840efaf4de2dc88b081b\",\"eip712Domain\":{\"domain\":{\"name\":\"\",\"chainId\":1,\"version\":\"1\"},\"primaryType\":\"VerifiableCredential\",\"messageSchema\":{\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"organization\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}]}},\"proofPurpose\":\"assertionMethod\",\"verificationMethod\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t#controller\"},\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t\"},\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"isPublic\":true,\"recipient\":\"did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb\",\"issuanceDate\":\"2022-10-21T19:08:37.287Z\",\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb\",\"organization\":\"BoysClub\"}}"
}
```
{% endcode %}

</details>

**cURL Example**

```javascript
vc.json

{
  "vc": "{\"id\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t#eaf7052b-4da3-4a20-accb-370cd3841ef8\",\"type\":[\"VerifiableCredential\",\"MembershipCredential\"],\"genId\":\"d35d51c2-cbc8-40bb-8644-b65d97c23c15\",\"proof\":{\"type\":\"EthereumEip712Signature2021\",\"created\":\"2022-10-21T19:08:38.053Z\",\"proofValue\":\"0x4291116c532f56dec309c849351f1ab41685b67064e84a71e54a95b6c10bdb1333659ae48000a0afd75557af9d64bbc0cb4637c686889e840efaf4de2dc88b081b\",\"eip712Domain\":{\"domain\":{\"name\":\"\",\"chainId\":1,\"version\":\"1\"},\"primaryType\":\"VerifiableCredential\",\"messageSchema\":{\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"organization\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}]}},\"proofPurpose\":\"assertionMethod\",\"verificationMethod\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t#controller\"},\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t\"},\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"isPublic\":true,\"recipient\":\"did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb\",\"issuanceDate\":\"2022-10-21T19:08:37.287Z\",\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb\",\"organization\":\"BoysClub\"}}"
}
```

```sh
curl --location 'https://api.disco.xyz/v1/credential/verify' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer <token_Here>' \
--data-raw vc.json
```

**Javascript Example**

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Authorization", "Bearer <token_Here>");

var raw = JSON.stringify({
  "vc": "{\"id\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t#eaf7052b-4da3-4a20-accb-370cd3841ef8\",\"type\":[\"VerifiableCredential\",\"MembershipCredential\"],\"genId\":\"d35d51c2-cbc8-40bb-8644-b65d97c23c15\",\"proof\":{\"type\":\"EthereumEip712Signature2021\",\"created\":\"2022-10-21T19:08:38.053Z\",\"proofValue\":\"0x4291116c532f56dec309c849351f1ab41685b67064e84a71e54a95b6c10bdb1333659ae48000a0afd75557af9d64bbc0cb4637c686889e840efaf4de2dc88b081b\",\"eip712Domain\":{\"domain\":{\"name\":\"\",\"chainId\":1,\"version\":\"1\"},\"primaryType\":\"VerifiableCredential\",\"messageSchema\":{\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"organization\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}]}},\"proofPurpose\":\"assertionMethod\",\"verificationMethod\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t#controller\"},\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw145ltolsez9qm7q65uw60n3cx001p7gs1x2q7rcaft9f3eybi48t\"},\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"isPublic\":true,\"recipient\":\"did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb\",\"issuanceDate\":\"2022-10-21T19:08:37.287Z\",\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw14b7xqq94oiy0lcnndgyt0p3vtlnsscpljosx6gom46qkxcv8sjb\",\"organization\":\"BoysClub\"}}"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.disco.xyz/v1/credential/verify", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```
