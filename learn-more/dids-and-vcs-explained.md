---
description: A deeper dive into decentralized identifiers and verifiable credentials.
---

# DIDs and VCs explained

### Decentralized Identifiers (DIDs)[​](https://docs.disco.xyz/learn/dids-and-vcs#decentralized-identifiers-dids) <a href="#decentralized-identifiers-dids" id="decentralized-identifiers-dids"></a>

Decentralized Identifiers (DIDs) are unique identifiers that serve as an alias for existing cryptographic identifiers such as Ethereum, Bitcoin, or PGP Keys.

* DIDs make it easy to prove ownership and control over other identifiers and data.
* They are self-generated and self-owned.
* DIDs act as a safeguard for our digital presence through cryptography.
* Each address in a DID is unique, just like a keychain that holds many keys we need to access gated doors.
* DIDs provide a non-centralized, universally discoverable way for individuals to own their credentials.
* The DID subject can be any organization, person, or object.
* Although the DID is simply an identifier, it allows you to resolve to a DID document, which is a descriptive data blob containing a mapping of public keys and optional service endpoints for the DID subject.

Decentralized Identifiers (DIDs) are universal and resolvable nametags that represent individuals, organizations, or objects in a non-centralized manner. Each DID is a unique identifier that resolves to a DID document, containing a mapping of public keys and optional service endpoints. The public keys enable cryptographic proofs of identity and control, while the service endpoints can be used to discover and interact with services offered by the DID subject.

### Anatomy[​](https://docs.disco.xyz/learn/dids-and-vcs#anatomy) <a href="#anatomy" id="anatomy"></a>

A DID typically consists of three parts:

* Scheme: usually "did".
* DID method: specifies the operations for creating, resolving, and updating DIDs and their associated DID documents.
* Method-specific identifier: allows for lookup using the specific DID method.

<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

DIDs provide a persistent identifier that can be used to interact with various online systems.

DIDs become highly effective when combined with Verifiable Credentials, acting as digital certificates for IDs, diplomas, and more. This enables the verification of an entity's identity, empowering them to control their data while preserving its integrity.

Let's consider an example. If Disco issued me a membership credential, my DID would be the subject, and the credential would be issued from the organization's DID.

To verify that Disco owns the DID, we can examine the DID document or link it to their owned accounts such as Twitter ([@disco](https://twitter.com/discoxyz)) and relevant domain ([disco.xyz](https://www.disco.xyz/)).

## Verifiable Credentials (VC)[​](https://docs.disco.xyz/learn/dids-and-vcs#verifiable-credentials-vc) <a href="#verifiable-credentials-vc" id="verifiable-credentials-vc"></a>

Ok, time to dive into Verifiable Credentials.

**A Verifiable Credential:**

* Is a signed attestation or statement made by one party about itself or another.
* Takes the form of specially formatted data (JSON), which conforms to the technical specifications established by the World Wide Web Consortium (W3C).
* Is revocable or can be set to expire. Think of them as a digital version of your membership cards, IDs, library cards, or any other important document that you get from some other authority.
* **Is signed.** In most cases, a Verifiable Credential is cryptographically signed by one DID about another DID, and because the credential is signed, it means nobody can tamper with it.
* Provide evidence or a statement of verification regarding the recipient or user, such as Bob's membership in DAOHaus or Boys Club, or Bob's diploma from Waterloo University or completion of a specific course.
* Is an open-sourced standard by the W3C Verifiable Credentials Data Model, which is a set of specifications and verifiable documentation that allow credentials to be verified and shared on the web.

According to the [W3C](https://www.w3.org/TR/vc-data-model/), “Verifiable Credentials represent statements made by an issuer in a tamper-evident and privacy-respecting manner.”

What does this mean? Let’s think about the physical credentials we use in our daily lives. An ID card or car insurance card is a physically issued credential…that represents my association, membership, or identification with the government or another entity.&#x20;

![](<../.gitbook/assets/image (11).png>)

Why/how is this trustworthy? In most cases, we implicitly trust the source who issued it.

{% hint style="info" %}
**Verifiable Credentials** are a new digital mechanism allowing proofs or claims using public-key cryptography. Essentially, these credentials are blobs of data that are digitally signed/watermarked by a private key. The “public key” is essentially a public address everyone knows and is controlled by a private key.
{% endhint %}

### Anatomy[​](https://docs.disco.xyz/learn/dids-and-vcs#anatomy-1) <a href="#anatomy-1" id="anatomy-1"></a>

Time to dissect. Three components make up a Verifiable Credential: Metadata, Claims, and Proofs.

#### **Metadata**

Metadata is data about data. Think of this as credential properties such as the issuer, expiration, image, public key, etc. It’s usually formatted as JSON key-values:

```
{ 
  key: "value", 
  expiration: "January 2, 2024"
}
```

**Claims**

Claims are statements that pertain to a specific subject, such as:

"Bob attended Harvard," "Janice was born on December 20th, 1999," or "Jamie is a member of DAOHaus." \
\
These statements provide information about the subject and can be used to verify their identity or status.

**Proofs**

A proof is a set of data that includes an encoded digital signature and additional context, as well as the identifier of the public key. \
\
This identifier helps identify the entity or individual that issued the credential. Here is an example:

```
  "proof": {
    // the cryptographic signature suite that was used to generate the signature
    "type": "RsaSignature2018",
    // the date the signature was created
    "created": "2017-06-18T21:19:10Z",
    // purpose of this proof
    "proofPurpose": "assertionMethod",
    // the identifier of the public key that can verify the signature
    "verificationMethod": "https://example.edu/issuers/565049#key-1",
    // the digital signature value
    "jws": "eyJhbGciOiJSUzI1NiIsImI2NCI6ZmFsc2UsImNyaXQiOlsiYjY0Il19..TCYt5X
      sITJX1CxPCT8yAV-TVkIEq_PbChOMqsLfRoPsnsgw5WEuts01mq-pQy7UJiN5mgRxD-WUc
      X16dUEMGlv50aqzpqh4Qktb3rk-BuQy72IFLOqV0G_zS245-kronKb78cPN25DGlcTwLtj
      PAYuNzVBAh4vGHSrQyHUdBBPM"
```

When we talk about "verifying a credential," we are referring to the process of verifying the proof associated with the credential and ensuring that its contents have not been altered in any way. The verification process employs the RSA Signature Encryption method, which is recommended by the W3C standard. If you want to learn more about RSA and Digital Signatures, you can click [here](https://www.geeksforgeeks.org/rsa-and-digital-signatures/).

## Why choose VCs? <a href="#why" id="why"></a>

* Verifiable Credentials are private, only visible to you if you choose. You have your DID as your identifier, and no other personal info is public.
* The ID Holder can choose what attributes of their identity they want to disclose. For example, they could show their birth year without disclosing the day and month they were born. This is known as Selective Disclosure and will be in our upcoming [Roadmap](broken-reference).
* The ID Holder is always in control of the relationship with ID Verifiers. They know what data was shared and when (there’s an audit trail)
* They are tamper-evident through the use of cryptographic signatures
* They are portable. Verifiable Credentials are yours to store in your wallet and can be shared with parties you trust.

{% hint style="info" %}
There **is** a difference between **verification** and **validation** when it comes to VCs.

To **verify** a Verifiable Credential, a comprehensive evaluation is necessary to determine the authenticity and the statement in question. This includes checking: the credential conforms to a set of specifications (data model), the cryptographic method/signature is satisfied and optionally, and a status check.

To **validate** a Verifiable Credential, it is sufficient to determine whether it meets the needs of a verifier for relevant fields (issuer DID, timestamp, etc) for the specific credential in question.
{% endhint %}

### How do they work together?[​](https://docs.disco.xyz/learn/dids-and-vcs#how-do-they-work-together) <a href="#how-do-they-work-together" id="how-do-they-work-together"></a>

Recall that we identify users with DID’s. In a verifiable credential, you’ll have a subject and issuer, and we use the DID’s to identify them!

### How do they work together?[​](https://docs.disco.xyz/learn/dids-and-vcs#how-do-they-work-together) <a href="#how-do-they-work-together" id="how-do-they-work-together"></a>

Recall that we identify users with DID’s. In a verifiable credential, you’ll have a subject and issuer, and we use the DID’s to identify them!

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

## Additional Learning[​](https://docs.disco.xyz/learn/dids-and-vcs#additional-learning) <a href="#additional-learning" id="additional-learning"></a>

Still want to read up more on VC’s and DID’s? We got you.&#x20;

* [Blog Post: More on DIDs](https://mirror.xyz/0xaf115b18eE30734f6CeA1C56BE76615df046e010/UqHHismf1ookU2JMMkX2DPBA5PiTVF7-4vQkshTukEg)
* [DIDs, VCs, and Disco High Level](https://docs.disco.xyz/#identity-legos-)
* W3C Technical Specifications:
  * [Decentralized Identifiers](https://www.w3.org/TR/did-core/)
  * [Verifiable Credentials Data Model](https://www.w3.org/TR/vc-data-model/)
* [Understanding VCs](https://hackernoon.com/understanding-the-verifiable-credentials-vcs-it1535e9)
* [Hackernoon: Decentralized Identifiers (DIDs)](https://hackernoon.com/decentralized-identifiers-dids-a-deeper-dive-04383442?ref=hackernoon.com)
* [Digital Identity by Mattr](https://learn.mattr.global/docs/concepts/digital-identity)
* [Video: Human Centered Identity by Johnny Howle](https://www.youtube.com/watch?v=x-6o8PzXYU4)
* [Video: The Off-Chain Internet (ETHDenver)](https://www.youtube.com/watch?v=EZ\_Bb6j87mg)
