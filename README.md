#### Introduction
This README outlines the setup and use of Service Discovery within a microservices architecture. Service Discovery allows services to find and communicate with each other without hard-coding hostname and port numbers. We'll use Netflix Eureka as our service discovery server.

#### Prerequisites
- JDK 1.8 or later
- Maven 3.2+
- Spring Boot 2.x
- Basic understanding of microservices

#### Setup and Installation
1. **Create Eureka Server:** Generate a Spring Boot application and include the 'Eureka Server' dependency.
   - Annotate the main application class with `@EnableEurekaServer`.
2. **Configure application.properties** for the Eureka server.
   ```properties
   server.port=8761
   eureka.client.register-with-eureka=false
   eureka.client.fetch-registry=false
   ```
3. **Create Eureka Client Services:** For each microservice, include the 'Eureka Client' dependency.
   - Annotate the main class with `@EnableEurekaClient`.
4. **Configure application.properties** for each client to register with Eureka.
   ```properties
   eureka.client.serviceUrl.defaultZone=http://localhost:8761/eureka/
   ```
5. **Run the Eureka Server and Microservices:** Start the Eureka server first, then the microservices.

#### Testing
- Access the Eureka Dashboard at `http://localhost:8761` to see registered services.
- Test inter-service communication through service discovery.

#### Best Practices
- Secure the Eureka dashboard and client communications.
- Use Spring Cloud LoadBalancer for client-side load balancing.
- Monitor and manage services with Spring Boot Actuator.
