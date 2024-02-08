---
description: Overview of API key usage
---

# Using your API key

The preferred method to authenticate with your API key is through the use of an apikey submitted as part of the HTTP header for the request.&#x20;

Examples for authentication are provided through some simple CURL requests using the Resource Information Network Services

{% tabs %}
{% tab title="HTTP Header" %}
{% code overflow="wrap" %}
```sh
curl -i --verbose --location 'https://api.scicrunch.io/elastic/v1/_cat/aliases' --header 'apikey: <<YOUR API KEY>>'
```
{% endcode %}
{% endtab %}

{% tab title="URL Query Paramter" %}
{% code overflow="wrap" %}
```sh
curl -i --verbose --location 'https://api.scicrunch.io/elastic/v1/_cat/aliases?key=<<YOUR API KEY>>'
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
## Best Practice

Use the apikey HTTP header for authentication
{% endhint %}

