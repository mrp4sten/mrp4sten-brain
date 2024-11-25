Tags: 
- [[Java]]
- [[0 Spring Boot]]
- [[Software Engingeering/Spring Boot/5. Microservices/Spring Cloud/0 Introduction]]
# Circuit Breaker

Spring Cloud Circuit Breaker is a library for managing the fault tolerance of microservices-based applications using the Circuit Breaker pattern. The Circuit Breaker pattern is a design pattern that helps to prevent cascading failures and improve the resilience of distributed systems. It does this by introducing a “circuit breaker” proxy in front of a service that can detect when the service is unresponsive or has failed, and stop routing traffic to it temporarily, in order to allow the service to recover.