# Deployment Architecture

## Infrastructure

- **Hosting:** AWS EC2 instance
- **Application Server:** Apache Tomcat 9.0 servlet container
- **Database:** Direct MySQL 8.0 database connection

## Deployment Pipeline

### Current Method
Legacy manual WAR deployment

### Process

1. Build WAR file using Maven
2. Manual upload to EC2 instance
3. Deploy to Tomcat webapps directory
4. Restart Tomcat service

## Configuration

- Environment-specific configuration files
- Database connection pooling
- Security settings and credentials management
