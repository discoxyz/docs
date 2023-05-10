---
description: Sending and Receiving Credentials on Disco
---

# Verifiable Credentials

<figure><img src="../../.gitbook/assets/image (21).png" alt=""><figcaption></figcaption></figure>

## **Let's take a look at an example.**

Degen University is the [Issuer](verifiable-credentials.md#parties-involved) and issues a diploma in the form of a Verifiable Credential (VC) to Alex as the [Recipient](verifiable-credentials.md#parties-involved) for their graduation on a specific date. They use Disco to accept the credential and apply for a job. The employer, acting as a [Verifier](verifiable-credentials.md#parties-involved), who will verify the credential via Disco's API endpoints.

In this scenario, the inherent trust model comes into play in three ways:

1. Alex can prove who issued the credential, as Degen University's DID is unique to them.
2. Alex owns the credential and is the subject of the claim (i.e. their Degree in Arts).
3. The credential is valid, and the cryptography has not been tampered with.

## Parties Involved 🥂

**Issuer**

Whoever is issuing a claim, or credential. This could be any governing body, entity, university, or organization! They’ll sign the claim with their public and private key-pairs so it’s legit.

**Recipient**&#x20;

Whoever is receiving a claim, or credential. They will ultimately own these credentials and control how it’s shared. They’ll have a DID so it’ll be unique to that address only.

**Verifier**&#x20;

An entity that verifies if the credential is authentic and valid. Typically, they’ll ensure that it is legitimate, tamper-proof, and is still relevant on the requested date.

