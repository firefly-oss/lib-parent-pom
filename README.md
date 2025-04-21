# Firefly Library Parent POM

This repository contains the parent POM for all Firefly platform libraries. It provides standardized dependency management, plugin configurations, and build processes to ensure consistency across all Firefly library projects.

## Purpose

The `lib-parent-pom` serves as a centralized configuration point for all Firefly libraries, offering:

- Consistent dependency versions
- Standardized build processes
- Common plugin configurations
- Unified code quality standards
- Streamlined deployment procedures

By using this parent POM, development teams can focus on implementing business logic rather than configuring build tools and managing dependencies.

## Requirements

- Java 21
- Maven 3.8+
- GitHub account with access to Firefly repositories

## Usage

### Adding as Parent to Your Project

To use this parent POM in your library project, add the following to your `pom.xml`:

```xml
<parent>
    <groupId>com.catalis</groupId>
    <artifactId>lib-parent-pom</artifactId>
    <version>1.0.0-SNAPSHOT</version>
</parent>
```

### Inheriting Managed Dependencies

The parent POM provides dependency management for commonly used libraries. To use a managed dependency, simply declare it in your project's `dependencies` section without specifying the version:

```xml
<dependencies>
    <!-- Spring Boot Starter -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-webflux</artifactId>
    </dependency>

    <!-- Other dependencies -->
</dependencies>
```

## Key Features

### Spring Boot and Spring Cloud Integration

The parent POM includes Spring Boot 3.2.2 and Spring Cloud 2023.0.0, providing a solid foundation for building microservices.

### Database Support

Built-in support for:
- PostgreSQL (JDBC and R2DBC)
- Flyway for database migrations

### API Documentation

OpenAPI/Swagger integration for API documentation with standardized configuration.

### Development Tools

- Lombok for reducing boilerplate code
- MapStruct for object mapping
- Standardized annotation processor configuration

### Testing Framework

Comprehensive testing support with:
- JUnit Jupiter
- Mockito
- Testcontainers for integration testing

## Configuration Options

### OpenAPI Configuration

The parent POM provides default OpenAPI configuration properties:

```properties
openapi.skip.validate=false
openapi.use.tags=true
openapi.use.optional=true
openapi.date.library=java8
```

### Project Structure

Default package structure is configured as:

```properties
base.package=com.catalis
openapi.base.package=${base.package}.${project.artifactId}
openapi.model.package=${openapi.base.package}.interfaces.dto
openapi.api.package=${openapi.base.package}.interfaces.api
```

## Build and Deployment

The parent POM configures the following build and deployment processes:

### Source and Javadoc Attachment

Source and Javadoc JARs are automatically generated and attached to the build artifacts.

### GitHub Packages Deployment

The project is configured to deploy to GitHub Packages. The CI/CD workflow is defined in `.github/workflows/publish.yml`.

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Create a new Pull Request