# Download Larger Datasets

If you are new to our API service, we recommend starting with “[Getting Started with the APIs](../../api-service-gateway-overview/getting-started-with-sparc-apis.md)” and “[Using your API key](../../api-service-gateway-overview/using-your-api-key.md)” for helpful guidance first. If you have any questions, please do not hesitate to contact us.\
\
With a large number of records to download you would not be able to do that via a simple Elasticsearch search as Elasticsearch's paging limit is 10,000 records. Therefore, you need to use Elasticsearch's scroll mechanism. An example of such a curl request would be (Note: for normal queries you would not add the ?scroll=1s to the end):\
\
**Initialize Download of an Entire Index**\
\
To download an entire index from the API, you start the scrolling process with the following curl command:

`curl --location 'https://api.scicrunch.io/elastic/v1/<<YOUR TARGET INDEX>>/_search?scroll=1s' \`\
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
The initial scroll query would yield results such as:\
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
To download additional content you would need to download the next set of results.  To do this,  use the scroll\_id from the prior result and create a new request:\
\
`curl --location 'https://api.scicrunch.io/elastic/v1/_search/scroll' \`\
`--header 'Content-Type: application/json' \`\
`--header 'apikey: <<YOUR API KEY>>' \`\
`--data '{`\
`"scroll" : "1s",`\
`"scroll_id" : "DnF1ZXJ5VGhlbkZldGNoAgAAAAAF-0fRFkhYNzFBb1loU1dLbVpicWpmSTl3b1EAAAAABftH0hZIWDcxQW9ZaFNXS21aYnFqZkk5d29R"`\
`}'`\
\
This will generate a set of results with a **new** scroll\_id. Use this new scroll\_id to generate a new request and repeat...
