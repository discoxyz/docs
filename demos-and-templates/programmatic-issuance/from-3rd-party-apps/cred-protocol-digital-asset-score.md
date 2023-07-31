# Cred Protocol Digital Asset Score

### What

The [Cred Protocol ](https://www.credprotocol.com/)Digital Asset Score Demo is a simple next.js application that communicates with the Cred Protocol API to retrieve information about an account's on-chain score, including the value and value rating of their digital assets. The fetched score data is issued as a verifiable credential to the connected wallet's Disco Data Backpack.

[Demo Link](https://disco-credit-score-issuer.vercel.app/)

### **How it works:**

1. The next.js application interacts with the Cred Protocol API to request the digital asset score for a specific account.
2. Upon receiving the score data, the app makes a request to Disco's API to do [programmatic-issuance.md](../../../for-builders/api-endpoints/programmatic-issuance.md "mention").
3. Credential is waiting in the user's backpack! They can go to http://app.disco.xyz to make it public.

### **Links/Resources:**&#x20;

GitHub Repository: [Cred Protocol Digital Asset Score Demo](https://github.com/discoxyz/disco-credit-score-issuer)
