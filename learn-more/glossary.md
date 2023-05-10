# 📔 Glossary

The identity domain has a lot of complex terms and definitions, so here is a non-exhaustive list of key terms, acronyms, and phrases to help aid your learning journey. Keep in mind this is Disco's interpretation!

## Identity

### SSI (Self-Sovereign Identity)

* Self-sovereign identities (SSI) are digital identities that are managed by users themselves. This technology allows users to self-manage their digital identities without depending on third-party providers to store and centrally manage the data.

### Identifier

* An identifier is a string of numbers and/or letters that can be used to refer to a person, account, object, profile etc.
* An identifier is a name that you can use to refer to a party — Evin, 0x12348593383, User1, @provenauthority on twitter, etc.
* An identifier does not have any signing keys, it is just the name/username

### Identity

An identity is 3 things together:

1. a name (an identifier)
2. a list of things that identifier has done (metadata)
3. the ability to exercise control over both
   * _**example**_: evin’s twitter identity
     * name: @provenauthority (twitter username)
     * metadata: all evin’s tweets & likes
     * control: evin can confirm tweets from this account and grant access to its control
   * _**example**_: evin’s email identity
     * name: evin@disco.xyz
     * metadata: all of evin’s contacts, calendar invites, emails
     * control: evin can send emails from this account and grant access to its control \*\*\*\*

### Decentralized Identifier or DID

* A decentralized identifier uses a standard method of enabling a public identifier (e.g. ETH address, SOL address, email address) and retrofitting it to send and receive private data from other public identifiers. It's like an alias for our existing addresses. For more, see [here](https://docs.disco.xyz/learn/dids-and-vcs).

### Verifiable Credentials

Verifiable credentials are signed attestations, written by one party about another party or itself.

VCs are:

* **Signed**
  * Statement that is signed by the person who said/wrote it
* **Attestations**
  * Statement written by one party about another party or itself that _attesting_ to a piece of information, for example a diploma is an attestation by a university that a Evin graduated from Hawken School
  * An attestation from another party means that someone _else_ made a statement about you
  * A **self-attestation** means that you’ve written a signed attestation about yourself
* **Encrypted**
  * Verifiable credentials are encrypted, meaning their content is encoded in a series of numbers and letters, like translating a private note into a secret code.
  * If anyone tries to change the verifiable credential, the secret code will be broken no human-readable message can be derived or resolved anymore
* **Private by default**
  * VCs are issued/sent to the subject they are written about, and so the receiver has the ability to choose how publicly to share that piece of data.
* **Can be generated manually**
  * An issuer can decide to create a verifiable credential and issue it to someone else by clicking buttons and typing into the[ Disco.xyz](http://disco.xyz) web app
* **Can be generated programmatically**
  * A verifiable credential can be automatically generated and issued to a subject based on pre-determined requirements in an app
  * For example, an app might issue a “successful purchase!” credential to all users who make a purchase within the app
  * this proof would attest that a particular user has made a purchase within the app before, and can be used as future reference to prove their status as a customer in the future
* **Timestamped**
  * A verifiable credential can be defined so that it carries a time stamp of when it was generated
* **Can be set to expire**
  * A verifiable credential can be issued with an expiration date, so that the credential will no longer be valid after a certain date
  * You can hang onto an expired credential, like you can hang onto expired milk, but you can’t expect that everyone will treat it the same as they did when it was valid
* **Revocable**
  * Verifiable credentials can be revoked, meaning that the issuer can keep a list of all of the credentials they’ve issued and then later revoked
    * Often, that list (called a revocation registry) is stored on the blockchain
    * This means that anyone verifying a credential from that issuer needs to do three things to validate the credential:
      1. Check the cryptography/resolve the credential to learn what it says and to ensure that no one has tried to tamper with the data it contains
      2. Check to see whether the credential had an expiration date, and if so, whether it’s expired
      3. Check the revocation registry, to see whether that particular credential has been revoked

### Issuer

* An issuer is a party that writes a verifiable credential, and attests to the statement contained within it
* The issuer also signs the credentials they create, and send them to their subject/intended recipient
* Issuers can be individual people, or organizations
* Anybody can be an issuer of any kind of credential
* Individual users and apps need to decide how much they trust an individual issuer to make a statement about that particular topic — the trustworthiness of the issuer’s opinion on the content

### Verifier

A verifier is a party who wants to check out a verifiable credential to determine:

* Who said the attestation?
* What did they attest?
* When did it happen?
* Has the attestation been tampered with?
* Has the attestation expired or is it still valid?
* Has the attestation been revoked or is it still valid (this one is kind of tricky)?

A verifier is sometimes called a relying party because they are relying upon the contents of the credential to execute some logic or make a decision for example, does this user have the right credential to enter the website or party or secure room? Anyone can verify a credential, so anyone can be a verifier

### DID Methods

A DID method is a specification which specifies the operations by which DIDs and DID documents are created, resolved, updated, and deactivated.

Examples: `did:ethr`, `did:3`. Disco uses 3id which you can learn more about [here](https://developers.ceramic.network/docs/advanced/standards/accounts/3id-did/).

### DID Document

Recall that each DID resolves to a DID document. This is like a key-value lookup. This document serves to describe additional information like public keys, protocols, and endpoints about the cryptography of this entity. It is usually a valid JSON-LD object. Here's an example:

```
{
  "@context": [
    "https://www.w3.org/ns/did/v1",
    "https://w3id.org/security/suites/ed25519-2020/v1"
  ]
  "id": "did:example:123456789abcdefghi",
  "authentication": [{
    
    "id": "did:example:123456789abcdefghi#keys-1",
    "type": "Ed25519VerificationKey2020",
    "controller": "did:example:123456789abcdefghi",
    "publicKeyMultibase": "zH3C2AVvLMv6gmMNam3uVAjZpfkcJCwDwnZn6z3wXmqPV"
  }]
}
```

## Data

### JSON (Javascript Object Notation)

JavaScript Object Notation, aka the acronym JSON, is an open data format that is both human and machine-readable. JSON is independent of any programming language and is commonly represented as key value pairs, defined within left and right opening braces(“{}”). Here’s an example:

### JSON-LD

A sub-specific format of JSON is JSON-LD, which stands for Linked Data format. Created for an easy way for humans to read and write data interoperably. It uses hyperlinks and certain data keys to represent references. An example of this is:

```{
  "@context": {
    "name": "http://xmlns.com/foaf/0.1/name",
    "homepage": {
      "@id": "http://xmlns.com/foaf/0.1/workplaceHomepage",
      "@type": "@id"
    },
    "Person": "http://xmlns.com/foaf/0.1/Person"
  },
  "@id": "https://me.example.com",
  "@type": "Person",
```

### Schema

A schema is a data template that helps organize and interpret information. We use various VC schemas to define a type of credential that contains a set of fields and certain metadata to be included. Each schema may serve one or many different use cases, like Membership, Attendance, and GM! Here’s an example in our schemas repository.

### Selective Disclosure

Selective disclosure is one of the key pillars of SSI and is the ability for individuals to share minimal data to a recipient or verifier and take actions based on it.

Here’s an example: Vince walks into a bar and the bouncer would like to request proof that Vince is over 21 to gain entry. However, Vince wants to prove that he is over 21 years old, but doesn’t want to disclose any other information such as his name or address. How can he do that? With selective disclosure, Vince is able to generate a Verifiable Presentation which aggregates data from a claim and answers the question, “Is this person 21 or over?” Without having to share any other details!

### Wallet

Crypto wallets store your private keys, keeping your crypto safe and accessible. They also allow you to send, receive, and spend cryptocurrencies like Bitcoin and Ethereum. See more here: https://docs.disco.xyz/learn/what-is-a-wallet
