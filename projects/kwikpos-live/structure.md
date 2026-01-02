# Project Structure

```
kwikpos-live-legacy-backend/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/oneclicktech/spring/
│   │   │       ├── component/          # Component classes
│   │   │       ├── config/             # Configuration classes
│   │   │       ├── controller/         # REST controllers
│   │   │       ├── dto/                # Data transfer objects
│   │   │       ├── enums/              # Enum objects
│   │   │       ├── login/              # Authentication & security classes
│   │   │       ├── mapper/             # Mapper interface methods
│   │   │       ├── model/              # Entity models and constants
│   │   │       └── service/            # Business logic
│   │   │
│   │   └── resources/
│   │       ├── application.properties
│   │       └── email_templates/        # Templates for email services
│   │
│   └── test/                           # Unit and integration tests
├── pom.xml                             # Maven configuration
└── README.md
```

## Package Overview

### component/
Component classes for cross-cutting concerns and utilities that can be injected and reused across the application.

### config/
Configuration classes for Spring Boot, security, database connections, and other application settings.

### controller/
REST controllers that handle HTTP requests and responses. Each controller typically corresponds to a specific domain or feature area.

### dto/
Data Transfer Objects used for API requests and responses, separating internal models from external representations.

### enums/
Enum objects that define fixed sets of constants used throughout the application for type-safe value representation.

### login/
Authentication and security classes that handle user login, session management, and security-related functionality.

### mapper/
MyBatis mapper interfaces that define SQL query methods for database operations.

### model/
Entity models representing database tables and constant values used throughout the application.

### service/
Business logic layer that implements the core functionality. Services are called by controllers and interact with mappers.
