# Project Structure

```
kwikpos-legacy-adapter/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/oneclicktech/kwikpos_legacy_adapter
│   │   │       ├── component/       # Component classes
│   │   │       ├── config/          # Configuration classes
│   │   │       ├── controller/      # REST controllers
│   │   │       ├── enums/           # Enum objects
│   │   │       ├── mapper/          # Mapper interface methods (SQL Queries)
│   │   │       ├── model/           # Data entity models
│   │   │       ├── security/        # Security configurations
│   │   │       ├── service/         # Business logic
│   │   │       └── utils/           # Global utility classes
│   │   │
│   │   └── resources/
│   │       ├── application.properties
│   │       ├── application-dev.properties
│   │       ├── application-production.properties
│   │       └── static/              # Static asset files (Img, CSS, JS, etc.)
│   │
│   └── test/                        # Unit tests
├── pom.xml                          # Maven configuration
└── README.md
```

## Package Overview

### component/
Component classes for cross-cutting concerns such as automatic BASE URL resolution for deployment environments, scheduled tasks (e.g., clearing pending sales orders after 1 hour), and other reusable utilities.

### config/
Configuration classes for Spring Boot application settings, including async configuration, AWS integration, caching, CORS policies, OpenAPI documentation, task scheduling, and storage backend configurations.

### controller/
REST controllers that handle HTTP requests from kiosks. Endpoints are designed to receive order data in modern formats.

### enums/
Enum objects that define fixed sets of constants used throughout the application for type-safe value representation.

### mapper/
MyBatis mapper interfaces defining SQL queries for database operations with both the order database and POS database.

### model/
Entity models representing both modern order structures and legacy POS data structures.

### security/
Security configuration classes that handle authentication, authorization, and other security-related functionality.

### service/
Business logic layer that handles order transformation and POS communication. This is where the adapter logic resides.

### utils/
Global utility classes that provide helper functions and common functionality across the application, not limited to specific resources.
