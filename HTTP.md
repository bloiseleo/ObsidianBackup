### CORS
CORS means Cross-Origin Resource Sharing. This defines the policy of content sharing and if some client in some origin can make requests for resources in a different origin. We can define `cross-origin` as a request that was made from an origin to another origin. An origin is composed of domain, protocol and port. So, if we have a website running on `http://localhost:8000` and it makes requests to `http://localhost:8001`, this request is called `cross-origin`.

By Default, the requests cannot be `cross-origin`, which means that you can only request resources for your own website. Besides, the client app must sent a pre-flight request asking for permission when the request's method is different than GET or POST with MIME TYPES. After the pre-flight approve, the real request is made. Credentials can also be specified if they're going to be sent.
## Example
Imagine the request:
```
GET /resource HTTP/1.1
Host: bar.other
//...
Origin: http://foo.example
```
The origin is used by the server to determine if the origin is allowed. This is determined by the response header `Access-Control-Allow-Origin`. 