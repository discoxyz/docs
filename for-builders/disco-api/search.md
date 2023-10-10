# Search

post v1/credentials/search

```postman_json
{
    "criteria": [
        {
            "field": "issuer",
            "operator": "=",
            "value": "did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6"
        }
    ],
    "conjunction": "and",
    "page": 1,
    "size": 100
}
```

get **v1/credentials/search**?field=issuer\&op==\&value=did:3:kjzl6cwe1jw149lyliyfh4mbjgy59rhoktkhsoc7suu2trqje2wigrgea21bqy6\&page=1\&size=10
