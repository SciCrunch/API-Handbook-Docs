---
description: Information about RRID resolver
---

# The RRID Resolver

## Introduction

The RRID resolver provides the ability to resolve an RRID without the need for an API key. The resolver by default returns information in a structured report.  In addition, results can be retrieved in JSON format.

For example the resolver page for a software tool (fMRIPrep) can be resolved via the following URL: [https://scicrunch.org/resolver/RRID:SCR\_016216](https://scicrunch.org/resolver/RRID:SCR\_016216)

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption><p>RRID Resolver Report</p></figcaption></figure>

## Retrieving JSON Metadata for an RRID

{% swagger method="get" path="/resolver/{RRID}.json" baseUrl="https://scicrunch.org" summary="Use the RRID resolver to return metadata in JSON format" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="path" name="RRID" required="true" %}
The RRID being resolved
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="RRID Found" %}

{% endswagger-response %}

{% swagger-response status="404: Not Found" description="RRID Not Found" %}

{% endswagger-response %}
{% endswagger %}
