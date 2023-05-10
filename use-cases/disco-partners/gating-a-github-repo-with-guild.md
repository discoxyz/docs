# Gating a Github Repo with Guild

**Summary**

In this example, we'll gate access to a private Github Repo. We only want members with the Disconaut Credential to have access to this repo.

### Instructions

Visit guild.xyz, and click Create a Guild.&#x20;

Choose **Github Repo** as the designated platform. Be sure that your wallet is connected and you've signed a message to verify ownership.

<figure><img src="../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

Go through the OAuth flow again, and select the repo that you'd like to gate.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-05-02 at 1.51.49 PM.png" alt=""><figcaption></figcaption></figure>

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

_**Hit Save**_**, and now you have a Github Repo gated by a Verifiable Credential**! You can now distribute this link, and people can check if they have access by connecting their wallet.
