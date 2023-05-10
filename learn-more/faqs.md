---
description: Here are some frequently asked questions.
---

# ❓ FAQs

What are **Decentralized Identifiers (DIDs)**?[​](broken-reference)

* Decentralized Identifiers (DIDs) - These are like aliases for our existing addresses (Ethereum address, email address, website, Bitcoin address, etc.) that make it easy to prove ownership and control over other identifiers.
* DID Method - There a number of different ways to create DIDs (over 100 in fact!) but because different types of identifiers (like Ethereum addresses or Bitcoin addresses) work slightly differently and are rooted in different system we need a set of rules about how to create and interact with DIDs made out of the different identifiers. A DID Method is simply those rules!
* DID Document (DDO) - DIDs need DID Documents. A DID Document is a file that lists the current state of the DID as well as other public keys and endpoints for how to interact with that DID. The DID Document is where the magic of DIDs really happens!
* DID Communication Protocol (DIDComm) - This is a protocol that allows two DIDs to open a secure channel between them and send messages back and forth.

#### What are **Verifiable credentials (VCs)**?[​](broken-reference) <a href="#what-are-verifiable-credentials-vcs" id="what-are-verifiable-credentials-vcs"></a>

* Verifiable credentials are specially formatted data that you can put on your Disco profile. Think of them like a digital version of your membership cards, IDs, library cards, or any other important document that you get from some other authority.
* Signed: In most cases, A verifiable credential is cryptographically signed by one DID about another DID and because the credential is signed it means nobody can tamper with the credential.
* Also Known As: Verifiable Credentials are the official name of the technical standard for this type of data but you might hear them referred to as Attestations, Claims, or even Badges.
* Encrypted: A VC can be encrypted using the subject’s DID so that only the subject and the issuer know what is in the credential.

#### Where does Disco store my credentials?[​](broken-reference) <a href="#where-does-disco-store-my-credentials" id="where-does-disco-store-my-credentials"></a>

* Credentials need to be stored somewhere! Because putting personal information on a blockchain ranges from suboptimal to dangerous (for a number of reasons), the credential needs to be stored somewhere else. Disco currently uses the Ceramic [network](https://developers.ceramic.network/learn/) for storage but will be integrating many different storage solutions over time.

#### Are my Disco credentials portable?[​](broken-reference) <a href="#are-my-disco-credentials-portable" id="are-my-disco-credentials-portable"></a>

* Your data is yours! It’s the whole point of Disco. If you have a Verifiable Credential on your Disco profile, you can take your Verifiable Credentials along with you to unlock access in other apps and spaces. Because your VC is signed, encrypted and tamper-evident, you can safely for move it across storage solutions and environments without damaging its integrity.

#### Are my Disco credentials private?[​](broken-reference) <a href="#are-my-disco-credentials-private" id="are-my-disco-credentials-private"></a>

* Disco is here to enhance your privacy. By default, a credential that you receive is encrypted so that only you can see it. You can decrypt this credential and add it to your Disco profile so that the whole world can see it but then if you change your mind, you can re-encrypt the credential so that it is no longer on your profile. Just remember, once you make a credential public anyone can copy the data to an archive, that’s just the nature of the internet.

#### What is a Verifiable Credential Subject?[​](broken-reference) <a href="#what-is-a-verifiable-credential-subject" id="what-is-a-verifiable-credential-subject"></a>

* Sometimes referred to as the “Credential Holder”. The subject is the person or entity that a Verifiable Credential is written about. For instance, you are the _subject_ of your Passport and your home country is the _issuer._

#### What is a Relying Party?[​](broken-reference) <a href="#what-is-a-relying-party" id="what-is-a-relying-party"></a>

* A Relying Party is an individual or organization who _relies_ upon data presented in a Verifiable Credential to inform app logic, unlock access to certain privileges, or other form of access enabled by data verification.

#### What is a Verifiable Credential schema?[​](broken-reference) <a href="#what-is-a-verifiable-credential-schema" id="what-is-a-verifiable-credential-schema"></a>

* A schema is a template for a Verifiable Credential. For example, driver’s licenses, passports, or diplomas all contain similar data organized in similar ways. This allows relying parties to interpret them easily no matter who the issuer. Schemas allow us to do the same thing for Verifiable Credentials.

#### How can I issue credentials using Disco?[​](broken-reference) <a href="#how-can-i-issue-credentials-using-disco" id="how-can-i-issue-credentials-using-disco"></a>

* Connect your wallet to [Disco.xyz](http://disco.xyz/), navigate to another user’s profile and click “Issue Credential”. From there you can select a credential type, fill in the necessary information, sign and send!

#### How can I issue a large amount of credentials programmatically?[​](broken-reference) <a href="#how-can-i-issue-a-large-amount-of-credentials-programmatically" id="how-can-i-issue-a-large-amount-of-credentials-programmatically"></a>

* Use a third party library like Spruce’s DIDKit. Libraries like these allow an organization or app to issue credentials programmatically at a high volume.

#### Can I write verifiable credentials about myself?[​](broken-reference) <a href="#can-i-write-verifiable-credentials-about-myself" id="can-i-write-verifiable-credentials-about-myself"></a>

* You can write Verifiable Credentials about yourself. This means that the _issuer_ and the _subject_ of the credential are the same — both you. Self-attested credentials are commonly used to assert personal preferences like your favorite color or music genre.

#### What does it mean for a DID to sign a VC?[​](broken-reference) <a href="#what-does-it-mean-for-a-did-to-sign-a-vc" id="what-does-it-mean-for-a-did-to-sign-a-vc"></a>

* In the context of DIDs and VCs, a “signature” is a digital watermark on piece of data that is unique for every DID. The signature uses complicated cryptography to work but the end result is that someone who looks at the data that has been signed can trust that the data has not been altered in any way, additionally they can look at the signature and find out the DID that performed the signing.

#### What types of credentials can I issue?[​](broken-reference) <a href="#what-types-of-credentials-can-i-issue" id="what-types-of-credentials-can-i-issue"></a>

* Technically you can issue whatever credential you want, but it doesn’t mean others will recognize you as an authority for that credential and trust it. For example, I _can_ create a diploma and sign it with my name, but no one will recognize me as a trusted source of that information! Additionally, Disco only offers the ability to issue a subset of the possible credential types via the Disco web app. This list will grow with time, but as a rule of thumb, only issue credentials that you are an authority for!

#### What type of accounts can I link?[​](broken-reference) <a href="#what-type-of-accounts-can-i-link" id="what-type-of-accounts-can-i-link"></a>

* Right now we offer the ability to link together a few different types of accounts and identifiers: Twitter handle, Discord handle, and domain name. However, we will be expanding this list shortly to allow you to link many more different types of credentials.

#### Does Disco only work for Ethereum?[​](broken-reference) <a href="#does-disco-only-work-for-ethereum" id="does-disco-only-work-for-ethereum"></a>

* Just for now! However, Disco’s aim is to create interoperability across lots of different ecosystems! In the near future you will be able to use Disco with wallets from a number of different blockchains and you will be able to present credentials issued to one blockchain identifier (like your Ethereum address) _from_ a different blockchain identifier (like your Solana address)!

#### Can I partner with Disco?[​](broken-reference) <a href="#can-i-partner-with-disco" id="can-i-partner-with-disco"></a>

* Of course! We are always eager to onboard and work with new projects! Get in touch [here!](mailto:ask@disco.xyz)
