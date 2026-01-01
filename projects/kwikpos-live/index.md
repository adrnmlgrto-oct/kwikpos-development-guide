# KwikPOS Live (Backend)

**Purpose:** Cloud web application backend serving multiple tenant stores and branches

KwikPOS Live is the central cloud-based backend system that aggregates and manages data from multiple POS terminals across different client stores and branches. It serves as the data hub for sales analytics, reporting, and multi-tenant management.

## Tech Stack

- **Framework:** Spring Boot 2.7.2
- **Runtime:** Java 8 (planned upgrade to newer version)
- **Database:** MySQL 8.0
- **Deployment:** Apache Tomcat 9.0 on AWS EC2
- **Deployment Method:** Manual WAR file updates

## Database Configuration

### Database Schema

- **Database Name:** `kwikpos_live_legacy`
- **User:** `root` (for local development)
- **Password:** Uses your local MySQL root user password

When running the project locally, the application will connect to the `kwikpos_live_legacy` database using the root user credentials configured on your local MySQL installation.

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

## Quick Links

- [Responsibilities](responsibilities.md) - Core system responsibilities
- [Deployment Architecture](deployment.md) - Infrastructure and deployment details
- [Development Setup](setup.md) - Local environment configuration
- [Project Structure](structure.md) - Code organization and architecture
- [Development Tasks](development.md) - Common development workflows
- [Testing](testing.md) - Testing strategies and practices
- [Troubleshooting](troubleshooting.md) - Common issues and solutions
- [Roadmap & Planned Work](roadmap.md) - Future features and integrations

## Getting Help

If you encounter issues:

- **Technical Questions:** Reach out to the development team
- **Database Issues:** Contact Sophie
- **Deployment Problems:** Contact Sophie
- **Architecture Questions:** Review existing codebase patterns or consult senior developers
