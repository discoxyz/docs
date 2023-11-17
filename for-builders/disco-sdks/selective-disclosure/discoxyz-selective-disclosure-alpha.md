---
description: Early Alpha Release of Disco Selective Disclosure SDK
---

# @discoxyz/selective-disclosure (alpha)

## Installation

To get started, add `@discoxyz/selective-disclosure` to your project:

{% tabs %}
{% tab title="Yarn" %}
```bash
yarn add @discoxyz/selective-disclosure
```
{% endtab %}

{% tab title="NPM" %}
```bash
npm i @discoxyz/selective-disclosure
```
{% endtab %}
{% endtabs %}

## Key exports

### DisclosureProvider

This provider handles API keys and authentication, to trigger the modal and access storage resources. For example:

{% tabs %}
{% tab title="React" %}
```tsx
import {useDiscoDisclosure} from '@discoxyz/selective-disclosure'

// Currently we support disco & ceramic endpoints
const config = {
        projectKey: 'ABCD...' // Your Disco API key
}

const App = ({children}) => {
    return (
        <DisclosureProvider config={config}>
            {children}
        </DisclosureProvider>
    )
}
```
{% endtab %}
{% endtabs %}

### requestAsync(request, provider)

`request`

An object representing the credential, or collection of credentials, that you are looking for.

<table><thead><tr><th width="178.33333333333331">Property</th><th width="166">Type</th><th>Description</th></tr></thead><tbody><tr><td><code>issuer</code></td><td><code>string[]</code></td><td>A list of the possible issuers of your credential</td></tr><tr><td><code>schema</code></td><td><code>string[]</code></td><td>An array of links to the permissible schemas. Schemas can be found at <code>@discoxyz/schemas</code></td></tr></tbody></table>

```javascript
const requestShape = {
        'AND': [ // This means that each criteria must be met
            {
                schema: [Membership], // Will find a match from an array
                issuer: [Disco]
            },{
                schema: [Participation],
                issuer: [Guild]
            }
        ]
    }
```

Response

<table><thead><tr><th width="177"></th><th width="189.33333333333331">Type</th><th>Meaning</th></tr></thead><tbody><tr><td><code>status</code></td><td><mark style="color:purple;"><code>'success'</code></mark></td><td>The user presented valid credentials</td></tr><tr><td></td><td><mark style="color:orange;"><code>'rejected'</code></mark></td><td>The user rejected the request</td></tr><tr><td></td><td><mark style="color:red;"><code>'invalid'</code></mark></td><td><a data-footnote-ref href="#user-content-fn-1">The user presented invalid credentials</a></td></tr><tr><td></td><td><mark style="color:red;">'<code>notConnected'</code></mark></td><td>The user's wallet is not connected</td></tr><tr><td></td><td><mark style="color:red;">'<code>invalidApi</code>'</mark></td><td>The keys provided for the API are invalid.</td></tr><tr><td></td><td><mark style="color:red;"><code>'error'</code></mark></td><td>Another error occurred. Information will be provided in the <code>message</code>.</td></tr><tr><td><code>message</code></td><td><code>String</code></td><td>A message to help you provide context in your UI. Helpful in the case of error messages</td></tr><tr><td><code>presentation</code></td><td><code>Presentation</code></td><td>The Verifiable Presentation, which you can independently check to verify authenticity.</td></tr></tbody></table>

{% tabs %}
{% tab title="success" %}
```javascript
{
    status: 'success',
    message: 'Presented 2 credentials successfully',
    presentation: ...
}
```
{% endtab %}

{% tab title="rejected" %}
```javascript
{
    status: 'rejected',
    message: 'The presentation request was rejected'
}
```
{% endtab %}

{% tab title="invalid" %}
```
{
    status: 'invalid',
    message: 'The presentation was invalid'
}
```
{% endtab %}

{% tab title="notConnected" %}
```
{
    status: 'notConnected',
    message: 'No wallet is connected'
}
```
{% endtab %}

{% tab title="invalidApi" %}
```
{
    status: 'invalidApi',
    message: 'An API endpoint could not be reached...'
}
```
{% endtab %}

{% tab title="error" %}
```
{
    status: 'error',
    message: ...
}
```
{% endtab %}
{% endtabs %}

***

## Requesting a presentation

Example:

{% tabs %}
{% tab title="React" %}
<pre class="language-tsx"><code class="lang-tsx">import { useDiscoDisclosure } from "@discoxyz/selective-disclosure";
<strong>import ( React } from "react";
</strong>import { useAccount } from "wagmi";

const Disclose: React.FC = () => {
    
    // ✅ Use Request Async
    const { requestAsync } = useDiscoDisclosure();
    
    // Store the result
    const [result, setResult] = useState&#x3C;RequestResult | undefined>()
    
    const requestShape: RequestShape = {
        'AND': [ // This means that each criteria must be met
            {
                schema: ["Membership"], // Will find a match from an array
                issuer: [DiscoDID],
                count: 1
            },{
                schema: ["Participation"],
                issuer: [GuildDID],
                count: 2
            }
        ]
    }
    
    async function sendRequest() {
        
        // 📨 Send the request. This triggers a modal for the user
        const result = await requestAsync(provider, requestShape)
        
        // If no presentation, errors are present
        if (!result.presentation) return
        
        // Now set the result
       setResult(result)
    }


    return (
        &#x3C;div>
            &#x3C;button onClick={sendRequest}>Reveal Credential&#x3C;/button>
            {result ? &#x3C;p>{status.message}&#x3C;/p>
            : &#x3C;p>Request not started&#x3C;/p>}
        &#x3C;/div>
<strong>    )
</strong>}
</code></pre>
{% endtab %}
{% endtabs %}


## Extracting Issuers

Example:
{% tabs %}
{% tab title="Node" %}
<pre class="language-tsx"><code class="lang-tsx">// Received Presentaion
const result = {
    "presentation": {
        ..., //other properties
        "verifiableCredential": [

        ]
    },
    "status": "success",
    "message":
}

// After receiving the presentation, 
// you can extract the credentials array from the following properties.

<strong>const credentials = result.presentation.verifiableCredential</strong>

// These Credentials can either be JWT's or JSON-LD. 
// You can use a regex like below to determine 
// And a library like did-jwt or jsonwebtoken to decode the jwts.

<strong>import { decodeJWT } from "did-jwt";

const jwtRegex = /^([a-zA-Z0-9_-]+)\.([a-zA-Z0-9_-]+)\.([a-zA-Z0-9_-]+)$/;

const res = vp.presentation.verifiableCredential.map((vc: any) => {
    return vc.match(jwtRegex) ? decodeJWT(vc).payload : JSON.parse(vc)
})

const issuers = res.map((vc:any) => {
    return vc.issuer.id;
})</strong>

//Now with the issuers we can see who signed the metIRL credential for this user
console.log(issuers)

</pre>
{% endtab %}
{% endtabs %}


[^1]: 
