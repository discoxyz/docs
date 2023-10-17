---
description: >-
  The following guide describes how you can issue credentials in batch from a
  CSV or list.
---

# Batch Issuance

### Batch Issuance

**Preparation:**&#x20;

Batch issuance allows you to issue any credential to a group of DIDs, or Ethereum addresses using _one single click_. In this case, you can issue membership credentials to your entire list of members in one click.

{% hint style="info" %}
Remember that you will need special permissions, an Organization Credential from Disco. Fill out [this](https://discoxyz.typeform.com/orgcred?typeform-source=app.gitbook.com) form to request one.
{% endhint %}

You will need a .csv file of these addresses, or you can manually input them. [Here](https://docs.google.com/spreadsheets/d/13oj4aKz6ENG0OmqiKNRhPgkUP7XyHJrrccS040x2VWI/edit#gid=577048407) is an example of using DIDs, but you can also replace this with ETH addresses.

**Issuance**

Now you have your CSV prepared, we can issue! Start by navigating to "_Schemas"_ on the top navigation bar.

<img src="../../.gitbook/assets/image (10).png" alt="" data-size="original">

Click on _**Issue Credential**_. Select the schema that you’d like to issue. If you’d like a custom schema to be added, please reach out in the Discord.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-05-31 at 12.52.53 PM.png" alt="" width="563"><figcaption></figcaption></figure>

Fill out any relevant fields, and Choose your CSV file you'd like to upload.

<figure><img src="../../.gitbook/assets/Screen Shot 2023-05-31 at 12.51.20 PM.png" alt="" width="563"><figcaption></figcaption></figure>

Ensure you include only one DID (or Eth Address) on each line in your CSV file. Also, make sure there's a "new line" after the last entry in your CSV file. For example:

<figure><img src="../../.gitbook/assets/Screenshot 2023-10-17 at 3.52.41 PM.png" alt=""><figcaption><p>CSV Example</p></figcaption></figure>

Once you’ve uploaded your CSV or put in the recipients manually, the DIDs will populate and you can click on **Issue** to fire them off. Congrats!
