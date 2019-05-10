```python
import requests
import json
import sys

endpoint = 'https://api-sandbox.oftrust.net/identities/v1/'
api_token= 'REPLACE_WITH_YOUR_TOKEN'
headers = {'Content-Type': 'application/json',
           'Authorization': 'Bearer {0}'.format(api_token)}

# Get the indentities
try:
        json_response = (requests.get(endpoint, headers=headers).json())
        print(json.dumps(json_response, indent=4, sort_keys=True))
except:
        print("Oops!",sys.exc_info()[0],"occured.")
```

```shell
curl https://api-sandbox.oftrust.net/identities/v1/ \
-H "Authorization: Bearer REPLACE_WITH_YOUR_TOKEN"
```

```javascript
console.error("Javascript example missing. Why not contribute one for us?");
```


```java
System.out.println("Java example missing. Why not contribute one for us?");
```

> The above example should return `JSON` structured like this:

```json
HTTP/1.0 200 OK

{
  "@context": "https://schema.org/",
  "@type": "collection",
  "ItemList": [
    {
      "@context": "http://platformoftrust.github.io/standards/contexts/identity-person.jsonld",
      "@type": "Person",
      "@id": "fbd106c5-c594-4416-a87e-f61e578fe829",
      "name": "John Doe",
      "data": {
        "firstName": "John",
        "lastName": "Doe",
        "gender": "Male"
      },
      "createdBy": "34fe0b13-e031-4ef2-822e-17eabad63259",
      "updatedBy": "34fe0b13-e031-4ef2-822e-17eabad63259",
      "createdAt": "2019-03-14T10:50:51+00:00",
      "updatedAt": "2019-03-14T11:17:35+00:00",
      "status": 0,
      "inLinks": [],
      "outLinks": []
    },
    ...
  ]
}}

```