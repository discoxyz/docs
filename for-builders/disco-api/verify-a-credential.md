---
description: How to verify a credential using the Disco API
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

# Verify a Credential

{% hint style="success" %}
**Why verify a credential?**\
\
We can verify a credential to check that the statement is valid, the attestation + signature has not been tampered with, it is still valid, and has not been revoked.
{% endhint %}

If you'd like to use a library to self-verify a credential in your app without relying on Disco as a central authority, [here](https://gist.github.com/aldigjo/41a20d8fced39d4c47e7ac088f0c35c0) is a snippet. \
\
Reminder that JWT (JSON Web Tokens) can be decoded using something like [https://jwt.io/](https://jwt.io/).

{% swagger src="../../.gitbook/assets/swagger.json" path="/v1/credential/verify" method="post" expanded="true" %}
[swagger.json](../../.gitbook/assets/swagger.json)
{% endswagger %}

### Usage example

{% tabs %}
{% tab title="Curl" %}
{% code overflow="wrap" %}
```bash
curl --location 'https://api.disco.xyz/v1/credential/verify' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--header 'Authorization: Bearer <your Disco API key>' \
--data-raw '{
    "vc": "{\"_id\":{\"$oid\":\"64f7952756aa629274bfbfce\"},\"vc\":{\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"id\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#b868f1fb-c6ab-402c-9710-bb5db331fcd3\",\"type\":[\"VerifiableCredential\",\"OrganizationCredential\"],\"proof\":{\"type\":\"EthereumEip712Signature2021\",\"created\":\"2022-11-16T17:14:29.713Z\",\"proofValue\":\"0x9e38337b93f6564db69b386a36cb7c22aa90c79facb48ba309f33e1d4030133d12ce5e3c035da34dfd8fa57ebec389db5f8331f4ccf3726433ef696d57642a241b\",\"eip712Domain\":{\"domain\":{\"name\":\"\",\"chainId\":1,\"version\":\"1\"},\"primaryType\":\"VerifiableCredential\",\"messageSchema\":{\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"organizationName\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}]}},\"proofPurpose\":\"assertionMethod\",\"verificationMethod\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#controller\"},\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt\"},\"issuanceDate\":\"2022-11-16T17:14:22.786Z\",\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OrganizationCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw14628704ob0iovstsmic2q9pu3xthi7t4yaywzrcvcrv3o41j06m\",\"organizationName\":\"Crumpet Capital\"}},\"genId\":\"77c8759b-ac29-4b25-8ac4-36ae0acf6a61\",\"isPublic\":true,\"isDeleted\":false,\"issuer\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt\",\"recipient\":\"did:3:kjzl6cwe1jw14628704ob0iovstsmic2q9pu3xthi7t4yaywzrcvcrv3o41j06m\",\"subject\":\"did:3:kjzl6cwe1jw14628704ob0iovstsmic2q9pu3xthi7t4yaywzrcvcrv3o41j06m\",\"updatedAt\":null,\"jwt\":\"\",\"schema\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OrganizationCredential/1-0-0.json\",\"history\":[\"Migrated from ceramic public tile on 2023-09-05T20:52:55.370Z\"]}"
}'
```
{% endcode %}
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");
myHeaders.append("Accept", "*/*");
myHeaders.append("Authorization", "Bearer <your Disco API key>");

var raw = JSON.stringify({
  "vc": "{\"_id\":{\"$oid\":\"64f7952756aa629274bfbfce\"},\"vc\":{\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"id\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#b868f1fb-c6ab-402c-9710-bb5db331fcd3\",\"type\":[\"VerifiableCredential\",\"OrganizationCredential\"],\"proof\":{\"type\":\"EthereumEip712Signature2021\",\"created\":\"2022-11-16T17:14:29.713Z\",\"proofValue\":\"0x9e38337b93f6564db69b386a36cb7c22aa90c79facb48ba309f33e1d4030133d12ce5e3c035da34dfd8fa57ebec389db5f8331f4ccf3726433ef696d57642a241b\",\"eip712Domain\":{\"domain\":{\"name\":\"\",\"chainId\":1,\"version\":\"1\"},\"primaryType\":\"VerifiableCredential\",\"messageSchema\":{\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"CredentialSchema\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"organizationName\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSchema\",\"type\":\"CredentialSchema\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}]}},\"proofPurpose\":\"assertionMethod\",\"verificationMethod\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#controller\"},\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt\"},\"issuanceDate\":\"2022-11-16T17:14:22.786Z\",\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OrganizationCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"credentialSubject\":{\"id\":\"did:3:kjzl6cwe1jw14628704ob0iovstsmic2q9pu3xthi7t4yaywzrcvcrv3o41j06m\",\"organizationName\":\"Crumpet Capital\"}},\"genId\":\"77c8759b-ac29-4b25-8ac4-36ae0acf6a61\",\"isPublic\":true,\"isDeleted\":false,\"issuer\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt\",\"recipient\":\"did:3:kjzl6cwe1jw14628704ob0iovstsmic2q9pu3xthi7t4yaywzrcvcrv3o41j06m\",\"subject\":\"did:3:kjzl6cwe1jw14628704ob0iovstsmic2q9pu3xthi7t4yaywzrcvcrv3o41j06m\",\"updatedAt\":null,\"jwt\":\"\",\"schema\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/OrganizationCredential/1-0-0.json\",\"history\":[\"Migrated from ceramic public tile on 2023-09-05T20:52:55.370Z\"]}"
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
{% endtab %}
{% endtabs %}

### Successful Response

```json
true
```
