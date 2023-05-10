---
description: 'A peek under the hood: Disco''s architectural components'
---

# Components

The **frontend** layer is responsible for

* Guiding you through the creation of a data backpack.
* Connecting your wallet to your DID through MetaMask.
* Allowing you to update your Disco profile information.
* Allowing you to send and receive Verifiable credentials and update the visibility of your Verifiable credentials.
* Containing JSON Schemas that define verifiable credentials.

The **backend** layer is responsible for:

* Serving as the data interface layer for mappings of profile data and verifiable credential data.
* Containing Disco’s API which allows you to pull user data.
* Containing cross-platform libraries and components used throughout Disco.

The **data storage** layer is responsible for:

* Storing and manages users’ DIDs and linked account information in a SQL database.
* Fetching credential and profile data from a decentralized network via users’ DIDs.

The **wallet** is responsible for:

* Signing in with any EVM Compatible Keys (Ethereum, Optimism, or other L2s)
* Allowing Disco to create (if it doesn't exist) and access your DID and associate it with your profile.
* Signing messages (credentials, account linkages) using your public-private keypair.
