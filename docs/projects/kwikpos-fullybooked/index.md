# KwikPOS x FullyBooked Integration

## Overview

**Purpose:** Custom integration between KwikPOS POS system and FullyBooked's IMS system

This project handles the integration between KwikPOS POS terminals and FullyBooked's (a bookstore chain) IMS systems, primarily focusing on data exchange through text file imports/exports and custom SQL queries for data retrieval and manipulation.

## Project Context

This is a **client-specific integration project** developed to meet FullyBooked's unique business requirements. The integration is primarily database-centric, involving custom SQL queries, database views, and text file-based data exchange.

Their POS application is a **heavily** modified version of WinPOS, which is technically the legacy version of the retail POS we provide. Do keep this in mind as there might be columns and tables not a part of the **standard** retail POS.

**Note:** This project was not primarily developed by the current documentation author. Most involvement was limited to SQL query modifications and database-level work.

## Key Components

### Data Export System

The integration exports data from the POS database to text files for FullyBooked's systems to consume.

**Primary Exports Include:**

- Transaction data
- Detailed transaction data
- Other POS data as required by FullyBooked

**Export Mechanism:**

- Data is exported as **text files**
- Custom SQL views are used to retrieve and format the data
- Exports are generated based on FullyBooked's specific data format requirements

### Data Import System

The integration imports data from FullyBooked's systems into the POS database via text files.

**Primary Imports Include:**

- Product/item data
- Promos and discounts
- Customer information
- Pricing information
- Other master data as needed

**Import Mechanism:**

- Text file-based imports
- Custom SQL procedures or scripts to process and insert data
- Data validation and transformation during import

### Custom SQL Queries and Views

A significant portion of the work involves maintaining and modifying SQL queries and database views:

**Database Views:**

- Custom views created to retrieve transaction data
- Views optimized for FullyBooked's specific reporting needs
- Views that transform POS data into FullyBooked's required format

**SQL Query Modifications:**

- Modifying existing views to accommodate new data requirements
- Creating new queries for data extraction
- Optimizing query performance for large datasets

## Technical Approach

### Database-Centric Integration

The integration primarily operates at the database level:

- Custom SQL views for data retrieval
- Stored procedures or scripts for data import/export
- Database triggers (if applicable) for automated processes
- Direct database access for FullyBooked's systems or middleware

### Text File Format

Data exchange uses text files as the medium:

- **Export Format:** Text files (CSV, tab-delimited, or fixed-width)
- **Import Format:** Text files provided by FullyBooked
- File transfer mechanism (FTP, shared folder, or other)

## Responsibilities

### Data Export

- Generate text file exports containing POS transaction data
- Format data according to FullyBooked's specifications
- Ensure data accuracy and completeness
- Handle export scheduling (manual or automated)

### Data Import

- Process text file imports from FullyBooked's systems
- Validate and transform incoming data
- Insert/update POS database with imported data
- Handle data conflicts and errors

### Database Maintenance

- Maintain and modify SQL views for data retrieval
- Optimize queries for performance
- Create new views or queries as requirements evolve
- Ensure data integrity during import/export operations

## Development Notes

### Limited Code Involvement

**Important Context:**

- The core application code was developed by others
- Primary involvement has been at the database/SQL level
- Focus has been on query modifications and view maintenance
- Limited knowledge of the full application architecture

### SQL Work

Most development work involves:

- Writing and modifying SQL queries
- Creating and updating database views
- Optimizing query performance
- Troubleshooting data export/import issues

### Common Tasks

Typical tasks in this project include:

1. **Modifying Views** - Updating existing views to include new fields or change data retrieval logic
2. **Query Optimization** - Improving performance of slow-running queries
3. **Data Extraction** - Writing new queries to retrieve specific transaction or item data
4. **Import Logic** - Modifying import procedures to handle new data formats
5. **Data Validation** - Ensuring imported/exported data meets requirements

## Tech Stack

**Database:** MS SQL Server

**Export/Import Tools:** KwikPOS WebExt Web Application

**File Format:** Text files (tab-delimited)

## Getting Started

### Prerequisites

- Database access credentials for the FullyBooked POS database
- Understanding of FullyBooked's data format specifications
- SQL query writing and optimization skills
- Database client tool (SQL Server Management Studio)

### Common Workflows

#### Modifying an Export View

1. Identify the view that needs modification
2. Review current view definition and data output
3. Make necessary SQL changes to the view
4. Test the modified view with sample data
5. Verify export file format matches FullyBooked's requirements
6. Deploy the updated view

#### Adding New Export Data

1. Understand the new data requirements from FullyBooked
2. Identify the `KwikPOS_WebExt` schema and update the table with `lkp`.
3. Create the view table. Follow existing naming conventions based on existing view tables.
4. Update column with updated row to query the new SQL view in the `lkp` table.
5. Test export with real data

#### Troubleshooting Import Issues

1. Review import error logs
2. Validate text file format against specifications
3. Check for data type mismatches or constraint violations
4. Test import procedure with problematic data
5. Fix SQL import logic or data validation
6. Re-run import and verify success

## Known Limitations

- **Limited Application Knowledge** - Core application code is not well-documented here
- **Text File Dependency** - Integration relies on file-based data exchange (not real-time)
- **Manual Processes** - Some exports/imports may require manual intervention
- **Custom Requirements** - Highly specific to FullyBooked's needs, not reusable

## Getting Help

If you need assistance with this integration:

- **SQL/Database Questions:** Review existing views and queries in the database
- **Data Format Issues:** Check with FullyBooked's technical team for specifications
- **Export/Import Problems:** Review logs and validate file formats
- **New Requirements:** Coordinate with the development team or directly with the contact person in FullyBooked GCs

## Notes for Future Developers

### Important Considerations

- This is a **client-specific integration** - changes must be coordinated with FullyBooked
- Always test SQL changes with sample data before deployment
- Export file format changes require FullyBooked's approval
- Document any new views or queries you create
- Consider performance impact of query changes on production database

### When Making Changes

1. **Understand the requirement** - Get clear specifications from FullyBooked
2. **Test thoroughly** - Use sample data that covers edge cases
3. **Coordinate deployment** - Schedule changes during low-traffic periods
4. **Monitor after deployment** - Verify exports/imports work correctly

---

**Last Updated:** December 31, 2025<br />
**Updated By:** Adrian Melegrito
