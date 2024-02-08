# Basic SPARC Searche Examples

## Boolean Filter Search

This search finds data given by generating a boolean query across facets. Currently this is also combined with an optional text based search, although this may be removed in future.

### JSON Body example

```yaml
{
  "size": 10,
  "from": 0,
  "query": {
    "query_string": {
      "query": "(Ardell) AND attributes.subject.sex.value:((male) OR (female))  AND anatomy.organ.name.aggregate:((heart))"
    }
  }
}
```

### Result

```yaml
{
    "took": 2070,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 5,
        "max_score": 5.709837,
        "hits": [
            {
                "_index": "scr_017041-sparc_datasets-ks_2021apr28",
                "_type": "ks",
                "_id": "DOI:10.26275/w4my-puqm",
                "_score": 5.709837,
//...
```

## Available Facets Query

This query requests available facets for a given parameter in the 'hits' object.

### JSON Body example

```yaml
{
  "from": 0,
  "size": 0,
  "aggregations": {
    "genotype": {
      "terms": {
        "field": "anatomy.organ.name.aggregate",
        "size": 200,
        "order": [
          {
            "_count": "desc"
          },
          {
            "_key": "asc"
          }
        ]
      }
    }
  }
}
```

### Result

```yaml
{
    "took": 2,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 88,
        "max_score": 0.0,
        "hits": []
    },
    "aggregations": {
        "genotype": {
            "doc_count_error_upper_bound": 0,
            "sum_other_doc_count": 0,
            "buckets": [
                {
                    "key": "heart",
                    "doc_count": 21
                },
//...
```

## Search for all DOI

This search looks for all DOIs.

### JSON Body Example

```yaml
{
    "from": 0,
    "size": 0,
    "aggregations": {
        "doi" : {
            "composite": {
                "size": 1000,
                "sources": [
                    {
                        "curie": {"terms": {"field": "item.curie.aggregate"}}
                    }
                ],
                "after": {"curie": ""}
            }
        }
    }
```

### Result

```yaml
{
    "took": 31,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 98,
        "max_score": 0.0,
        "hits": []
    },
    "aggregations": {
        "doi": {
            "after_key": {
                "curie": "doi:10.26275/zxe9-o3ss"
            },
            "buckets": [
                {
                    "key": {
                        "curie": "doi:10.26275/0ag5-j3x7"
                    },
                    "doc_count": 1
                }, ...
```

## Search for dataset by title

This search looks for a dataset by title.

### JSON Body Example

```yaml
{
    "size": 20,
    "from": 0,
    "query": {
        "query_string": {
            "fields": [
                "item.names.name"
            ],
            "query": "(Generic) AND (rat) AND (stomach) AND (scaffold)"
        }
    }
}
```

### Result

```yaml
{
    "took": 22,
    "timed_out": false,
    "_shards": {
        "total": 2,
        "successful": 2,
        "skipped": 0,
        "failed": 0
    },
    "hits": {
        "total": 1,
        "max_score": 7.7667675,
        "hits": [
            {
                "_index": "scr_017041-sparc_portal-ks-2021jun22",
                "_type": "ks",
                "_id": "DOI:10.26275/dn1d-owj9",
                "_score": 7.7667675,
                "_source": {
                    "item": {
                        "version": {
                            "keyword": "1.1.2"
                        },
                        "types": [
                            {
                                "curie": "ilx:0102834",
                                "name": "Dataset",
                                "type": "category"
                            }
                        ],
                        "contentTypes": [
                            {
                                "curie": "ilx:0381348",
                                "name": "product"
                            }
                        ],
                        "names": [
                            {
                                "nameType": "Complete Data Set",
                                "name": "Generic rat stomach scaffold"
                            }
                        ],
                        "statistics": {
                            "files": {
                                "count": "24"
                            },
                            "directory": {
                                "count": "4"
                            },
                            "bytes": {
                                "count": "5582424"
                            }
                        }, ...
```
