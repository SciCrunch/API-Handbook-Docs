# Download Larger Datasets

With a large number of records to download you would not be able to do that via a simple Elasticsearch search as Elasticsearch's paging limit is 10,000 records. Therefore, you need to use Elasticsearch's scroll mechanism. An example of such a curl request would be (Note: for normal queries you would not add the ?scroll=1s to the end):\
\
`curl --location 'https://api.scicrunch.io/elastic/v1/<<YOUR<https://api.scicrunch.io/elastic/v1/%3C%3CYOUR> TARGET INDEX>>/_search?scroll=1s' \`\
`--header 'Content-Type: application/json' \`\
`--header 'apikey: <<YOUR API KEY>>' \`\
`--data '{ <<YOUR QUERY HERE>> }'`\


Note: The above example would download an entire index.  To download specific content you would add a query component to the initial scroll request.

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
