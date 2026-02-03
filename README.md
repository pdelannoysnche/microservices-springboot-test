Objective
The goal of this activity is to strengthen your understanding of distributed architectures using the Spring Boot ecosystem. You are required to build a resilient communication flow between two microservices, ensuring high quality in error handling, documentation, and fault tolerance.

🏗️ System Architecture
You must implement two services:

Order-Service (Port 8080): The main entry point that processes client requests.

Inventory-Service (Port 8081): A secondary service that provides stock availability data.

🛠️ Requirements
1. Communication & Validation
Implement a REST-based communication from Order-Service to Inventory-Service using WebClient or RestTemplate.

Use spring-boot-starter-validation to ensure all incoming DTOs (Data Transfer Objects) are properly validated.

2. Resilience Patterns (Resilience4J)
Implement fault tolerance in the Order-Service when calling the Inventory-Service:

Retry: Attempt the connection at least 3 times before failing.

Circuit Breaker: Open the circuit after 5 consecutive failures to prevent system cascading failure.

Fallback: If the service is unavailable, return a controlled message: "Inventory service is currently unavailable. Please try again later."

3. Error Management & Documentation
Centralized Exception Handling: Implement a @RestControllerAdvice to manage standard HTTP errors (400 Bad Request, 404 Not Found, 500 Internal Error) with a consistent JSON response body.

How to Run and Test
Run the Infrastructure:

Bash
docker-compose up -d
Build the Services:

Bash
./gradlew clean build

API Documentation: Configure SpringDoc OpenAPI (Swagger). The documentation must be accessible at http://localhost:8080/swagger-ui.html.

4. Logging & Configuration
Apply logging best practices (using SLF4J/Logback) to track the flow of requests and circuit breaker state changes.

Externalize configurations using application.yml.
