# Searching InterLex

## Introduction

The InterLex APIs are provided via an ElasticSearch endpoint.  &#x20;

### Access to the InterLex APIs

Access to the InterLex API is provided via an Elasticsearch pass-through.

{% swagger baseUrl="https://api.scicrunch.io" path="/elastic/v1/Interlex_pr/_search" method="post" summary="Elasticsearch Pass-Through" %}
{% swagger-description %}
The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the Interlex index (Interlex\_pr) and the search command (\_search).\
\
Documentation on the Elasticsearch Search API is available at https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html&#x20;
{% endswagger-description %}

{% swagger-parameter in="path" name="index" type="string" required="true" %}
For InterLex this is Interlex\_pr
{% endswagger-parameter %}

{% swagger-parameter in="header" name="apikey" required="true" %}
Your API key to access the services
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" %}
JSON query body
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
    "took": 35,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {...
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/elastic/v1/Interlex_pr/_search" baseUrl="https://api.scicrunch.io" summary="Elasticsearch Pass-Through" %}
{% swagger-description %}
The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the Interlex index (Interlex\_pr) and the search command (\_search).\
\
Documentation on the Elasticsearch Search API is available at https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html&#x20;
{% endswagger-description %}

{% swagger-parameter in="header" name="apikey" required="true" %}
Your API key to access the services
{% endswagger-parameter %}

{% swagger-parameter in="path" name="index" required="true" %}
For InterLex this is Interlex\_pr
{% endswagger-parameter %}

{% swagger-parameter in="query" name="q" %}
Search String
{% endswagger-parameter %}
{% endswagger %}

### Interlex indices

Management of indices is accomplished via [Elasticsearch aliases](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/indices-aliases.html). The index aliases are provided:

| Index Alias  | Description               |
| ------------ | ------------------------- |
| Interlex\_pr | Production Interlex index |

Using aliases will allow for testing on updates and enhancements to the  index structure.  If needed additional aliases can be constructed for specialized testing.
