```python
import sys
sys.stdout.write("Python example missing. Why not contribute one for us?")
```

```shell
curl -X POST https://api-sandbox.oftrust.net/messages/v1/ \
-H "Content-Type: application/json" \
-H "Authorization: Bearer REPLACE_WITH_YOUR_TOKEN" \
-d '{
	"toIdentity": "34fe0b13-e031-4ef2-822e-17eabad63259",
	"subject": "Test message nr 1",
	"content": "Testing the message api",
	"cc": [
		"34fe0b13-e031-4ef2-822e-17eabad63259"
	]
}'
```

```javascript
console.error("Javascript example missing. Why not contribute one for us?");
```


```java
System.out.println("Java example missing. Why not contribute one for us?");
```

> The above example should return `JSON` structured like this:

```json
HTTP/1.0 201 Created

{
  "@context": "https://standards.oftrust.net/contexts/message.jsonld",
  "@type": "Message",
  "@id": "3a9e31ff-b654-4069-8361-6b446dc04c95",
  "toIdentity": "34fe0b13-e031-4ef2-822e-17eabad63259",
  "subject": "Test message nr 1",
  "content": "Testing the message api",
  "cc": [
    "34fe0b13-e031-4ef2-822e-17eabad63259"
  ],
  "readBy": [],
  "createdBy": "34fe0b13-e031-4ef2-822e-17eabad63259",
  "updatedBy": null,
  "createdAt": "2019-03-14T13:55:12+00:00",
  "updatedAt": "2019-03-14T13:55:12+00:00"
}

```