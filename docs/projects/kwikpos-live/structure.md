# Project Structure

```
kwikpos-live/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/kwikpos/live/
│   │   │       ├── controller/    # REST controllers
│   │   │       ├── service/       # Business logic
│   │   │       ├── mapper/        # Mapper interface methods
│   │   │       ├── model/         # Entity models and constants
│   │   │       ├── dto/           # Data transfer objects
│   │   │       └── config/        # Configuration classes
│   │   └── resources/
│   │       ├── application.properties
│   │       └── static/            # Static resources
│   └── test/                      # Unit and integration tests
├── pom.xml                        # Maven configuration
└── README.md
```

## Package Overview

### controller/
REST controllers that handle HTTP requests and responses. Each controller typically corresponds to a specific domain or feature area.

### service/
Business logic layer that implements the core functionality. Services are called by controllers and interact with repositories.

### mapper/
MyBatis mapper interfaces that define SQL query methods for database operations.

### model/
Entity models representing database tables and constant values used throughout the application.

### dto/
Data Transfer Objects used for API requests and responses, separating internal models from external representations.

### config/
Configuration classes for Spring Boot, security, database connections, and other application settings.
