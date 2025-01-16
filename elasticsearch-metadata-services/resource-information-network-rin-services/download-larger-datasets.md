# Download Larger Datasets

If you are new to our API service, we recommend starting with “[Getting Started with the APIs](https://app.gitbook.com/o/-MKC-C_E8VrlFQpFKwue/s/IFPUklTpgWYMOYnZkrEP/api-service-gateway-overview/getting-started-with-sparc-apis)” and “[Using your API key](https://app.gitbook.com/o/-MKC-C_E8VrlFQpFKwue/s/IFPUklTpgWYMOYnZkrEP/api-service-gateway-overview/using-your-api-key)” for helpful guidance first. If you have any questions, please do not hesitate to contact us.\
\
With a large number of records to download you would not be able to do that via a simple Elasticsearch search as Elasticsearch's paging limit is 10,000 records. Therefore, you need to use Elasticsearch's scroll mechanism. An example of such a curl request would be (Note: for normal queries you would not add the ?scroll=1s to the end):\
\
**Initialize Download an Entire Index**\
\
To download an entire index from the API, use the following curl command:

`curl --location 'https://api.scicrunch.io/elastic/v1/<<YOUR<https://api.scicrunch.io/elastic/v1/%3C%3CYOUR> TARGET INDEX>>/_search?scroll=1s' \`\
`--header 'Content-Type: application/json' \`\
`--header 'apikey: <<YOUR API KEY>>' \`\
`--data '{ <<YOUR QUERY HERE>> }'`\
\
Make sure to replace the placeholders:

<\<YOUR TARGET INDEX>> with the index you're targeting.

<\<YOUR API KEY>> with your API key.

<\<YOUR QUERY HERE>> with the specific query you want to execute.

For example queries, refer to the following link:[ Example Queries](basic-rin-search-examples.md).

\


**Page Through Index and Download Content**

\
To download specific content you would add a query component to the initial scroll request.

\
This would yield results:\
`{`\
`"_scroll_id": "DnF1ZXJ5VGhlbkZldGNoAgAAAAAF-0fRFkhYNzFBb1loU1dLbVpicWpmSTl3b1EAAAAABftH0hZIWDcxQW9ZaFNXS21aYnFqZkk5d29R",`\
`"took": 19,`\
`"timed_out": false,`\
`"_shards": {`\
`"total": 2,`\
`"successful": 2,`\
`"skipped": 0,`\
`"failed": 0`\
`},`\
`"hits": { ...`\
\
You would then use the scroll\_id for future request:\
\
`curl --location 'https://api.scicrunch.io/elastic/v1/_search/scroll' \`\
`--header 'Content-Type: application/json' \`\
`--header 'apikey: <<YOUR API KEY>>' \`\
`--data '{`\
`"scroll" : "1s",`\
`"scroll_id" : "DnF1ZXJ5VGhlbkZldGNoAgAAAAAF-0fRFkhYNzFBb1loU1dLbVpicWpmSTl3b1EAAAAABftH0hZIWDcxQW9ZaFNXS21aYnFqZkk5d29R"`\
`}'`\
\
And then grab the scroll\_id from that results and iterate.
