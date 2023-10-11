# Verify Credentials

### Summary

Once we have these Verifiable Credentials in our backpack, we can verify them with another app to use them appropriately. This evaluation will check for: the validity of the statement, the conformity of the credential to its specification, and the proof.

Due to the decentralized nature of these credentials, they can be verified by anyone, anywhere.&#x20;

{% hint style="info" %}
Verification can be done using our [API endpoint](../../for-builders/disco-api/verify-a-credential.md), or manually like in this [code snippet](https://gist.github.com/aldigjo/41a20d8fced39d4c47e7ac088f0c35c0) without relying on Disco as the central authority.
{% endhint %}

Here are some examples of integrations with Disco where we verify the VC, which unlocks a subsequent flow.&#x20;
