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
```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
```
In this case, the server sent the response telling us that the request was authorized and that any origin could make this request.

> This only happens when the request is called as simple request. When the there's a pre-flight request, it'll have two requests:  the pre-flight request and the request itself

## Example Pre Flight

Imagine the request:
```
GET /resource HTTP/1.1
Host: bar.other
//...
Origin: http://foo.example
```
Now, instead of executing the request itself, at first, a pre-flight request would be made:
```
OPTIONS /resource HTTP/1.1
Origin: http://foo.example
Access-Control-Request-Method: POST
Access-Control-Request-Headers: X-PINGOTHER, Content-Type
```
The response should be something like it:
```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
Access-Control-Max-Age: 86400
```
And then the real request would be made.