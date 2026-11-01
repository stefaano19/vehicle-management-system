# GestionaleAuto

GestionaleAuto is a Spring Boot REST API for managing dealership operations. It covers vehicles and showroom stock, customers, appointments, manufacturers, suppliers and products, quotes, purchase and sales orders, invoices, and user registration and login.

This repository contains the backend only; it does not include a web or mobile frontend.

## Technology

- Java 17
- Spring Boot 3.0.9-SNAPSHOT
- Spring MVC, Spring Data JPA, and Spring Security
- PostgreSQL
- Maven, using the included Maven Wrapper
- JUnit 5 and Spring Boot Test

## Requirements

- JDK 17
- PostgreSQL

## Configure and run

1. Create a PostgreSQL database named `gestionaleAuto` (PostgreSQL treats this unquoted name as lowercase):

   ```sql
   CREATE DATABASE gestionaleauto;
   ```

2. Set the database connection for your local environment. Spring Boot reads these environment variables and uses them in preference to the datasource values in `src/main/resources/application.yaml`:

   ```sh
   export SPRING_DATASOURCE_URL=jdbc:postgresql://localhost:5432/gestionaleAuto
   export SPRING_DATASOURCE_USERNAME=postgres
   export SPRING_DATASOURCE_PASSWORD=your-local-password
   ```

   The checked-in configuration contains fixed connection settings; override them for your environment and do not use local defaults for a shared or publicly accessible deployment. Do not commit real credentials.

3. Start the API:

   ```sh
   ./mvnw spring-boot:run
   ```

   On Windows, use `mvnw.cmd spring-boot:run`. The server uses Spring Boot's default port, `8080`, unless configured otherwise.

The API controllers are grouped under `/auto`, `/clienti`, `/appuntamenti`, `/caseProduttrici`, `/fornitori`, `/prodotti`, `/preventivi`, `/ordini`, `/fatture`, `/utenti`, and `/home`. Inspect the controller classes in `src/main/java/com/example/gestionaleauto/controllers` for available operations and request parameters.

## Tests

Run the test suite with:

```sh
./mvnw test
```

The current test suite includes a Spring application-context smoke test. PostgreSQL must be available and configured for that test to start successfully.

## Security note

Although registration and login endpoints are present, the current security configuration permits all requests. Treat this project as a development application unless request authorization and deployment security are configured appropriately.
