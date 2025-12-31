# Deployment & Tech Stack

This document covers the technical infrastructure and deployment details for the FullyBooked integration.

## Deployment Model

### On-Premise Deployment

The integration is deployed on individual FullyBooked POS machines:

- **Environment:** On-premise at FullyBooked store locations
- **Server:** Apache Tomcat 9.0
- **Application:** KwikPOS WebExt Web Application
- **Database:** MS SQL Server (co-located with POS application)

### Infrastructure

The integration runs alongside the FullyBooked POS application:

- Deployed on the same machines as the FullyBooked POS system
- Direct database access to the POS database
- Text file-based data exchange with FullyBooked's IMS system
- File transfer via FTP, shared folders, or other mechanisms

## Prerequisites

To work on this integration, you'll need:

- Database access credentials for the FullyBooked POS database
- Understanding of FullyBooked's data format specifications
- SQL query writing and optimization skills
- Database client tool (SQL Server Management Studio or Azure Data Studio)

## Architecture Context

### Modified WinPOS Base

The FullyBooked POS application is a **heavily** modified version of WinPOS, which is the legacy version of our retail POS product.

**Important:** There may be columns and tables that are not part of the **standard** retail POS. Always verify the database schema when working with this integration.

### Integration Flow

```
FullyBooked POS Database
         ↓
  SQL Views/Queries
         ↓
  WebExt Application
         ↓
    Text Files
         ↓
FullyBooked IMS System
```

**Bidirectional Flow:**
- **Export:** POS → Text Files → IMS
- **Import:** IMS → Text Files → POS
