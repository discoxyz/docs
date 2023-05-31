---
description: Here are some frequently asked questions.
layout: landing
---

# ❓ FAQs

## Identity  <a href="#what-are-decentralized-identifiers-dids" id="what-are-decentralized-identifiers-dids"></a>

### What are **Decentralized Identifiers (DIDs)**?[​](broken-reference) <a href="#what-are-decentralized-identifiers-dids" id="what-are-decentralized-identifiers-dids"></a>

* Decentralized Identifiers (DIDs) - These are like aliases for our existing addresses (Ethereum address, email address, website, Bitcoin address, etc.) that make it easy to prove ownership and control over other identifiers.
* DID Method - There a number of different ways to create DIDs (over 100 in fact!) but because different types of identifiers (like Ethereum addresses or Bitcoin addresses) work slightly differently and are rooted in different system we need a set of rules about how to create and interact with DIDs made out of the different identifiers. A DID Method is simply those rules!
* DID Document (DDO) - DIDs need DID Documents. A DID Document is a file that lists the current state of the DID as well as other public keys and endpoints for how to interact with that DID. The DID Document is where the magic of DIDs really happens!
* DID Communication Protocol (DIDComm) - This is a protocol that allows two DIDs to open a secure channel between them and send messages back and forth.

### What are **Verifiable credentials (VCs)**?[​](broken-reference) <a href="#what-are-verifiable-credentials-vcs" id="what-are-verifiable-credentials-vcs"></a>

* Verifiable credentials are specially formatted data that you can put on your Disco profile. Think of them like a digital version of your membership cards, IDs, library cards, or any other important document that you get from some other authority.
* Signed: In most cases, A verifiable credential is cryptographically signed by one DID about another DID and because the credential is signed it means nobody can tamper with the credential.
* Also Known As: Verifiable Credentials are the official name of the technical standard for this type of data but you might hear them referred to as Attestations, Claims, or even Badges.
* Encrypted: A VC can be encrypted using the subject’s DID so that only the subject and the issuer know what is in the credential.

### Where does Disco store my credentials?[​](broken-reference) <a href="#where-does-disco-store-my-credentials" id="where-does-disco-store-my-credentials"></a>

* Credentials need to be stored somewhere! Because putting personal information on a blockchain ranges from suboptimal to dangerous (for a number of reasons), the credential needs to be stored somewhere else. Disco currently uses the Ceramic [network](https://developers.ceramic.network/learn/) for storage but will be integrating many different storage solutions over time.

### Are my Disco credentials portable?[​](broken-reference) <a href="#are-my-disco-credentials-portable" id="are-my-disco-credentials-portable"></a>

* Your data is yours! It’s the whole point of Disco. If you have a Verifiable Credential on your Disco profile, you can take your Verifiable Credentials along with you to unlock access in other apps and spaces. Because your VC is signed, encrypted and tamper-evident, you can safely for move it across storage solutions and environments without damaging its integrity.

### Are my Disco credentials private?[​](broken-reference) <a href="#are-my-disco-credentials-private" id="are-my-disco-credentials-private"></a>

* Disco is here to enhance your privacy. By default, a credential that you receive is encrypted so that only you can see it. You can decrypt this credential and add it to your Disco profile so that the whole world can see it but then if you change your mind, you can re-encrypt the credential so that it is no longer on your profile. Just remember, once you make a credential public anyone can copy the data to an archive, that’s just the nature of the internet.

### What is a Verifiable Credential Subject?[​](broken-reference) <a href="#what-is-a-verifiable-credential-subject" id="what-is-a-verifiable-credential-subject"></a>

* Sometimes referred to as the “Credential Holder”. The subject is the person or entity that a Verifiable Credential is written about. For instance, you are the _subject_ of your Passport and your home country is the _issuer._

### What is a Relying Party?[​](broken-reference) <a href="#what-is-a-relying-party" id="what-is-a-relying-party"></a>

* A Relying Party is an individual or organization who _relies_ upon data presented in a Verifiable Credential to inform app logic, unlock access to certain privileges, or other form of access enabled by data verification.

### What is a Verifiable Credential schema?[​](broken-reference) <a href="#what-is-a-verifiable-credential-schema" id="what-is-a-verifiable-credential-schema"></a>

* A schema is a template for a Verifiable Credential. For example, driver’s licenses, passports, or diplomas all contain similar data organized in similar ways. This allows relying parties to interpret them easily no matter who the issuer. Schemas allow us to do the same thing for Verifiable Credentials.



## Using Disco

### How can I issue credentials using Disco?[​](broken-reference) <a href="#how-can-i-issue-credentials-using-disco" id="how-can-i-issue-credentials-using-disco"></a>

* Connect your wallet to [Disco.xyz](http://disco.xyz/), navigate to another user’s profile and click “Issue Credential”. From there you can select a credential type, fill in the necessary information, sign and send!

### How can I issue a large amount of credentials? <a href="#how-can-i-issue-a-large-amount-of-credentials-programmatically" id="how-can-i-issue-a-large-amount-of-credentials-programmatically"></a>

* Use [Batch Issuance for Organizations.](../for-organizations/issuing-credentials.md) Reach out to us if you have more than 10,000 credentials you'd like to issue.

### How do I create credentials about myself? <a href="#can-i-write-verifiable-credentials-about-myself" id="can-i-write-verifiable-credentials-about-myself"></a>

* You can create self-attested credentials by going to your profile, then clicking `Issue Self-Attested Credential.`

### What types of credentials can I issue?[​](broken-reference) <a href="#what-types-of-credentials-can-i-issue" id="what-types-of-credentials-can-i-issue"></a>

* Credential schemas that you can issue can be found under the schemas tab. If you'd like more schemas, please reach out to us!

### What type of accounts can I link?[​](broken-reference) <a href="#what-type-of-accounts-can-i-link" id="what-type-of-accounts-can-i-link"></a>

* Right now we offer the ability to link: Twitter handle, Discord handle, and domain name. However, we will be expanding this list soon!

### How do I make a credential public? <a href="#does-disco-only-work-for-ethereum" id="does-disco-only-work-for-ethereum"></a>

* You can toggle your credential public/private by going to your inbox, clicking the eye icon, then make public. Reminder that by doing so, the API will surface this credential to other apps!

### Does Disco only work for Ethereum?[​](broken-reference) <a href="#does-disco-only-work-for-ethereum" id="does-disco-only-work-for-ethereum"></a>

* Disco is EVM compatible. This means if you are on any EVM-compatible chain, you can sign in with Metamask to create a DID, and you'll be able to play!

### Can I partner with Disco?[​](broken-reference) <a href="#can-i-partner-with-disco" id="can-i-partner-with-disco"></a>

* Of course! We are always eager to onboard and work with new projects! Get in touch [here!](mailto:ask@disco.xyz)
