---
description: Decentralized Identifiers (DID) Personas for Data Backpack Holders
---

# User Persona

## Account Linking



Get persona data

/v1/persona/did/metadata/:did

```
{
    "orgBrand": {
        "textColor": "#000000",
        "brandColor": "#00ff66",
        "backgroundImage": ""
    },
    "avatar": "https://pbs.twimg.com/profile_images/1630919334917816331/v704WvO8_400x400.jpg",
    "accountLinks": [
        {
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "type": "Discord",
            "handle": "Mic#4261"
        },
        {
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "type": "Twitter",
            "handle": "michael_hansen"
        }
    ],
    "username": "michael_hansen"
}
```

/v1/persona/link?did=\{{mick\_did\}}\&type=\{{twitter\}}\&handle=\{{mick\_twitter\}}

```json
{
    "id": "99ed17e8-cd8c-4683-b395-e8fd5108df22",
    "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
    "type": "Twitter",
    "handle": "michael_hansen",
    "evidence": "https://twitter.com/michael_hansen/status/1626283127231373314",
    "status": "verified"
}
```

/v1/profile/address/\{{eth\_address\}}

```json
{
    "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
    "isDiscoOrg": true,
    "profile": {
        "avatar": "https://pbs.twimg.com/profile_images/1630919334917816331/v704WvO8_400x400.jpg",
        "name": "michael_hansen",
        "bio": "vp of eng @disco.xyz",
        "ethAddress": "0x08936438bfb8e9b269f978d5327ad684f47f8c05",
        "linkages": [
            {
                "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "type": "Discord",
                "handle": "Mic#4261"
            },
            {
                "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "type": "Twitter",
                "handle": "michael_hansen"
            }
        ],
        "orgBrand": {
            "textColor": "#000000",
            "brandColor": "#00ff66",
            "backgroundImage": ""
        }
    }
}
```



/v1/persona/find/eth/\{{eth\_address\}}

<pre class="language-json"><code class="lang-json">{
    "id": "de0eae21-b88f-4f22-ad92-7ed99f7ae50c",
    "user": {
        "id": "ae541371-590b-4dba-b783-5ced14cc0d3c"
    },
    "dids": [
        {
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "ethAddr": "0x08936438bfb8e9b269f978d5327ad684f47f8c05"
        }
    ],
    "handle": "michael_hansen",
    "avatarUri": "https://pbs.twimg.com/profile_images/1630919334917816331/v704WvO8_400x400.jpg",
    "bio": "vp of eng @disco.xyz",
    "ethAddress": "0x08936438bfb8e9b269f978d5327ad684f47f8c05",
    "links": [
        {
            "accountType": "Discord",
            "handle": "Mic#4261",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "proof": "https://discord.com/channels/947857036257935390/975763597529600041/1078306074618236980"
        },
        {
            "accountType": "Discord",
            "handle": "Mic#4261",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "proof": "https://discord.com/channels/947857036257935390/975763597529600041/1116035979627724890"
        },
        {
            "accountType": "Discord",
            "handle": "Mic#4261",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "proof": "https://discord.com/channels/947857036257935390/975763597529600041/1118573219776049222"
        },
        {
            "accountType": "Discord",
            "handle": "Mic#4261",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "proof": "https://twitter.com/michael_hansen/status/1626283127231373314"
        },
        {
            "accountType": "Discord",
            "handle": "Mic#4261",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "proof": "https://twitter.com/michael_hansen/status/1634569399997743104"
        },
        {
            "accountType": "Discord",
            "handle": "Mic#4261",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "proof": "https://twitter.com/michael_hansen/status/1667219955002032136"
        },
        {
            "accountType": "Twitter",
            "handle": "michael_hansen",
            "verified": true,
            "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
            "proof": "https://twitter.com/michael_hansen/status/1626283127231373314"
        }
    ],
    "metadata": {
        "orgBrand": {
            "textColor": "#000000",
            "brandColor": "#00ff66",
            "backgroundImage": ""
        },
        "avatar": "https://pbs.twimg.com/profile_images/1630919334917816331/v704WvO8_400x400.jpg",
        "accountLinks": [
            {
                "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "type": "Discord",
                "handle": "Mic#4261"
            },
            {
                "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "type": "Twitter",
                "handle": "michael_hansen"
            }
        ],
        "username": "michael_hansen"
    },
    "isOrg": true
<strong>}
</strong></code></pre>

/v1/persona/find/:type/:handle

```json
[
    {
        "id": "de0eae21-b88f-4f22-ad92-7ed99f7ae50c",
        "user": {
            "id": "ae541371-590b-4dba-b783-5ced14cc0d3c"
        },
        "dids": [
            {
                "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "ethAddr": "0x08936438bfb8e9b269f978d5327ad684f47f8c05"
            }
        ],
        "handle": "michael_hansen",
        "avatarUri": "https://pbs.twimg.com/profile_images/1630919334917816331/v704WvO8_400x400.jpg",
        "bio": "vp of eng @disco.xyz",
        "ethAddress": "0x08936438bfb8e9b269f978d5327ad684f47f8c05",
        "links": [
            {
                "accountType": "Twitter",
                "handle": "michael_hansen",
                "verified": true,
                "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                "proof": "https://twitter.com/michael_hansen/status/1667219955002032136"
            }
        ],
        "metadata": {
            "avatar": "https://pbs.twimg.com/profile_images/1630919334917816331/v704WvO8_400x400.jpg",
            "accountLinks": [
                {
                    "did": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6",
                    "type": "Twitter",
                    "handle": "michael_hansen"
                }
            ],
            "username": "michael_hansen"
        },
        "isOrg": false
    }
]
```

