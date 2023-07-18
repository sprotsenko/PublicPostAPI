# Quick Start

{% hint style="info" %}
**Good to know:** A quick start guide can be good to help folks get up and running with your API in a few steps. Some people prefer diving in with the basics rather than meticulously reading every page of documentation!
{% endhint %}

## Get your API keys

Your API requests are authenticated using API keys. Any request that doesn't include an API key will return an error.

You can get your API keys (Bearer and Token) for production and sandbox environment from the Ukrpost manager.



{% hint style="info" %}
**Good to know:** Using tabs to separate out different languages is a great way to present technical examples or code documentation without cramming your docs with extra sections or pages per language.
{% endhint %}

## Make your first request

To make your first request, send an authenticated request to the endpoint. This will retrieve a post office by providing a post index.

{% hint style="info" %}
**Good to know:** You can use the API Method block to fully document an API method. You can also sync your API blocks with an OpenAPI file or URL to auto-populate them.
{% endhint %}

Take a look at how you might call this method using our official libraries, or via `curl`:

{% tabs %}
{% tab title="curl" %}
```
curl --location 'https://www.ukrposhta.ua/address-classifierws/get_postoffices_by_postindex?pi=01001' \
--header 'Accept: application/json' \
--header 'Authorization: Bearer 11111111-2222-3333-aaaa-bcdef1234567'
```
{% endtab %}

{% tab title="Node" %}
```javascript
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://www.ukrposhta.ua/address-classifierws/get_postoffices_by_postindex?pi=01001',
  'headers': {
    'Accept': 'application/json',
    'Authorization': 'Bearer 11111111-2222-3333-aaaa-bcdef1234567'
  }
};
request(options, function (error, response) {
  if (error) throw new Error(error);
  console.log(response.body);
});
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

url = "https://www.ukrposhta.ua/address-classifierws/get_postoffices_by_postindex?pi=01001"

payload = {}
headers = {
  'Accept': 'application/json',
  'Authorization': 'Bearer 11111111-2222-3333-aaaa-bcdef1234567'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```
{% endtab %}
{% endtabs %}
