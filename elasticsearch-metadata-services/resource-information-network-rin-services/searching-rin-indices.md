---
description: Introduction to searching the RIN indices
---

# Searching RIN Indices

## Introduction

The Resources Information Network (RIN) APIs are provided via an ElasticSearch endpoint.   Simple URL based searches are available via the GET method.  More complex queries can be supplied via the POST method.

### Access to the RIN APIs

Access to the RIN API is provided via an Elasticsearch pass-through.

## Elasticsearch Pass-Through

<mark style="color:green;">`POST`</mark> `https://api.scicrunch.io/elastic/v1/{index}/_search`

The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the index, the type and the search command (\_search).\
\
Documentation on the Elasticsearch Search API is available at [https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html)&#x20;

#### Path Parameters

| Name                                    | Type   | Description          |
| --------------------------------------- | ------ | -------------------- |
| index<mark style="color:red;">\*</mark> | String | Production RIN index |

#### Headers

| Name                                     | Type   | Description                         |
| ---------------------------------------- | ------ | ----------------------------------- |
| apikey<mark style="color:red;">\*</mark> | String | Your API key to access the services |

#### Request Body

| Name | Type   | Description     |
| ---- | ------ | --------------- |
| data | String | JSON query body |

{% tabs %}
{% tab title="200: OK Successful request" %}
```json
{
    "took": 23,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {...}
}
```
{% endtab %}

{% tab title="401: Unauthorized No API key supplied" %}
```json
{
    "error": {
        "root_cause": [
            {
                "type": "security_exception",
                "reason": "action [indices:data/read/search] requires authentication",
                "header": {
                    "WWW-Authenticate": [
                        "Bearer realm=\"security\"",
                        "ApiKey",
                        "Basic realm=\"security\" charset=\"UTF-8\""
                    ]
                }
            }
        ],
        "type": "security_exception",
        "reason": "action [indices:data/read/search] requires authentication",
        "header": {
            "WWW-Authenticate": [
                "Bearer realm=\"security\"",
                "ApiKey",
                "Basic realm=\"security\" charset=\"UTF-8\""
            ]
        }
    },
    "status": 401
}
```
{% endtab %}

{% tab title="400: Bad Request API request is malformed" %}
```json
{
    "error": {
        "root_cause": [
            {
                "type": "illegal_argument_exception",
                "reason": "request [/RIN_Addgene_pr/rin/_search] contains unrecognized parameter: [api_key]"
            }
        ],
        "type": "illegal_argument_exception",
        "reason": "request [/RIN_Addgene_pr/rin/_search] contains unrecognized parameter: [api_key]"
    },
    "status": 400
}
```
{% endtab %}

{% tab title="404: Not Found The index or the uri is incorrect" %}
```json
{
    "error": {
        "root_cause": [
            {
                "type": "index_not_found_exception",
                "reason": "no such index",
                "resource.type": "index_or_alias",
                "resource.id": "RIN_Addgene",
                "index_uuid": "_na_",
                "index": "RIN_Addgene"
            }
        ],
        "type": "index_not_found_exception",
        "reason": "no such index",
        "resource.type": "index_or_alias",
        "resource.id": "RIN_Addgene",
        "index_uuid": "_na_",
        "index": "RIN_Addgene"
    },
    "status": 404
}
```
{% endtab %}

{% tab title="500: Internal Server Error The query is incorrect" %}
```json
{
    "error": {
        "root_cause": [
            {
                "type": "json_parse_exception",
                "reason": "Unexpected character ('=' (code 61)): was expecting a colon to separate field name and value\n at [Source: org.elasticsearch.transport.netty4.ByteBufStreamInput@4eccf1fd; line: 5, column: 25]"
            }
        ],
        "type": "json_parse_exception",
        "reason": "Unexpected character ('=' (code 61)): was expecting a colon to separate field name and value\n at [Source: org.elasticsearch.transport.netty4.ByteBufStreamInput@4eccf1fd; line: 5, column: 25]"
    },
    "status": 500
}
```
{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}
{% endtabs %}

## Elasticsearch Pass-Through

<mark style="color:blue;">`GET`</mark> `https://api.scicrunch.io/elastic/v1/{index}/_search`

The pass-through is accessible at https://scicrunch.org/api/1/elastic.  Similar to standard Elasticsearch APIs you must then supply an index and an action.  In this case the index, the type and the URL search query paramter.

\
Documentation on the Elasticsearch Search API is available at [https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/search.html)&#x20;

#### Path Parameters

| Name                                    | Type   | Description          |
| --------------------------------------- | ------ | -------------------- |
| index<mark style="color:red;">\*</mark> | String | Production RIN index |

#### Query Parameters

| Name | Type   | Description   |
| ---- | ------ | ------------- |
| q    | String | Search String |

#### Headers

| Name                                     | Type   | Description                         |
| ---------------------------------------- | ------ | ----------------------------------- |
| apikey<mark style="color:red;">\*</mark> | String | Your API key to access the services |

{% tabs %}
{% tab title="200: OK Successful request" %}

{% endtab %}

{% tab title="400: Bad Request API request is malformed" %}

{% endtab %}

{% tab title="401: Unauthorized No API key supplied" %}

{% endtab %}

{% tab title="403: Forbidden Invalid API key" %}

{% endtab %}

{% tab title="404: Not Found The index or the uri is incorrect" %}

{% endtab %}

{% tab title="500: Internal Server Error The query is incorrect" %}

{% endtab %}
{% endtabs %}

### RIN Index Aliases

Management of indices is accomplished via [Elasticsearch aliases](https://www.elastic.co/guide/en/elasticsearch/reference/6.8/indices-aliases.html). The index aliases are provided:

| Index Alias                        | Description                                  |
| ---------------------------------- | -------------------------------------------- |
| RIN\_Tool\_pr                      | Production tools index                       |
| RIN\_Antibody\_pr                  | Production antibodies index                  |
| RIN\_CellLine\_pr                  | Production cell lines index                  |
| RIN\_Organism\_pr                  | Production organisms index                   |
| RIN\_Addgene\_pr,RIN\_DGRC\_\*\_pr | Production plasmids (AddGene & DGRC) indices |
| RIN\_BioSample\_pr                 | Production biosamples index                  |
| RIN\_Protocols\_pr                 | Production protocols index                   |
| \*\_pr                             | Production all indices                       |

Using aliases will allow for testing on updates and enhancements to the  index structure.  If needed additional aliases can be constructed for specialized testing.
