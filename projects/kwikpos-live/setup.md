# Development Environment Setup

## Prerequisites

Refer to [Prerequisites](../../prerequisites.md) for detailed requirements. For KwikPOS Live, you need:

- JDK 8
- Maven 3.6+
- MySQL 8.0
- Apache Tomcat 9.0 (for local testing)
- Git

## Local Setup Steps

### 1. Clone the Repository

```bash
git clone https://github.com/oct-ph/kwikpos-live-legacy-backend.git
cd kwikpos-live-legacy-backend
```

### 2. Request for the Dumped Data for Local Testing then Import via MySQL Workbench 8.0

### 3. Update Configuration

Edit the `application.properties` file and configure database connection:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/kwikpos_live_legacy
spring.datasource.username=your_username
spring.datasource.password=your_password
```

### 4. Build the Project

```bash
mvn clean install
```

### 5. Run Locally

```bash
# Using Spring Boot
mvn spring-boot:run
```

### 6. Verify Installation

- Access via
    - http://localhost:8082
- Test API endpoints using Postman

## Additional Resources

- Spring Boot 2.7.2 Documentation
- MySQL 8.0 Reference Manual
- Apache Tomcat 9.0 Documentation
- Internal API documentation (if available)
