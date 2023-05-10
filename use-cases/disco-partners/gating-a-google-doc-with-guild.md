# Gating a Google Doc with Guild

### **Summary**

Let's see just how easy it is to get started using Disco and Guild to gate a Google Doc now!

In the following steps, we'll walk you through gating access to a **Google Doc** if the users have an `OfficialDisconautCredential` issued during onboarding. (Full steps and instructions on creating a data backpack [here](https://docs.disco.xyz/getting-started/data-backpack)).

**Note:** Users will be required to mark their credential as public so that the API will be able to query it. This is like implicit consent ;)



### Instructions

Visit guild.xyz, and click Create a Guild.&#x20;

Choose **Google Workspace** as the designated platform. Be sure that your wallet is connected and you've signed a message to verify ownership.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Add the following Google Account as an editor to your document, so it can have the appropriate access. Note that you'll have to have admin access to the Google Doc itself too!

<figure><img src="../../.gitbook/assets/Screen Shot 2023-05-02 at 12.25.09 PM.png" alt=""><figcaption></figcaption></figure>

Once the Google Account has been added, click on Gate Access back in Guild. Then, specify whether we want _read, comment, or write_ access.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-05-02 at 12.28.33 PM.png" alt=""><figcaption></figcaption></figure>

Click Next, and "Start from Scratch" as your Template.

Proceed to Creating the Guild.&#x20;

Once the guild has been created, click the pencil icon next to the _Member Role_ that was created.&#x20;

<figure><img src="../../.gitbook/assets/Screen Shot 2023-05-02 at 12.31.17 PM.png" alt=""><figcaption></figcaption></figure>

**Let's add a requirement now** so that we only grant access to people with a certain type of Credential in their Disco Data Backpack. Click on _Add Requirements_. Under the List of _Integrations_, search for Disco.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-05-02 at 1.48.52 PM.png" alt=""><figcaption></figcaption></figure>



**Add the Credential Requirement**.

Under Credential Type, you’ll need to fill in the exact type of Credential you’d like to be checking for. Ensure that you type the exact credential the way it’s spelled: `OfficialDisconautCredential`, `MembershipCredential` and optionally, the Issuer DID!

We'll check for the OfficialDisconautCredential below.

![](https://docs.disco.xyz/assets/images/image4-19a96f10acd573033644ae929cf83585.png)

_**Hit Save**_**, and now you have a Google Doc gated by a Verifiable Credential**! You can now distribute this link, and people can check if they have access by connecting their wallet.
