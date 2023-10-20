---
description: How to get and use your very own did:web ID for your organization!
---

# did:web for Organizations

Before signing up for a `did:web` ID, make sure to complete the [getting-started.md](../getting-started.md "mention") section for your Organization.

## Signing up for did:web

1. Generate an API Key for your organization (see [generate-an-api-key.md](../../for-builders/generate-an-api-key.md "mention"))
2. Email a request for `did:web` with your desired org alias to masha@disco.xyz and walter@disco.xyz.&#x20;
3. A Disco admin will set up your `did:web`
4. You'll receive an email with your very own `did:web`  ID and a secret finiman link with an API Key for your new `did:web` ID.&#x20;

Your Disco `did:web` ID will have the following format: `did:web:api.disco.xyz/v1/{your-org-alias}` and will resolve at `https://api.disco.xyz/v1/{your-org-alias}/.well-known/did.json`.   For example:&#x20;

```json
{
    "@context": [
        "https://www.w3.org/ns/did/v1",
        "https://w3id.org/security/v2",
        "https://w3id.org/security/suites/secp256k1recovery-2020/v2"
    ],
    "id": "did:web:api.disco.xyz/v1/{your-org-alias}",
    "verificationMethod": [
        {
            "id": "did:web:api.disco.xyz/v1/{your-org-alias}#8f12a117-459a-4945-a93e-b1b5229a82f7",
            "type": "EcdsaSecp256k1VerificationKey2019",
            "controller": "did:web:api.disco.xyz/v1/{your-org-alias}",
            "publicKeyHex": "0417ae31be71e2c3d102df7f64b7b59d8a08d7b18d4236e0af4888f8b8e7ec0a9c66abf4b364d43f85bff81169c5a0e834ef00cc946f220e59c1e2370d76578cdf"
        }
    ],
    "authentication": [
        "did:web:api.disco.xyz/v1/{your-org-alias}#8f12a117-459a-4945-a93e-b1b5229a82f7"
    ],
    "assertionMethod": [
        "did:web:api.disco.xyz/v1/{your-org-alias}#8f12a117-459a-4945-a93e-b1b5229a82f7"
    ],
    "keyAgreement": [],
    "service": []
}
```
