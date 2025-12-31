# Project Structure

```
kwikpos-api/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/kwikpos/api/
│   │   │       ├── controller/      # REST controllers
│   │   │       ├── service/         # Business logic
│   │   │       ├── mapper/          # Mapper interface methods (SQL Queries)
│   │   │       ├── model/           # Data entity models
│   │   │       ├── dto/             # Data transfer objects
│   │   │       └── config/          # Configuration classes
│   │   └── resources/
│   │       ├── application.properties
│   │       ├── application-dev.properties
│   │       ├── application-production.properties
│   │       └── templates/           # Templates if any
│   └── test/                        # Unit and integration tests
├── pom.xml                          # Maven configuration
└── README.md
```

## Package Overview

### controller/
REST controllers that handle HTTP requests from kiosks. Endpoints are designed to receive order data in modern formats.

### service/
Business logic layer that handles order transformation and POS communication. This is where the adapter logic resides.

### mapper/
MyBatis mapper interfaces defining SQL queries for database operations with both the order database and POS database.

### model/
Entity models representing both modern order structures and legacy POS data structures.

### dto/
Data Transfer Objects for API requests and responses, handling the translation between kiosk format and POS format.

### config/
Configuration classes for Spring Boot, database connections, security, and integration settings.
