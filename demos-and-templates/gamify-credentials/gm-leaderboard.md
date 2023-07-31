# GM Leaderboard

### Show your rank

A leaderboard to rank users against each other, counting the number of _public GMs_ in their data backpacks. Check it out [here](http://gm.disco.xyz)

&#x20;

<figure><img src="../../.gitbook/assets/Screen Shot 2023-07-28 at 12.06.50 PM.png" alt=""><figcaption></figcaption></figure>



### How it works:

This is a nextJS app using Firebase's Firestore and Cloud Functions as backend. Whenever a user connects their wallet, the application pings the Disco API on the Ethereum address and fetches the total number of GM credentials.&#x20;

Will also run a CRON job periodically overnight to update counts for users who haven't connected their wallet.



### Links

Demo - https://gm.disco.xyz[^1]

README - [https://github.com/discoxyz/disco-gm-leaderboard](https://github.com/discoxyz/disco-gm-leaderboard)

[^1]: 
