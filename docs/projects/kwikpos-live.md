# KwikPOS Live (Backend)

## Overview

**Purpose:** Cloud web application backend serving multiple tenant stores and branches

KwikPOS Live is the central cloud-based backend system that aggregates and manages data from multiple POS terminals across different client stores and branches. It serves as the data hub for sales analytics, reporting, and multi-tenant management.

## Tech Stack

- **Framework:** Spring Boot 2.7.2
- **Runtime:** Java 8 (planned upgrade to newer version)
- **Database:** MySQL 8.0
- **Deployment:** Apache Tomcat 9.0 on AWS EC2
- **Deployment Method:** Manual WAR file updates

## Key Features

### Multi-Tenant Architecture
- Support for multiple clients with their branches and terminals
- Centralized data aggregation from individual POS terminals
- Tenant isolation and data security

### Data Management
- Sales data consolidation with flexible filtering
  - Company-wide reports
  - Branch-specific analysis
  - Store-specific metrics
- Real-time data synchronization from POS terminals

### Analytics & Reporting
- Sales performance analytics
- Comprehensive reporting dashboard
- Historical data analysis
- Custom report generation

### API Services
- RESTful API endpoints for POS terminal communication
- Secure data retrieval for web dashboard
- Authentication and authorization mechanisms

## Responsibilities

1. **Data Reception**
    - Accepts data from POS terminals across all client stores via REST API
    - Validates and processes incoming sales records
    - Handles real-time data synchronization

2. **Data Storage**
    - Serves as the central data repository for sales records
    - Maintains data integrity and consistency
    - Provides efficient data retrieval mechanisms

3. **Backend Services**
    - Provides backend services for the KwikPOS Live web application
    - Handles business logic for multi-tenant operations
    - Manages user authentication and authorization

4. **Analytics Processing**
    - Processes data for sales analytics and reporting
    - Generates aggregated statistics
    - Supports complex querying and filtering

## Deployment Architecture

### Infrastructure
- **Hosting:** AWS EC2 instance
- **Application Server:** Apache Tomcat 9.0 servlet container
- **Database:** Direct MySQL 8.0 database connection

### Deployment Pipeline
- **Current Method:** Legacy manual WAR deployment
- **Process:**
    1. Build WAR file using Maven
    2. Manual upload to EC2 instance
    3. Deploy to Tomcat webapps directory
    4. Restart Tomcat service

### Configuration
- Environment-specific configuration files
- Database connection pooling
- Security settings and credentials management

## Development Environment Setup

### Prerequisites

Refer to [Prerequisites](../prerequisites.md) for detailed requirements. For KwikPOS Live, you need:

- JDK 8
- Maven 3.6+
- MySQL 8.0
- Apache Tomcat 9.0 (for local testing)
- Git

### Local Setup Steps

1. **Clone the Repository**

        git clone https://github.com/oct-ph/kwikpos-live-legacy-backend.git
        cd kwikpos-live-legacy-backend

2. **Request for the Dumped Data for Local Testing then Import via MySQL Workbench 8.0**

3. **Update Configuration**

    - Edit the `application.properties` file
    - Configure database connection:

            spring.datasource.url=jdbc:mysql://localhost:3306/kwikpos_live_legacy
            spring.datasource.username=your_username
            spring.datasource.password=your_password

4. **Build the Project**

        mvn clean install

5. **Run Locally**

        # Using Spring Boot
        mvn spring-boot:run

6. **Verify Installation**

    - Access http://localhost:8080 (or configured port)
    - Test API endpoints using Postman

## Project Structure

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

## Common Development Tasks

### Adding New Features
1. Create feature branch from main, separated by dashes. (ex. `feature-add-something`)
2. Implement changes following existing patterns
3. Write unit tests
4. Test locally with MySQL database
5. Submit pull request for code review

### Database Changes
1. Create migration SQL DDL scripts
2. Test on local database
3. Document changes
4. Coordinate with team for production deployment

### API Development
1. Define endpoint in appropriate controller
2. Implement service layer logic
3. Add repository methods if needed
4. Document API using comments or Swagger
5. Test with Postman

## Testing

### Local Testing
```bash
# Run all tests
mvn test

# Run specific test class
mvn test -Dtest=YourTestClass

# Run integration tests
mvn verify
```

### Manual Testing
- Use Postman collections for API testing
- Test multi-tenant scenarios
- Verify data consistency

## Troubleshooting

### Common Issues

**Build Failures**
- Verify JDK 8 is active: `java -version`
- Clean Maven cache: `mvn clean`
- Update dependencies: `mvn dependency:resolve`

**Database Connection Issues**
- Check MySQL service is running
- Verify credentials in `application.properties`
- Ensure database exists

**Tomcat Deployment Issues**
- Check Tomcat logs in logs/catalina.out
- Verify WAR file is not corrupted
- Ensure port 8080 (*or the configured port*) is available

## Additional Resources

- Spring Boot 2.7.2 Documentation
- MySQL 8.0 Reference Manual
- Apache Tomcat 9.0 Documentation
- Internal API documentation (if available)

## Getting Help

If you encounter issues:

- **Technical Questions:** Reach out to the development team
- **Database Issues:** Contact Sophie
- **Deployment Problems:** Contact Sophie
- **Architecture Questions:** Review existing codebase patterns or consult senior developers
