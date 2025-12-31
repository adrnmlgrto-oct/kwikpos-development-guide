# Troubleshooting

This document covers known limitations and guidance for getting help with the FullyBooked integration.

## Known Limitations

### Limited Application Knowledge

- **Limited Application Knowledge** - Core application code is not well-documented here
- Most documentation focuses on database/SQL work rather than application architecture
- The WebExt application layer is not extensively covered

### Integration Constraints

- **Text File Dependency** - Integration relies on file-based data exchange (not real-time)
- **Manual Processes** - Some exports/imports may require manual intervention
- **Custom Requirements** - Highly specific to FullyBooked's needs, not reusable for other clients

### Technical Limitations

- File-based integration introduces latency compared to real-time API integration
- Manual file transfers may be required depending on deployment setup
- Data sync frequency depends on export/import scheduling

## Getting Help

### SQL/Database Questions

**What to do:**
- Review existing views and queries in the database
- Check SQL Server query execution plans for performance issues
- Examine database schema for available tables and columns
- Review database logs for errors

**Tools:**
- SQL Server Management Studio (SSMS)
- Azure Data Studio
- Database documentation (if available)

### Data Format Issues

**What to do:**
- Check with FullyBooked's technical team for format specifications
- Review sample files to understand expected format
- Validate file structure (delimiters, headers, data types)

**Common Issues:**
- Tab-delimited format mismatches
- Missing or extra columns
- Data type incompatibilities
- Character encoding issues

### Export/Import Problems

**What to do:**
- Review logs and validate file formats
- Check file permissions and access
- Verify file paths and transfer mechanisms
- Test with sample data before production

**Common Issues:**
- File permission errors
- Path/location mismatches
- File format validation failures
- Data transformation errors

### New Requirements

**What to do:**
- Coordinate with the development team or directly with the contact person in FullyBooked GCs
- Get clear specifications before making changes
- Document new requirements and implementation approach
- Test thoroughly before deployment

## Common Issues & Solutions

### Export View Not Returning Expected Data

**Symptoms:**
- Missing rows in export
- Incorrect data values
- NULL values where data should exist

**Solutions:**
1. Review the SQL view definition
2. Check JOIN conditions and WHERE clauses
3. Verify source tables have the expected data
4. Test query with sample data
5. Check for data type conversions

### Import Failing with Validation Errors

**Symptoms:**
- Import process fails
- Data type mismatch errors
- Constraint violation errors

**Solutions:**
1. Review import error logs
2. Validate text file format matches specifications
3. Check for data type mismatches
4. Verify required fields are present
5. Test import procedure with small sample file

### Performance Issues with Views

**Symptoms:**
- Slow query execution
- Timeouts during export
- High database CPU/memory usage

**Solutions:**
1. Review query execution plan
2. Add appropriate indexes
3. Optimize JOIN operations
4. Consider materialized views for complex queries
5. Break large queries into smaller batches

## Escalation Process

If you cannot resolve an issue:

1. **Document the problem** - Error messages, logs, steps to reproduce
2. **Check existing documentation** - Review this guide and database documentation
3. **Contact development team** - For technical assistance
4. **Contact FullyBooked** - For business requirement clarifications or IMS-related issues
