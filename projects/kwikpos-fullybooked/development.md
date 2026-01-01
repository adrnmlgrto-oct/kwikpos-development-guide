# Development Tasks

This document provides guidance on common development tasks and workflows for the FullyBooked integration.

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

## Common Workflows

### Modifying an Export View

1. Identify the view that needs modification
2. Review current view definition and data output
3. Make necessary SQL changes to the view
4. Test the modified view with sample data
5. Verify export file format matches FullyBooked's requirements
6. Deploy the updated view

### Adding New Export Data

1. Understand the new data requirements from FullyBooked
2. Identify the `KwikPOS_AddIn` schema and update the table with `dbo.FB_IMSFILE_LKP`
3. Create the view table in the `serverposdb` schema. Follow existing naming conventions based on existing view tables
4. Update column with updated row to query the new SQL view in the `dbo.FB_IMSFILE_LKP` table
5. Test export with real data

### Troubleshooting Import Issues

1. Review import error logs
2. Validate text file format against specifications
3. Check for data type mismatches or constraint violations
4. Test import procedure with problematic data
5. Fix SQL import logic or data validation
6. Re-run import and verify success

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

## Development Environment

### Database Tools

Recommended tools for working with the FullyBooked integration:

- **SQL Server Management Studio (SSMS)** - Full-featured IDE for SQL Server
- **Database client** with SQL Server support

### SQL Best Practices

When writing queries for this integration:

- Follow existing naming conventions for views and procedures
- Comment complex queries to explain business logic
- Test with realistic data volumes
- Consider indexing for performance-critical queries
- Validate data types match FullyBooked's specifications
