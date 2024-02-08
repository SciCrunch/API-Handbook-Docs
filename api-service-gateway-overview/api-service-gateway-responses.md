---
description: Overview of API Service Gateway Responses
---

# API Service Gateway Responses

Responses from API services available via the API Gateway will generally be in JSON format. If a service utilizes a different response format that will be documented with that specific service.

## CORS Support

Services provide support for Cross-Origin Resource Sharing (CORS). CORS is a mechanism that allows restricted resources on a web page to be accessed from another domain outside the domain from which the first resource was served ([https://en.wikipedia.org/wiki/Cross-origin\_resource\_sharing](https://en.wikipedia.org/wiki/Cross-origin\_resource\_sharing))

{% code overflow="wrap" %}
```bash
curl -X OPTIONS --verbose --location 'https://api.scicrunch.io/elastic/v1/_cat/aliases' --header 'apikey: <<YOUR API KEY>>'
```
{% endcode %}

```
*   Trying 52.89.161.7:443...
* Connected to api.scicrunch.io (52.89.161.7) port 443
* ALPN: curl offers h2,http/1.1
* Cipher selection: ALL:!EXPORT:!EXPORT40:!EXPORT56:!aNULL:!LOW:!RC4:@STRENGTH
* TLSv1.2 (OUT), TLS handshake, Client hello (1):
*  CAfile: /etc/pki/tls/certs/ca-bundle.crt
*  CApath: none
* TLSv1.2 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS handshake, Certificate (11):
* TLSv1.2 (IN), TLS handshake, Server key exchange (12):
* TLSv1.2 (IN), TLS handshake, Server finished (14):
* TLSv1.2 (OUT), TLS handshake, Client key exchange (16):
* TLSv1.2 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (OUT), TLS handshake, Finished (20):
* TLSv1.2 (IN), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (IN), TLS handshake, Finished (20):
* SSL connection using TLSv1.2 / ECDHE-ECDSA-AES128-GCM-SHA256
* ALPN: server accepted http/1.1
* Server certificate:
*  subject: CN=api.scicrunch.io
*  start date: Feb  2 22:02:47 2024 GMT
*  expire date: May  2 22:02:46 2024 GMT
*  subjectAltName: host "api.scicrunch.io" matched cert's "api.scicrunch.io"
*  issuer: C=US; O=Let's Encrypt; CN=R3
*  SSL certificate verify ok.
* using HTTP/1.1
> OPTIONS /elastic/_cat/aliases HTTP/1.1
> Host: api.scicrunch.io
> User-Agent: curl/8.3.0
> Accept: */*
> apikey: <<YOUR API KEY>>
> 
< HTTP/1.1 200 OK
< Server: openresty/1.25.3.1
< Date: Tue, 06 Feb 2024 02:08:25 GMT
< Content-Type: application/json
< Content-Length: 0
< Connection: keep-alive
< Access-Control-Allow-Origin: *
< Access-Control-Allow-Methods: GET, POST, OPTIONS, HEAD
< Access-Control-Allow-Headers: Authorization, Origin, X-Requested-With, Content-Type, Accept
< 
* Connection #0 to host api.scicrunch.io left intact

```
