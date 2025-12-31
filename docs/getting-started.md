# Getting Started with KwikPOS Development

Welcome to the KwikPOS development team! This guide introduces you to our ecosystem of projects and helps you understand what we build and maintain.

## Before You Begin

Before diving into development, make sure you have the necessary knowledge and tools:

- **Review [Prerequisites](prerequisites.md)** - Essential knowledge (Git, Java, Spring Boot, etc.) and required development tools
- Verify you have the appropriate JDK version for your project
- Ensure your development environment is set up correctly

## Project Ecosystem

Our ecosystem consists of cloud-based backend services and on-premise API adapters that work together to provide a complete POS solution. Real-time data syncing enables individual POS applications to communicate with our cloud backend server, consolidating sales records from different client stores and branches.

## Our Projects

We maintain these main projects:

### 1. KwikPOS Live (Backend)
**Cloud-based multi-tenant backend system**

- Central data hub for multiple stores and branches
- Sales analytics and reporting platform
- Built with Spring Boot 2.7.2 (Java 8) and MySQL 8.0
- Deployed on AWS EC2

[View detailed documentation →](projects/kwikpos-live/index.md)

### 2. KwikPOS API (Kiosk-to-POS Adapter)
**On-premise bridge for legacy POS integration**

- Connects modern kiosks to legacy POS systems
- Data transformation layer for Chase POS compatibility
- Built with Spring Boot 3.5.4 (Java 17)
- Deployed on local POS machines

[View detailed documentation →](projects/kwikpos-api/index.md)

### 3. FullyBooked Integration (WebExt)
**Client-specific POS integration for FullyBooked bookstore chain**

- Custom integration between KwikPOS and FullyBooked's IMS system
- Text file-based data import/export (tab-delimited)
- Database-centric with custom SQL views and queries
- Built on MS SQL Server

[View detailed documentation →](projects/kwikpos-fullybooked/index.md)

## Technology Stack Overview

### Backend Technologies
- **Java 8** - KwikPOS Live (with upgrade plans)
- **Java 11** - FullyBooked Integration (likely, but unconfirmed)
- **Java 17** - KwikPOS API
- **Spring Boot 2.7.2** - KwikPOS Live and FullyBooked Integration
- **Spring Boot 3.5.4** - KwikPOS API

### Databases
- **MySQL 8.0** - KwikPOS Live primary database
- **MS SQL Server** - KwikPOS API and FullyBooked integration

### Application Servers
- **Apache Tomcat 9.0** - KwikPOS Live and FullyBooked Integration deployment
- **Apache Tomcat 10.0** - KwikPOS API deployment

### Infrastructure
- **AWS EC2** - Cloud hosting for KwikPOS Live
- **On-Premise** - Local POS machine hosting for KwikPOS API and FullyBooked Integration

## Architecture Comparison

| Aspect | KwikPOS Live | KwikPOS API | FullyBooked (WebExt) |
|--------|--------------|-------------|----------------------|
| **Deployment** | Cloud (AWS EC2) | On-Premise (POS Machine) | On-Premise (FullyBooked POS) |
| **Scope** | Multi-tenant | Single store | Single client (FullyBooked) |
| **Purpose** | Central data hub | Kiosk-POS bridge | POS-IMS integration |
| **Database** | MySQL 8.0 | MS SQL Server | MS SQL Server |
| **Clients** | Multiple tenants | Individual kiosks | FullyBooked stores |
| **Integration** | POS Terminals → Cloud | Kiosks → Legacy POS | POS ↔ IMS (text files) |
| **Java Version** | Java 8 | Java 17 | Java 11 (likely) |
| **Spring Boot** | 2.7.2 | 3.5.4 | 2.7.2 |
| **App Server** | Tomcat 9.0 | Tomcat 10.0 | Tomcat 9.0 |
| **Primary Tech** | Spring Boot API | Spring Boot API | SQL views/queries |

## Your Work Scope

As a developer on the KwikPOS team, you'll work on **multiple projects** depending on the features and requirements. Your work will primarily involve:

### Backend Development
- Building and maintaining RESTful APIs for both KwikPOS Live and KwikPOS API
- Implementing business logic and service layers
- Developing new features and enhancements
- Bug fixes and performance optimization

### Frontend Development
- Working on the **Angular-based frontend** for KwikPOS Live
- Building responsive UI components and pages
- Integrating with backend REST APIs
- Implementing forms, validations, and user interactions
- Managing application state and data flow

### Database Work
A significant portion of your work will involve **writing SQL queries** across multiple database systems:

- **MySQL** - For KwikPOS Live (primary backend database)
- **Microsoft SQL Server** - For KwikPOS API, FullyBooked integration, and legacy system integration
- **SQLite** - For KwikPOS application local storage
- **PostgreSQL** - For Supabase integration

You'll be creating, optimizing, and maintaining SQL queries including:

- Complex `SELECT` queries with joins and aggregations
- `INSERT`, `UPDATE`, `DELETE` operations
- Stored procedures, views, and functions
- Database migrations and schema changes
- Query optimization and indexing

### Full-Stack Responsibilities
- Both cloud-based (KwikPOS Live) and on-premise (KwikPOS API) development
- Multi-tenant architecture implementation
- Legacy system integration and data transformation
- Testing and deployment across different environments

### Client-Specific Integrations
- **FullyBooked Integration** - Custom SQL views, queries, and text file import/export
- Writing and optimizing database views for data extraction
- Creating import procedures for external data sources
- Maintaining integration-specific documentation

## Quick Start Steps

1. **Check Prerequisites**

    - Review the [Prerequisites](prerequisites.md) page
    - Install required tools for both Java 8 and Java 17 development
    - Set up database clients for MySQL, SQL Server, SQLite, and PostgreSQL
    - Verify your development environment

2. **Get Access & Onboarding**

    - Contact your team lead for organization access for the project repositories
    - Request credentials for:
        - AWS access (for KwikPOS Live deployment)
        - Database connections (MySQL, SQL Server, PostgreSQL)
        - On-premise system access (if needed for KwikPOS API testing)

3. **Set Up Both Projects**

    - Clone both repositories:
        - KwikPOS Live (Java 8, Spring Boot 2.7.2)
        - KwikPOS API (Java 17, Spring Boot 3.5.4)
    - Follow setup instructions in respective project documentation:
        - [KwikPOS Live Setup Guide](projects/kwikpos-live/setup.md)
        - [KwikPOS API Setup Guide](projects/kwikpos-api/setup.md)
    - Verify both projects run locally

4. **Familiarize with Database Systems**

    - Set up local MySQL database for KwikPOS Live development
    - Install SQL Server Management Studio or Azure Data Studio
    - Get familiar with SQLite (DB Browser for SQLite)
    - Set up PostgreSQL client for Supabase integration
    - Review existing database schemas and query patterns

5. **Start Developing**

    - Review existing codebase patterns in both projects
    - Understand the database query structure and ORM usage
    - Pick up your first task or ticket
    - Follow team coding standards and SQL best practices

## Development Workflow

1. **Branch Management**

    - Create feature branches from main
    - Use descriptive branch names (e.g., `feature/add-sales-report`)

2. **Code Changes**

    - Follow existing code patterns and conventions
    - Write unit tests for new functionality
    - Test locally before committing

3. **Code Review**

    - Submit pull requests for code review
    - Address review comments, if any are provided

4. **Deployment**

    - Follow project-specific deployment procedures
    - Coordinate with team for production deployments

## Getting Help

If you need assistance:

- **Technical Questions:** Reach out to the development team
- **Access Issues:** Contact your team lead for repository and AWS credentials
- **Architecture Questions:** Review project-specific documentation or consult senior developers
- **Deployment Issues:** Check deployment guides or contact DevOps
- **Prerequisites Help:** See the [Prerequisites](prerequisites.md) page

## Additional Resources

- [Prerequisites Guide](prerequisites.md) - Required knowledge and tools
- [KwikPOS Live Documentation](projects/kwikpos-live/index.md) - Detailed project guide
- [KwikPOS API Documentation](projects/kwikpos-api/index.md) - Detailed project guide
- [KwikPOS Website](https://www.kwikpos.ph) - Product information

---

Welcome to the KwikPOS development team! We're excited to have you on board.
