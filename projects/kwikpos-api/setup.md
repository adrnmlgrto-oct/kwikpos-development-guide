# Development Environment Setup

## Prerequisites

Refer to [Prerequisites](../../prerequisites.md) for detailed requirements. For KwikPOS API, you need:

- OpenJDK 17 (*Zulu*)
- Maven 3.8+
- Apache Tomcat 10.0 (for local testing)
- Git

## Local Setup Steps

### 1. Clone the Repository

```bash
git clone https://github.com/oct-ph/kwikpos-legacy-adapter.git
cd kwikpos-legacy-adapter
```

### 2. Configure Application

Edit `application-dev.properties` file and configure settings for schemas:

```properties
spring.datasource.username=springboot
spring.datasource.password=<PASSWORD_HERE>

mybatis.configuration-properties.orderdb-schema=orderdb
mybatis.configuration-properties.posdb-schema=posdb

app.storage.local.base-path=D:/KwikPOS API/media/files
```

### 3. Build the Project

```bash
mvn clean install
```

### 4. Run Locally

```bash
# Using Spring Boot
mvn spring-boot:run

# Or deploy WAR to local Tomcat 10
cp target/kwikpos-legacy-adapter.war /path/to/tomcat10/webapps/
```

!!! note "Note:"
    When running the embedded tomcat server for local development, this project is special as it has this funcationality of **hot-reload** whenever code gets saved.

### 5. Verify Installation

- Access via:
    - http://localhost:8083
    - http://localhost:8083/swagger-ui/index.html (Swagger UI)
- Test API endpoints using Postman
- Verify kiosk connectivity

## Additional Resources

- Spring Boot 3.5.4 Documentation
- Apache Tomcat 10.0 Documentation
- Kiosk API Specification
