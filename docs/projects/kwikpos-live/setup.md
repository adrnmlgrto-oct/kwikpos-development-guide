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

### 2. Request for the Application Properties File

The project utilizes an `application.properties` file which holds all of the necessary project configurations. The spring boot application will not run without this.

We additionally excluded this from source control as it doesn't use profiles unlike the project for KwikPOS API.

### 3. Request for the Dumped Data for Local Testing then Import via MySQL Workbench 8.0

This step would be crucial in order to setup your own database to use for local development and testing.

!!! warning "Warning:"
    Avoid testing in production environment.

### 4. Update Configuration

Edit the `application.properties` file and configure database connection:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/kwikpos_live_legacy
spring.datasource.username=your_username
spring.datasource.password=your_password
```

!!! warning "Warning:"
    Do **not** commit and push the `application.properties` in source control for this project as it contains sensitive keys and etc. unlike the KwikPOS API project which uses profile-specific properties files.

### 5. Build the Project

```bash
mvn clean install
```

### 6. Run Locally

```bash
# Using Spring Boot
mvn spring-boot:run
```

### 7. Verify Installation

- Access via
    - http://localhost:8082
- Test API endpoints using Postman

## Additional Resources

- Spring Boot 2.7.2 Documentation
- MySQL 8.0 Reference Manual
- Apache Tomcat 9.0 Documentation
- Internal API documentation (if available)
