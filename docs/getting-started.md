# Getting Started with KwikPOS Development

Welcome to the KwikPOS development team! This guide introduces you to our ecosystem of projects and helps you understand what we build and maintain.

## Project Ecosystem

Our ecosystem consists of cloud-based backend services and on-premise API adapters that work together to provide a complete POS solution. Real-time data syncing enables individual POS applications to communicate with our cloud backend server, consolidating sales records from different client stores and branches.

## Our Projects

### KwikPOS Live (Backend)

**Purpose:** Cloud web application backend serving multiple tenant stores and branches

#### **Tech Stack:**
- **Framework:** Spring Boot 2.7.2
- **Runtime:** Java 8 (planned upgrade to newer version)
- **Database:** MySQL 8.0
- **Deployment:** Apache Tomcat 9.0 on AWS EC2
- **Deployment Method:** Manual WAR file updates

#### **Key Features:**
- Multi-tenant architecture supporting multiple clients with their branches and terminals
- Centralized data aggregation from individual POS terminals
- Sales data consolidation with flexible filtering (company-wide, branch-specific, store-specific)
- Sales performance analytics and reporting
- RESTful API endpoints for POS terminal communication
- Secure data retrieval and display for web dashboard

#### **Responsibilities:**
- Accepts data from POS terminals across all client stores via REST API
- Serves as the central data repository for sales records
- Provides backend services for the KwikPOS Live web application
- Handles data retrieval requests for sales analytics and reporting

#### **Deployment Architecture:**
- Hosted on AWS EC2 instance
- Apache Tomcat 9.0 servlet container
- Direct MySQL 8.0 database connection
- Legacy deployment pipeline (manual WAR deployment)

---

### KwikPOS API (Ordering Kiosk to Legacy POS Data Adapter)

**Purpose:** Bridge layer connecting self-ordering kiosks to legacy POS applications

#### **Tech Stack:**
- **Framework:** Spring Boot 3.5.4
- **Runtime:** Java 17
- **Deployment:** Apache Tomcat 10.0
- **Deployment Location:** On-premise POS machine

#### **Key Features:**
- API server for self-ordering kiosk integration
- Data transformation layer between modern kiosks and legacy POS systems
- Real-time order transmission from kiosks to POS terminals
- Compatibility layer for Chase POS integration

#### **Responsibilities:**
- Receives order requests from self-ordering kiosks
- Transforms and adapts order data to legacy POS format
- Transmits orders to the connected POS terminal
- Serves as the communication bridge between modern ordering interfaces and legacy systems

#### **Deployment Architecture:**
- Installed on individual POS machines acting as local servers
- Apache Tomcat 10.0 servlet container
- Handles local network requests from nearby kiosks
- Direct integration with Chase POS application

#### **Main Highlight:**
This adapter enables our modern self-ordering kiosk products to seamlessly communicate with legacy POS applications, particularly Chase POS, without requiring modifications to the existing POS software.

---

## Technology Overview

### Backend Technologies
- **Java 8** - KwikPOS Live (with upgrade plans)
- **Java 17** - KwikPOS API
- **Spring Boot 2.7.2** - KwikPOS Live
- **Spring Boot 3.5.4** - KwikPOS API

### Databases
- **MySQL 8.0** - KwikPOS Live primary database

### Application Servers
- **Apache Tomcat 9.0** - KwikPOS Live deployment
- **Apache Tomcat 10.0** - KwikPOS API deployment

### Infrastructure
- **AWS EC2** - Cloud hosting for KwikPOS Live
- **On-Premise** - Local POS machine hosting for KwikPOS API

## Development Environment Setup

### Prerequisites

Ensure you have the following installed based on the project you're working on:

#### For KwikPOS Live
- **JDK 8**
  ```bash
  java -version  # Should show Java 8
  ```
- **Maven 3.6+**
  ```bash
  mvn -version
  ```
- **MySQL 8.0**
  ```bash
  mysql --version
  ```
- **Apache Tomcat 9.0** (for local testing)

#### For KwikPOS API
- **JDK 17**
  ```bash
  java -version  # Should show Java 17
  ```
- **Maven 3.8+**
  ```bash
  mvn -version
  ```
- **Apache Tomcat 10.0** (for local testing)

#### General Development Tools
- **Git** (v2.30+)
- **IDE:** IntelliJ IDEA or Eclipse with Spring Boot support
- **Postman** or similar API testing tool
- **MySQL Workbench** or DBeaver for database management

## Architecture Comparison

| Aspect | KwikPOS Live | KwikPOS API |
|--------|--------------|-------------|
| **Deployment** | Cloud (AWS EC2) | On-Premise (POS Machine) |
| **Scope** | Multi-tenant | Single store |
| **Purpose** | Central data hub | Kiosk-POS bridge |
| **Database** | MySQL 8.0 | N/A (passes through) |
| **Clients** | Multiple tenants | Individual kiosks |
| **Integration** | POS Terminals → Cloud | Kiosks → Legacy POS |

## Project Selection Guide

**Work on KwikPOS Live if:**
- You're developing cloud-based features
- Working on multi-tenant functionality
- Building sales analytics or reporting features
- Implementing web dashboard features
- Upgrading Java/Spring Boot versions

**Work on KwikPOS API if:**
- You're integrating with legacy POS systems
- Developing kiosk communication features
- Working on data transformation layers
- Implementing Chase POS compatibility
- Testing on-premise deployment scenarios

## Next Steps

1. Choose which project you'll be working on
2. Set up the appropriate development environment
3. Clone the respective repository
4. Review the project-specific documentation
5. Contact your team lead for repository access and credentials

## Getting Help

If you need assistance:

- **Technical Questions:** Reach out to the development team
- **Access Issues:** Contact your team lead for repository and AWS credentials
- **Architecture Questions:** Review project-specific architecture documentation
- **Deployment Issues:** Check deployment guides or contact DevOps

Welcome to the KwikPOS development team!
