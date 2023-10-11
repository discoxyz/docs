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

The following is a API endpoint for you to verify your credential.

If you'd like to use a library to self-verify a credential in your app without relying on Disco as a central authority, [here](https://gist.github.com/aldigjo/41a20d8fced39d4c47e7ac088f0c35c0) is a snippet. \
\
Reminder that JWT (JSON Web Tokens) can be decoded using something like [https://jwt.io/](https://jwt.io/).



**API Endpoint**&#x20;

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
--header 'Authorization: Bearer b499e2ff-92a9-49b3-b4f7-e7cf756b7b5d' \
--data-raw '{vc:"{\"@context\":[\"https://www.w3.org/2018/credentials/v1\"],\"type\":[\"VerifiableCredential\",\"MembershipCredential\"],\"issuer\":{\"id\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt\"},\"issuanceDate\":\"2023-09-19T13:12:14.801Z\",\"id\":\"https://api.disco.xyz/credential/22d9187b-8a33-4e17-b05f-c8192107ab28\",\"credentialSubject\":{\"id\":\"did:ethr:0x08936438bfb8e9b269f978d5327ad684f47f8c05\",\"organization\":\"House of Leroy\"},\"expirationDate\":\"2024-08-29T00:00:00.000Z\",\"credentialSchema\":{\"id\":\"https://raw.githubusercontent.com/discoxyz/disco-schemas/main/json/MembershipCredential/1-0-0.json\",\"type\":\"JsonSchemaValidator2018\"},\"proof\":{\"verificationMethod\":\"did:3:kjzl6cwe1jw14a7u9sx3thx9gg9uh7u5tqjkzcnr5pi5zzkap7kiztgsfhzayzt#controller\",\"created\":\"2023-09-19T13:12:14.827Z\",\"proofPurpose\":\"assertionMethod\",\"type\":\"EthereumEip712Signature2021\",\"proofValue\":\"0x3aa89255fe63d7ca70c43b0603aa3d004978bc0815b35ae5dcbf84a3df4867f133b6f0d717916cf84b8f6b3dcbf6a7643f18fa00557c0ddb5f5571cc8f678d291c\",\"eip712Domain\":{\"domain\":{\"chainId\":1,\"name\":\"Disco Verifiable Credential\",\"version\":\"1\"},\"messageSchema\":{\"EIP712Domain\":[{\"name\":\"name\",\"type\":\"string\"},{\"name\":\"version\",\"type\":\"string\"},{\"name\":\"chainId\",\"type\":\"uint256\"}],\"Proof\":[{\"name\":\"created\",\"type\":\"string\"},{\"name\":\"proofPurpose\",\"type\":\"string\"},{\"name\":\"type\",\"type\":\"string\"},{\"name\":\"verificationMethod\",\"type\":\"string\"}],\"Issuer\":[{\"name\":\"id\",\"type\":\"string\"}],\"CredentialSubject\":[{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"organization\",\"type\":\"string\"}],\"VerifiableCredential\":[{\"name\":\"@context\",\"type\":\"string[]\"},{\"name\":\"credentialSubject\",\"type\":\"CredentialSubject\"},{\"name\":\"id\",\"type\":\"string\"},{\"name\":\"issuanceDate\",\"type\":\"string\"},{\"name\":\"issuer\",\"type\":\"Issuer\"},{\"name\":\"proof\",\"type\":\"Proof\"},{\"name\":\"type\",\"type\":\"string[]\"}]},\"primaryType\":\"VerifiableCredential\"}}}"
}'
```
{% endcode %}
{% endtab %}
{% endtabs %}
