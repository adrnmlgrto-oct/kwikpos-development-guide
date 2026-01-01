# Overview

**Purpose:** Custom integration between KwikPOS POS system and FullyBooked's IMS system

This project handles the integration between KwikPOS POS terminals and FullyBooked's (a bookstore chain) IMS systems, primarily focusing on data exchange through text file imports/exports and custom SQL queries for data retrieval and manipulation.

## Project Context

This is a **client-specific integration project** developed to meet FullyBooked's unique business requirements. The integration is primarily database-centric, involving custom SQL queries, database views, and text file-based data exchange.

Their POS application is a **heavily** modified version of WinPOS, which is technically the legacy version of the retail POS we provide. Do keep this in mind as there might be columns and tables not a part of the **standard** retail POS.

**Note:** This project was not primarily developed by the current documentation author. Most involvement was limited to SQL query modifications and database-level work.

## Tech Stack

- **Database:** MS SQL Server
- **Application Server:** Apache Tomcat 9.0
- **Backend Framework:** Spring Boot 2.7.2
- **Java Version:** Java 11 (likely, but unconfirmed)
- **Export/Import Tools:** KwikPOS WebExt Web Application
- **File Format:** Text files (tab-delimited)
- **Deployment:** On-premise (loaded on individual FullyBooked POS machines)

**Note:** While this integration runs on a Spring Boot application deployed via Tomcat, most development work involves database/SQL-level modifications rather than application code changes.

## Database Configuration

### Database Schemas

The FullyBooked integration utilizes multiple MS SQL Server databases:

#### `serverposdb`
- **Purpose:** Primary POS application database
- **Usage:** Main database where most SQL view editing and modifications occur
- **Role:** Contains core POS data for transactions, items, and operations
- **Development Note:** This is the primary database you'll work with when creating or modifying views for data exports

#### `KwikPOS_AddIn`
- **Purpose:** Spring Boot integration configuration database
- **Usage:** Stores integration-specific settings and configurations
- **Key Contents:**
    - User configurations
    - Cron job settings (e.g., boolean flags for enabling/disabling scheduled text file exports to IMS)
    - FTP connection details (IP addresses, credentials)
    - Database-centric approach configuration tables
    - `dbo.FB_IMSFILE_LKP` - Lookup table for IMS file exports
        - Contains rows identifying resources to export
        - Maps view tables to query for each export type
        - Defines export configurations and mappings

**Database-Centric Approach:** This integration follows a database-centric design pattern where configuration and logic are stored in database tables rather than hardcoded in the application, allowing for flexible modifications without code changes.

## Key Features

### Data Export System

The integration exports data from the POS database to text files for FullyBooked's systems to consume.

**Primary Exports Include:**
- Transaction data
- Detailed transaction data
- Other POS data as required by FullyBooked

### Data Import System

The integration imports data from FullyBooked's systems into the POS database via text files.

**Primary Imports Include:**
- Product/item data
- Promos and discounts
- Customer information
- Pricing information
- Other master data as needed

### Custom SQL Queries and Views

A significant portion of the work involves maintaining and modifying SQL queries and database views for data extraction, transformation, and reporting.

## Quick Links

- [Responsibilities](responsibilities.md) - Core integration responsibilities
- [Deployment](deployment.md) - Infrastructure and technical details
- [Development Tasks](development.md) - Common workflows and development notes
- [Troubleshooting](troubleshooting.md) - Known limitations and getting help

## Getting Help

If you need assistance with this integration:

- **SQL/Database Questions:** Review existing views and queries in the database
- **Data Format Issues:** Check with FullyBooked's technical team for specifications
- **Export/Import Problems:** Review logs and validate file formats
- **New Requirements:** Coordinate with the development team or directly with the contact person in FullyBooked GCs
