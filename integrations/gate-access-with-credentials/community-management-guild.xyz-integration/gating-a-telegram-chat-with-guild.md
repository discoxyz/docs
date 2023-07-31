# Gating a Telegram Chat with Guild

### **Summary**

Let's see just how easy it is to get started using Disco and Guild to gate a Telegram Chat..

In the following steps, we'll walk you through gating access to a Telegram Chat if the users have an `OfficialDisconautCredential` issued during onboarding. (Full steps and instructions on creating a data backpack [here](https://docs.disco.xyz/getting-started/data-backpack)).

**Note:** Users will be required to mark their credential as public so that the API will be able to query it. This is like implicit consent ;)



### Instructions

Visit guild.xyz, and click Create a Guild.&#x20;

Choose **Telegram** as the designated platform. Be sure that your wallet is connected and you've signed a message to verify ownership.

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

First, be sure that you have a Telegram Group ready to gate. You'll add the Guild bot to the chat in Telegram, and enter the group ID including the dash in the beginning. Example: -953090436

<figure><img src="../../../.gitbook/assets/Screen Shot 2023-05-02 at 11.42.33 AM.png" alt=""><figcaption></figcaption></figure>

**Add Integration.**

Let’s make it so that we only grant access to people with a certain type of Credential in their Disco Data Backpack. Click on _Add Requirements_. Under the List of _Integrations_, select Disco.

![](https://docs.disco.xyz/assets/images/requirement-e61356dd04d08ef0bca3e7950cd55a4c.png)

**Add the Credential Requirement**.

Under Credential Type, you’ll need to fill in the exact type of Credential you’d like to be checking for. Ensure that you type the exact credential the way it’s spelled: `OfficialDisconautCredential`, `MembershipCredential` and optionally, the Issuer DID!

We'll check for the OfficialDisconautCredential below.

![](https://docs.disco.xyz/assets/images/image4-19a96f10acd573033644ae929cf83585.png)

_**Hit Save**_**, and now you have a community gating resources by Verifiable Credentials**! You can now distribute this link, and people can check if they have access by connecting their wallet.

\
