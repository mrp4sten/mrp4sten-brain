Tags: 
- [[Java]]
- [[0 Spring Boot]]
- [[Software Engingeering/Spring Boot/5. Microservices/Spring Cloud/0 Introduction]]

# Spring Cloud Gateway

Spring Cloud Gateway is a Spring Framework library for building API gateways. An API gateway is a service that acts as an intermediary between an application and a set of microservices. The API gateway is responsible for request routing, composition, and protocol translation, among other things. It can also perform tasks such as authentication, rate limiting, and caching.

Spring Cloud Gateway is built on top of the Spring Framework and Spring Boot, and it integrates with other Spring projects such as Spring Cloud Netflix and Spring Security. It provides a simple, yet powerful way to route and manage requests to microservices, allowing developers to focus on business logic instead of writing boilerplate code to handle common API gateway tasks.

```java
@SpringBootApplication
public class DemogatewayApplication {
	@Bean
	public RouteLocator customRouteLocator(RouteLocatorBuilder builder) {
		return builder.routes()
			.route("path_route", r -> r.path("/get")
				.uri("http://httpbin.org"))
			.route("host_route", r -> r.host("*.myhost.org")
				.uri("http://httpbin.org"))
			.route("rewrite_route", r -> r.host("*.rewrite.org")
				.filters(f -> f.rewritePath("/foo/(?<segment>.*)", "/${segment}"))
				.uri("http://httpbin.org"))
			.route("hystrix_route", r -> r.host("*.hystrix.org")
				.filters(f -> f.hystrix(c -> c.setName("slowcmd")))
				.uri("http://httpbin.org"))
			.route("hystrix_fallback_route", r -> r.host("*.hystrixfallback.org")
				.filters(f -> f.hystrix(c -> c.setName("slowcmd").setFallbackUri("forward:/hystrixfallback")))
				.uri("http://httpbin.org"))
			.route("limit_route", r -> r
				.host("*.limited.org").and().path("/anything/**")
				.filters(f -> f.requestRateLimiter(c -> c.setRateLimiter(redisRateLimiter())))
				.uri("http://httpbin.org"))
			.build();
	}
}

```