# KwikPOS API (Ordering Kiosk to Legacy POS Data Adapter)

## Overview

**Purpose:** Bridge layer connecting self-ordering kiosks to legacy POS applications

KwikPOS API serves as an on-premise adapter that enables modern self-ordering kiosks to communicate seamlessly with legacy POS applications, particularly Chase POS, without requiring modifications to the existing POS software.

## Tech Stack

- **Framework:** Spring Boot 3.5.4
- **Runtime:** Java 17
- **Deployment:** Apache Tomcat 10.0
- **Deployment Location:** On-premise POS machine

## Key Features

### Kiosk Integration
- API server for self-ordering kiosk integration
- Real-time order transmission from kiosks to POS terminals
- Support for modern kiosk interfaces

### Data Transformation
- Data transformation layer between modern kiosks and legacy POS systems
- Format conversion and data mapping
- Protocol adaptation

### Legacy POS Compatibility
- Compatibility layer for Chase POS integration
- Direct integration with legacy POS applications

### Local Server
- Runs as local server on POS machine
- Handles requests from nearby kiosks
- Low-latency local network communication

## Responsibilities

1. **Order Reception**
    - Receives order requests from self-ordering kiosks
    - Validates incoming order data
    - Handles multiple concurrent kiosk connections

2. **Data Transformation**
    - Transforms order data from modern format to legacy POS format
    - Maps fields and data structures
    - Ensures data compatibility

3. **POS Communication**
    - Transmits orders to the connected POS terminal
    - Handles POS-specific protocols
    - Manages error responses and retries

4. **Bridge Layer**
    - Serves as the communication bridge between modern ordering interfaces and legacy systems
    - Maintains session state
    - Provides logging and monitoring

## Deployment Architecture

### Infrastructure
- **Location:** Installed on individual POS machines acting as local servers
- **Application Server:** Apache Tomcat 10.0 servlet container
- **Network:** Local network access for nearby kiosks
- **Integration:** Direct connection with Chase POS application
- **Database:** Direct MS SQL Server database connection

### Deployment Characteristics
- **Scope:** Single store deployment
- **Isolation:** Each installation serves one POS terminal
- **Network:** Local LAN communication (`0.0.0.0`)
- **Availability:** Must be running whenever kiosks are operational

### Configuration
- POS machine-specific settings
- Kiosk connection parameters
- Legacy POS integration settings
- Network and security configuration

## Development Environment Setup

### Prerequisites

Refer to [Prerequisites](../prerequisites.md) for detailed requirements. For KwikPOS API, you need:

- OpenJDK 17 (*Zulu*)
- Maven 3.8+
- Apache Tomcat 10.0 (for local testing)
- Git

### Local Setup Steps

1. **Clone the Repository**

        git clone https://github.com/oct-ph/kwikpos-legacy-adapter.git
        cd kwikpos-legacy-adapter

2. **Configure Application**

    - Edit `application-dev.properties` file.
    - Configure settings for schemas:

            spring.datasource.username=springboot
            spring.datasource.password=<PASSWORD_HERE>

            mybatis.configuration-properties.orderdb-schema=orderdb
            mybatis.configuration-properties.posdb-schema=posdb

            app.storage.local.base-path=D:/KwikPOS API/media/files

3. **Build the Project**

        mvn clean install

4. **Run Locally**

        # Using Spring Boot
        mvn spring-boot:run

        # Or deploy WAR to local Tomcat 10
        cp target/kwikpos-api.war /path/to/tomcat10/webapps/

5. **Verify Installation**

    - Access http://localhost:8080 (or configured port)
    - Test API endpoints using Postman
    - Verify kiosk connectivity

## Project Structure

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

## Common Development Tasks

### Adding New Kiosk Features
1. Create feature branch from main
2. Implement endpoint in controller
3. Add transformation logic if needed
4. Test with mock kiosk requests
5. Submit pull request for code review

### Enhancing POS Integration
1. Identify required POS functionality
2. Implement adapter logic
3. Add transformation for new data types
4. Test with actual POS system if available
5. Document integration details

### Testing Integration
1. Mock kiosk requests using Postman
2. Test data transformation accuracy
3. Verify POS communication (if test system available)
4. Check error handling scenarios

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
- Use Postman to simulate kiosk orders
- Test different order types and configurations
- Verify error handling
- Check transformation accuracy

### Integration Testing
- Test with actual kiosk if available
- Verify POS system receives correct data
- Test concurrent order handling
- Check system performance under load

## Troubleshooting

### Common Issues

**Build Failures**
- Verify JDK 17 is active: `java -version`
- Clean Maven cache: `mvn clean`
- Update dependencies: `mvn dependency:resolve`

**Connection Issues**
- Verify kiosk can reach the API server
- Check firewall settings
- Ensure correct port configuration
- Test network connectivity

**POS Integration Issues**
- Verify POS system is running
- Check POS connection settings
- Review transformation logic
- Check POS system logs

**Tomcat Deployment Issues**
- Ensure using Tomcat 10.0 (not 9.0)
- Check Tomcat logs in logs/catalina.out
- Verify WAR file compatibility
- Ensure port is available

## Main Highlight

**This adapter enables our modern self-ordering kiosk products to seamlessly communicate with legacy POS applications, particularly Chase POS, and possibly other POS applications if requested.**

This is the key value proposition:

- Modern kiosk interface maintained
- Seamless integration
- Minimal disruption to existing operations

## Architecture Considerations

### Stateless Design
- Each request is independent
- No session persistence required
- Horizontal scaling possible if needed

### Error Handling
- Robust error handling for POS failures
- Retry mechanisms for transient errors
- Clear error messages to kiosks

### Performance
- Low-latency requirements
- Efficient data transformation
- Minimal processing overhead

### Security
- Local network security
- Input validation
- Secure POS communication

## Additional Resources

- Spring Boot 3.5.4 Documentation
- Apache Tomcat 10.0 Documentation
- Kiosk API Specification

## Getting Help

If you encounter issues:

- **Technical Questions:** Reach out to the development team, or you may contact the original author of the codebase via email (<a href="mailto:adrnmlgrto.dev@gmail.com" target="_blank">adrnmlgrto.dev@gmail.com</a>)
- **Integration Issues:** Consult with technical support or helpdesk
- **Deployment Problems:** Contact on-site technical support or helpdesk
- **Architecture Questions:** Review adapter patterns or consult senior developers
- **Kiosk Issues:** Check with KwikPOS Pro development team
