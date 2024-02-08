# Searching SPARC Dataset Indices

## Introduction

The SPARC metadata APIs are provided via an ElasticSearch endpoint.  &#x20;

### Access to the metadata APIs

Access to the metadata API is provided via an Elasticsearch pass-through.

{% swagger baseUrl="https://api.scicrunch.io" path="/elastic/v1/SPARC_Algolia_pr/_search" method="post" summary="Elasticsearch Pass-Through" %}
{% swagger-description %}
The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the SPARC Portal Dataset metadata (SPARC\_Algolia\_pr) and the search command (\_search).\
\
Documentation on the Elasticsearch Search API is available at https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html&#x20;
{% endswagger-description %}

{% swagger-parameter in="header" name="apikey" required="true" %}
Your API key to access the services
{% endswagger-parameter %}

{% swagger-parameter in="body" name="data" %}
JSON query body
{% endswagger-parameter %}

{% swagger-parameter in="path" required="true" name="index" %}
For SPARC datasets this is SPARC\_Algolia\_pr
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful response" %}

{% endswagger-response %}
{% endswagger %}

{% swagger method="get" path="/elastic/v1/SPARC_Algolia_pr/_search" baseUrl="https://api.scicrunch.io" summary="Elasticsearch Pass-Through" %}
{% swagger-description %}
The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the SPARC Portal Dataset metadata (SPARC\_Algolia\_pr) and the search query parameter.\
\
Documentation on the Elasticsearch Search API is available at https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html&#x20;
{% endswagger-description %}

{% swagger-parameter in="query" name="q" %}
Search string
{% endswagger-parameter %}

{% swagger-parameter in="header" name="apikey" required="true" %}
Your API key to access the services
{% endswagger-parameter %}

{% swagger-parameter in="path" name="index" required="true" %}
For SPARC datasets this is SPARC\_Algolia\_pr
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="Successful response" %}

{% endswagger-response %}
{% endswagger %}

### SPARC metadata indices

Management of indices is accomplished via [Elasticsearch aliases](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/indices-aliases.html). Three index aliases are provided:

| SPARC\_Algolia\_pr | Production index for SPARC datasets |
| ------------------ | ----------------------------------- |

Using aliases will allow for testing on updates and enhancements to the metadata index structure.  If needed additional aliases can be constructed for specialized testing.
