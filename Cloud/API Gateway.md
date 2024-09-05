An API Gateway is an infrastructure which aims to manage the access to one or more APIs. Every request that is directed to these APIs goes through the API Gateway. Then, the API Gateway can execute some routines before redirecting the request and its content to the real API.
## Cool Features
- An API Gateway can also act as a Load Balancer. This way, your application will be more reliable than it would be if all the requests went directly to it.
- An API Gateway can perform authentication and authorization. This way, your application can be more secure.
- Your application doesn't need to be exposed to the public internet. It can be inside a private network while the API Gateway is exposed to the public surface. In this way, the application will be more safe.
## Open Source Examples
- Kong: This is an Open Source API Gateway which extends Nginx to work also as an API Gateway and a load balancer.
- KrakenD: Another API Gateway example which aims to be scalable.
- Traefik: Besides being scalable, this software has an automatic service discovery in which it will discover and auto setup your API 