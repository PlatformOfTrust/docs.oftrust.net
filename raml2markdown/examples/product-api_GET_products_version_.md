```python
import sys
sys.stdout.write("Python example missing. Why not contribute one for us?")
```

```shell
curl https://api-sandbox.oftrust.net/products/v1/
```

```javascript
<!doctype html>
<html lang="en">
<head>
  <script src="http://code.jquery.com/jquery-3.3.1.min.js"></script>
</head>
<body>

<script>
$( document ).ready(function() {
  var potAPI = "https://api-sandbox.oftrust.net/product/v1/products";
  $.getJSON( potAPI, function( data ) {
        alert(JSON.stringify(data));
    });
});
</script>

</body>
</html>
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
      "@context": "https://standards.oftrust.net/contexts/product.jsonld",
      "@type": "Product",
      "@id": "https://api-sandbox.oftrust.net/product/v1/products/prh-business-identity-data-product",
      "productCode": "prh-business-identity-data-product",
      "dataContext": null,
      "parameterContext": "https://standards.oftrust.net/contexts/product-parameters.jsonld",
      "translatorUrl": "http://translator-test-backend-app/business-identity",
      "name": "PRH Business Identity",
      "organizationPublicKeys": null,
      "description": "Returns business information from the PRH Open Data API",
      "imageUrl": null
    },
    ...
  ]
}

```