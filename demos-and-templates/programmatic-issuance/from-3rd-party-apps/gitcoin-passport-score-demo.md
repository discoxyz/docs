# Gitcoin Passport Score Demo

### What

The Gitcoin Passport Score Integration is a Next.js application that interacts with the Gitcoin API to retrieve information about an account's Passport score, value and value rating. This data is issued as a Gitcoin Passport Score Credential to the connected wallet's Disco Data Backpack, allowing users to claim their Gitcoin Passport Score as a verifiable credential in Disco.

### **How it works:**

1. The app communicates with the Gitcoin API to request the connected user's on-chain score, including the value and value rating.
2. Upon receiving the score data, the app makes a request to Disco's API to do [programmatic-issuance.md](../../../for-builders/api-endpoints/programmatic-issuance.md "mention").
3. Credential is waiting in the user's backpack! They can go to http://app.disco.xyz to make it public.

### **Links/Resources:**&#x20;

* GitHub Repository: [Gitcoin Passport Score Integration](https://github.com/discoxyz/disco-gitcoin-passport-score)
