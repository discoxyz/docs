# API Endpoints

### Current Capabilities

**Profiles**

* [Get By DID](https://docs.disco.xyz/v2/for-developers/get-started-with-discos-api/profiles#get-profile-by-did)
* [Get By ETH Address](https://docs.disco.xyz/v2/for-developers/get-started-with-discos-api/profiles#get-profile-by-ethereum-address)
* [Search By Account Linkage](https://docs.disco.xyz/v2/for-developers/get-started-with-discos-api/profiles#search-for-profile-by-account-linkages)

**Credentials**

* [Get all Credentials](https://docs.disco.xyz/v2/for-developers/get-started-with-discos-api/credentials#get-all-credentials)
* [Get credential type](https://docs.disco.xyz/v2/for-developers/get-started-with-discos-api/credentials#get-a-credential-type)
* [Specific Credential from Disco Profile](https://docs.disco.xyz/v2/for-developers/guide-parsing-out-account-linkages)
* [Parse Account Linkages](https://docs.disco.xyz/v2/for-developers/guide-parsing-out-account-linkages)

#### Verify Credentials

* [Verify Credentials](https://docs.disco.xyz/v2/for-developers/get-started-with-discos-api/credentials#verify-a-credential)

**Issue Credentials**

* Programmatic Issuance
  * [Locate Schema](https://docs.disco.xyz/v2/for-developers/guide-parsing-out-account-linkages)
  * [Authentication](https://docs.disco.xyz/v2/for-developers/guide-parsing-out-account-linkages)
  * [Create Request](https://docs.disco.xyz/v2/for-developers/guide-parsing-out-account-linkages)

{% hint style="info" %}
**Privacy Note:** At Disco we take privacy very seriously. The API will only return credentials that are made public by the user. Credentials are by default, private. More info on how to make a credential public by toggling the eye icon[ here](https://docs.disco.xyz/v2/learn-more/faqs#does-disco-only-work-for-ethereum).
{% endhint %}

### Request Examples

in curl: to GET a specific profile

```sh
curl --location 'https://api.disco.xyz/v1/profile/address/0xc5e46e48f1ef5f305afba45c3122021dd09ed3de' \
--header 'Authorization: Bearer <token>'
```

in Javascript, to GET a specific profile

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
​
var requestOptions = {
method: 'GET',
headers: myHeaders,
redirect: 'follow'
};
​
fetch("https://api.disco.xyz/v1/profile/address/0xc5e46e48f1ef5f305afba45c3122021dd09ed3de", requestOptions)
.then(response => response.text())
.then(result => console.log(result))
.catch(error => console.log('error', error));
```
